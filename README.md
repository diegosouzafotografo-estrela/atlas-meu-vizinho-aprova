# Atlas visual do sistema

**[Abrir o índice navegável](index.html)** — busca, filtros por área e links para
os 35 diagramas.

Diagramas standalone do Meu Vizinho Aprova, gerados pelo pipeline nativo do
Archify (`validate` → `deliver` → `check` → `browser-check`). O conteúdo está em
português; o chrome do Viewer cai para inglês porque o Archify não tem catálogo
`pt-BR` embutido.

**Ponto de congelamento:** `f83b8d4` (2026-11-20). A fase 1 é **entregue**; as
fases 2 a 5 são **planejadas** e vêm dos specs, não de código executado.

## Como ler

| Legenda | Significado |
|---|---|
| **Entregue** | Existe no código/migrations da fase 1. |
| **Planejado** | Está no spec da fase, ainda sem implementação. |
| **Contexto** | Entidade mostrada só para fechar uma FK; não é o foco do MER. |

`P` e `c` nunca aparecem em visão de cliente ou curador. Valores de dinheiro são
inteiros de centavos. Onde o diagrama é ilustrativo, o próprio cartão diz isso.

## Arquitetura e isolamento

| # | Diagrama | Pergunta | Fonte |
|---|---|---|---|
| 01 | [Contexto](01-contexto.html) | Quem usa o sistema e quais serviços externos ele toca? | Spec §1, §5, §12 |
| 02 | [Containers](02-containers.html) | Quais aplicativos, serviços e bancos existem? | Spec §5, ADRs 0001–0003 |
| 03 | [Componentes do Next.js](03-componentes-next.html) | Como o código se organiza e por onde uma ação passa? | `src/app`, `src/dominio`, `src/lib` |
| 04 | [Implantação](04-implantacao.html) | O que roda hoje e o que é alvo de produção? | Spec §5, ADR 0011 |
| 05 | [Tenancy e RLS](05-tenancy-rls.html) | Quem enxerga o quê e qual é a barreira? | Spec §5, ADR 0002, migrations |

## Dados e MER

| # | Diagrama | Pergunta | Fonte |
|---|---|---|---|
| 06 | [Mapa de agregados](06-mapa-agregados.html) | Quais são os grandes blocos do domínio? | Spec §6 |
| 07 | [MER identidade e acesso](07-mer-identidade.html) | Quem é pessoa, membro, operador e promoção? | Spec §6, migrations |
| 08 | [MER grupos e vínculo](08-mer-grupos-vinculo.html) | Como GC, GP e vínculo se ligam? | Spec §6, migrations |
| 09 | [MER catálogo e agenda](09-mer-catalogo-agenda.html) | Como serviço, habilitação, blocos e exceções se ligam? | Spec §6, fase 2 |
| 10 | [MER pedido e orçamento](10-mer-pedido.html) | Quais campos o pedido copia e como o orçamento encaixa? | Spec §6, fase 3 |
| 11 | [MER dinheiro](11-mer-dinheiro.html) | Como titular, conta, pagamento e repasse se ligam? | Spec §6, fase 4 |
| 12 | [MER pós-venda e plataforma](12-mer-posvenda-plataforma.html) | Onde ficam avaliação, disputa, notificação e auditoria? | Spec §6, fase 5 |

## Entrada e oferta

| # | Diagrama | Pergunta | Fonte |
|---|---|---|---|
| 13 | [Ciclo do cliente](13-ciclo-cliente.html) | Como alguém entra, é aprovado, é revogado e reentra? | Spec §8.1, §8.13 |
| 14 | [Ciclo do vínculo](14-ciclo-vinculo.html) | Quais estados o vínculo atravessa? | Spec §8.2, §8.3, §9 |
| 15 | [Profissional e papéis](15-profissional-papeis.html) | Como convite, inclusão, promoção e conflito funcionam? | Spec §8.3, §8.11, §8.12 |
| 16 | [Oferta](16-oferta-catalogo-habilitacao.html) | Como catálogo, comissão e habilitação se encaixam? | Spec §8.14, fase 2 |
| 17 | [Agenda](17-agenda-profissional.html) | Como blocos e exceções viram disponibilidade? | Spec §8.15, fase 2 |
| 18 | [Disponibilidade e reserva](18-disponibilidade-reserva.html) | Como o cliente vê horários e reserva sem duplicar? | Spec §8.5, fase 3 |

