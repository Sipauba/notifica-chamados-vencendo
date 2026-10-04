# Melhorias futuras

Possíveis evoluções, **não implementadas** neste export:

- Parametrizar os intervalos de SLA e o fuso horário.
- Evitar SQL repetido e reunir as três verificações em uma lógica configurável.
- Avaliar alertas independentes para as três janelas, em vez de parar após o primeiro nível com resultados.
- Definir grupos diferentes por equipe, alertas por técnico e suporte a múltiplas entidades do GLPI.
- Evitar notificações duplicadas e registrar o histórico de envios.
- Tratar falhas da API de WhatsApp com retry, logs estruturados e observabilidade.
- Criar um dashboard e configurar destinos e parâmetros por variáveis em vez de valores nos nodes.
