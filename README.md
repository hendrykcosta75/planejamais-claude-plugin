# Plugin Claude — Planeja+

Plugin e marketplace público do conector MCP do **Planeja+** para Claude Code e
Cowork. Este repositório é apenas o pacote de distribuição; o produto Planeja+
não é aberto e vive em outro repositório.

## O que o plugin instala

- Servidor MCP remoto `planejamais` (`https://planejamais.com.br/api/mcp`),
  com OAuth 2.1 conduzido pelo Claude (Dynamic Client Registration + PKCE).
- Skill `planejamais` com os fluxos de uso, o cuidado com `companyId` e as
  regras de confirmação para ações destrutivas.

Nenhum token manual é necessário: na primeira chamada o Claude abre o navegador
para o usuário autorizar, e o token pode ser removido depois em
`https://planejamais.com.br/mcp`.

## Instalação

```bash
claude plugin marketplace add hendrykcosta75/planejamais-claude-plugin
claude plugin install planejamais@planejamais
```

Ou, dentro do Claude Code, use `/plugin`, escolha o marketplace `planejamais` e
instale o plugin. Para testar localmente:

```bash
claude plugin validate ./plugins/planejamais --strict
claude --plugin-dir ./plugins/planejamais
```

## Publicação no diretório

A submissão é feita pelo formulário de plugins (o mesmo diretório comunitário de
Cowork e Claude Code). Requisitos:

- Repositório público (este) — o formulário pede o link do GitHub.
- `claude plugin validate` sem erros.
- Org Team/Enterprise no claude.ai **ou** submissão pelo Console
  (`https://platform.claude.com/plugins/submit`), que aceita autores
  individuais.

O diretório de **connectors** do claude.ai (web/app) é outro processo e exige
organização Team/Enterprise; este plugin não cobre essa vitrine.

## Manutenção

- A URL de produção pressupõe `https://planejamais.com.br`. Se o app mudar de
  domínio, atualize `plugins/planejamais/.mcp.json`.
- Ao publicar uma nova versão, incremente `version` em
  `plugins/planejamais/.claude-plugin/plugin.json` e no marketplace.
