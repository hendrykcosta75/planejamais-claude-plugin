<div align="center">
  <img src="plugins/planejamais/.claude-plugin/icon.png" alt="Planeja+" width="88" />

  <h1>Planeja+ para Claude Code e Cowork</h1>

  <p>Plugin e marketplace público do conector MCP do <a href="https://planejamais.planejareconsultoria.com.br">Planeja+</a>: planejamento estratégico, tarefas Kanban, reuniões, relatórios, tickets e editais e projetos no Claude.</p>

  <p>
    <a href="https://github.com/hendrykcosta75/planejamais-claude-plugin/releases/latest"><img alt="Release" src="https://img.shields.io/github/v/release/hendrykcosta75/planejamais-claude-plugin?color=5A45FF" /></a>
    <a href="LICENSE"><img alt="MIT" src="https://img.shields.io/badge/licen%C3%A7a-MIT-blue" /></a>
    <a href="https://registry.modelcontextprotocol.io/v0/servers?search=io.github.hendrykcosta75/planejamais"><img alt="MCP Registry" src="https://img.shields.io/badge/MCP%20Registry-io.github.hendrykcosta75%2Fplanejamais-5A45FF" /></a>
    <a href="https://mcptry.com/servers/io.github.hendrykcosta75/planejamais"><img alt="mcptry" src="https://mcptry.com/badge/io.github.hendrykcosta75/planejamais" /></a>
  </p>
  <p>
    <img alt="ChatGPT e Codex" src="https://img.shields.io/badge/ChatGPT%20e%20Codex-publicado-10A37F?logo=openai&logoColor=white" />
    <a href="https://claude.ai/directory/connectors/planejamais"><img alt="Claude" src="https://img.shields.io/badge/Claude-conector%20publicado-D97757?logo=claude&logoColor=white" /></a>
    <img alt="Hermes" src="https://img.shields.io/badge/Hermes%20Agent-cat%C3%A1logo-111111" />
    <img alt="OAuth 2.1" src="https://img.shields.io/badge/OAuth%202.1-DCR%20%2B%20PKCE-2F855A" />
  </p>
</div>

Este repositório é só o pacote de distribuição; o produto Planeja+ não é aberto e vive em outro
repositório. No claude.ai e no Claude Desktop, o mais simples é o
[conector do diretório](https://claude.ai/directory/connectors/planejamais).

## O que o plugin instala

- Servidor MCP remoto `planejamais` (`https://planejamais.planejareconsultoria.com.br/api/mcp`),
  com OAuth 2.1 conduzido pelo Claude (Dynamic Client Registration + PKCE).
- Skill `planejamais` com os fluxos de uso, o cuidado com `companyId` e as
  regras de confirmação para ações destrutivas.

Exclusões permanentes, reescritas do projeto por IA e menções que enviam e-mail
passam por uma confirmação aplicada pelo servidor: a primeira chamada devolve um
token `confirmacao` e não executa nada; só a mesma chamada repetida com o token
executa, uma vez.

Nenhum token manual é necessário: na primeira chamada o Claude abre o navegador
para o usuário autorizar, e o token pode ser removido depois em
`https://planejamais.planejareconsultoria.com.br/mcp`.

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

A submissão é feita no portal de desenvolvedores do claude.ai
(`https://claude.ai/directory/manage`) como **Plugin bundle**, com o caminho
`plugins/planejamais`. Antes de enviar, rode:

```bash
claude plugin validate ./plugins/planejamais --profile directory
```

O README e o LICENSE exibidos na listagem ficam dentro de `plugins/planejamais`.

## Manutenção

- A URL de produção é `https://planejamais.planejareconsultoria.com.br/api/mcp`.
  Se o app mudar de domínio, atualize `plugins/planejamais/.mcp.json` e suba a versão.
- Ao publicar uma nova versão, incremente `version` em
  `plugins/planejamais/.claude-plugin/plugin.json` e no marketplace.
