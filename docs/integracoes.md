# Integrações

## MySQL / GLPI

Os três nodes MySQL executam consultas SQL no banco do GLPI. Selecione no n8n uma Credential MySQL privada com o mínimo de privilégios necessário. As consultas originais e suas janelas foram mantidas no JSON público.

## WhatsApp API

Os três HTTP Request nodes fazem `POST` para um endpoint compatível com `https://<servidor>/message/sendText/<instância>`. O corpo possui `number` (ID do grupo) e `text` (mensagem montada pelo Code node). O tipo de autenticação exportado é `HTTP Header Auth`; configure o cabeçalho exigido pelo seu provedor em uma Credential privada do n8n.

O host, a instância e o grupo estão mascarados no workflow. Substitua os placeholders nos três nodes antes de testar. Não copie URLs, identificadores de grupos ou chaves reais para o repositório. Os campos de [.env.example](../.env.example) servem como referência de configuração; o workflow atual não os consome automaticamente.
