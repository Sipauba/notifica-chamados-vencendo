# Fluxo de alertas

O Schedule Trigger executa o workflow a cada **4 minutos**. Cada consulta filtra `glpi_tickets` por `g.status IN (1, 2)` e compara `g.time_to_resolve` com `NOW()` no banco MySQL.

| Nível | Intervalo SQL para `time_to_resolve` | Próximo passo |
| --- | --- | --- |
| 1 hora | `NOW() + 60` até `NOW() + 65` minutos | Monta e envia alerta se houver chamado; caso contrário, verifica 30 minutos |
| 30 minutos | `NOW() + 30` até `NOW() + 35` minutos | Monta e envia alerta se houver chamado; caso contrário, verifica 15 minutos |
| 15 minutos | `NOW() + 15` até `NOW() + 20` minutos | Monta e envia alerta quando a consulta retorna itens |

As janelas de cinco minutos permitem que uma execução periódica de quatro minutos encontre chamados dentro de cada faixa. Os intervalos e a frequência foram preservados do workflow original.

As duas primeiras consultas usam `alwaysOutputData` e passam por nodes IF que verificam se o JSON está preenchido. A consulta de 15 minutos segue diretamente para o Code node e não tem IF separado. As ramificações são sequenciais: se houver chamados na faixa de 1 hora, as faixas de 30 e 15 minutos não são consultadas nessa execução; o mesmo vale para 30 minutos em relação a 15 minutos. Isso deve ser considerado ao avaliar cobertura e futuras melhorias, sem alterar o comportamento deste export.

Cada Code node compõe uma mensagem com o número (`id`), a hora limite formatada (`hora_fim_prazo`) e o título (`name`). Confira [exemplos fictícios](../examples/mensagens.md).