## Pedido

| # | Diagrama | Pergunta | Fonte |
|---|---|---|---|
| 19 | [Pedido com preço definido](19-pedido-preco-definido.html) | Qual é o caminho da descoberta até o pagamento? | Spec §8.6 |
| 20 | [Pedido sob orçamento](20-pedido-orcamento.html) | Como o orçamento é pedido, respondido e aceito? | Spec §8.7 |
| 21 | [Remarcação](21-remarcacao.html) | Quem remarca e o que acontece com o horário original? | Spec §8.8 |
| 22 | [Cancelamento e efeitos](22-cancelamento-no-show.html) | Quanto e para quem volta em cada cancelamento? | Spec §8.8 |
| 23 | [Pedido até o pagamento](23-ciclo-pedido-ate-pagamento.html) | Quais estados existem antes de pagar? | Spec §9 |
| 23b | [Pedido pós-pagamento](23b-ciclo-pedido-pos-pagamento.html) | Quais estados existem depois de pagar? | Spec §9 |
| 24 | [Relógios e prazos](24-relogios-prazos.html) | Quem vence quando? (cenário ilustrativo) | Spec §8 |

## Dinheiro e operação

| # | Diagrama | Pergunta | Fonte |
|---|---|---|---|
| 25 | [Cálculo do dinheiro](25-calculo-dinheiro.html) | Como P, c, a, m, CM e total se relacionam? | Spec §7 |
| 26 | [Pagamento](26-pagamento.html) | Como Pix/cartão e webhook confirmam o pedido? | Spec §8.9, ADR 0009 |
| 27 | [Ledger de repasses](27-ledger-repasses.html) | Como os quatro destinos recebem e como revertem? | Spec §8.9, ADR 0010 |
| 28 | [Disputa assistida](28-disputa-assistida.html) | Como a MVA decide liberar, estornar ou reter 30%? | Spec §8.8, fase 5 |
| 29 | [Avaliação](29-avaliacao.html) | Como nota, resposta, moderação e média funcionam? | ADR 0014, fase 5 |
| 30 | [Notificações](30-notificacoes.html) | Como um evento vira in-app, e-mail e push? | Spec §8, fase 5 |
| 31 | [Backoffice](31-backoffice.html) | O que o operador da MVA vê e faz? | ADR 0012, fase 5 |

## Projeto

| # | Diagrama | Pergunta | Fonte |
|---|---|---|---|
| 32 | [EAP de entrega](32-eap-entrega.html) | Quais fases e work packages existem? | Spec §12, issues #1–#92 |
| 33 | [Roadmap e linha do tempo](33-roadmap-fases.html) | O que já aconteceu e qual é o próximo passo? | Spec, specs de fase, issues |
| 34 | [Acompanhamento do projeto](34-acompanhamento.html) | Quanto cada fase fechou, o que pode começar e onde está travado? | Issues do GitHub, Spec §12 |

## Publicação

O atlas publicado fica em
**[diegosouzafotografo-estrela.github.io/atlas-meu-vizinho-aprova](https://diegosouzafotografo-estrela.github.io/atlas-meu-vizinho-aprova/)**.

`pnpm atlas:publicar` copia os HTMLs para o repositório satélite público
(`atlas-meu-vizinho-aprova`, branch `gh-pages`), tira o link para o spec privado
e publica. A publicação é manual de propósito: o repositório de origem é
privado e o site é público, então cada envio é uma decisão de quem roda o
comando. O site também pede aos buscadores que não o indexem.

