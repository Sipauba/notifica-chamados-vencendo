# Configuração do GLPI

1. Disponibilize acesso **somente de leitura**, se possível, ao MySQL do GLPI para o n8n.
2. Confirme a presença da tabela `glpi_tickets` e dos campos `id`, `name`, `status` e `time_to_resolve`.
3. Valide o significado dos status `1` e `2` na sua versão e configuração do GLPI. O workflow filtra esses códigos sem interpretá-los dinamicamente.
4. Confirme a timezone da sessão MySQL, do GLPI e do n8n. As consultas usam `NOW()` do banco; divergências de fuso podem deslocar os alertas.
5. Configure uma Credential MySQL privada no n8n e atribua-a aos três nodes de consulta. O export público contém apenas uma referência mascarada.
6. Faça uma execução de teste com dados de homologação e confira a formatação de `time_to_resolve` e de `hora_fim_prazo`.

Não coloque dados de acesso ao banco no workflow ou na documentação versionada.
