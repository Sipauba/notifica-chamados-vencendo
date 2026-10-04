# Segurança

- Mantenha senhas, chaves e Credentials apenas no ambiente privado do n8n. Nunca inclua senhas no JSON exportado.
- Não publique IDs de grupos de WhatsApp, números, nomes de instância, URLs internas, hosts ou identificadores de infraestrutura.
- Use um usuário do banco do GLPI com o menor privilégio possível, preferencialmente somente leitura.
- Não versione `.env`, exports brutos, arquivos de credenciais ou backups. A pasta local `originals/` está no `.gitignore` para preservar o export original fora do histórico Git.
- Revise todo novo export antes de commit, inclusive metadados, URLs, parâmetros de corpo, nomes e IDs de Credentials e possíveis dados fixados em nodes.
- Rode uma busca por dados sensíveis e, se disponível, `gitleaks` sobre os arquivos que serão versionados.

A versão pública troca referências privadas pelo placeholder `xxxxxxxxxxxxxxxxxxxx`. IDs internos de nodes, condições e atribuições foram regenerados para não publicar os identificadores do export original, mantendo IDs distintos para importação. Após importar, associe as Credentials e preencha os destinos em um ambiente privado.
