# Planeja+ para Claude

Conecte o Claude ao **Planeja+**, plataforma de planejamento estratégico e
gestão de tarefas da Planejare Consultoria. Com o plugin, você consulta e
atualiza planejamentos, perspectivas, objetivos, iniciativas e etapas; organiza
quadros Kanban, tarefas e checklists; agenda eventos e reuniões; gera
relatórios; e acompanha tickets de suporte, tudo a partir de uma conversa.

É necessário ter uma conta no Planeja+. Cada chamada usa a empresa escolhida e
respeita o papel do seu vínculo (`proprietário`, `gerente`, `colaborador` ou
`observador`); o servidor recusa ações que o seu papel não permite.

## O que o plugin contém

- **Servidor MCP remoto** `planejamais`, em
  `https://planejamais.planejareconsultoria.com.br/api/mcp` (Streamable HTTP).
- **Skill** `planejamais`, que orienta o Claude a escolher a empresa certa
  (`companyId`), preferir leituras e pedir confirmação antes de ações
  destrutivas ou que enviam mensagens.

O plugin não tem hooks, comandos, agentes, scripts nem servidores locais.

## Instalação

No Claude Code:

```bash
/plugin install planejamais --marketplace hendrykcosta75/planejamais-claude-plugin
```

Depois da publicação no diretório, o plugin também pode ser adicionado pelo
claude.ai em **Personalizar → Plugins**.

## Autenticação

Na primeira chamada, o Claude abre o navegador para você entrar no Planeja+ e
autorizar o acesso (OAuth 2.1 com Dynamic Client Registration e PKCE). Nenhum
token precisa ser copiado manualmente. Você pode revogar as autorizações a
qualquer momento na página MCP do Planeja+
(`https://planejamais.planejareconsultoria.com.br/mcp`).

## Dados enviados e recebidos

- O Claude envia ao servidor do Planeja+ apenas os argumentos de cada
  ferramenta chamada (por exemplo, o id da empresa, o título de uma tarefa ou o
  período de um relatório) e recebe os dados da sua conta necessários para
  responder.
- O plugin não envia dados a nenhum outro destino e não lê arquivos, memória ou
  histórico de conversas.
- Comentários, itens de checklist e descrições com menções podem gerar
  notificações por email aos membros mencionados; convites enviam email ao
  endereço convidado. A skill pede confirmação antes dessas ações.

## Exemplos de uso

- "Resuma o andamento das iniciativas do planejamento estratégico deste trimestre."
- "Crie as tarefas de acompanhamento da reunião de hoje no quadro do time."
- "Gere o relatório geral do planejamento e destaque os riscos."

## Links

- [Página da integração](https://planejamais.planejareconsultoria.com.br/integracoes/planejamais)
- [Privacy Policy / Política de privacidade](https://planejamais.planejareconsultoria.com.br/integracoes/planejamais/privacidade)
- [Termos de uso](https://planejamais.planejareconsultoria.com.br/integracoes/planejamais/termos)
- [Suporte](https://planejamais.planejareconsultoria.com.br/integracoes/planejamais/suporte)

## Licença

Os arquivos deste plugin são distribuídos sob a licença MIT (veja `LICENSE`).
O serviço Planeja+ é um produto proprietário da Planejare Consultoria LTDA.
