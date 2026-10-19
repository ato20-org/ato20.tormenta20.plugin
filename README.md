# Tormenta20 para o ATO20

Plugin que põe Tormenta20 no ATO20, em duas partes. É só o `manifest.json`,
sem código.

- **O sistema:** ao criar a campanha (ou depois, em Configuração da campanha,
  Sistema), ela nasce com FOR, DES, CON, INT, SAB e CAR, os medidores PV e PM,
  a ficha nos detalhes (Identidade, Combate, as 30 perícias, Habilidades,
  Ataques, Equipamento e Descrição) e 16 condições do jogo.
- **A ficha em PDF:** na lista de Personagens, **Importar ficha em PDF** cria
  o personagem a partir da ficha editável, com o PDF anexado como a ficha
  dele. Com o sistema aplicado, tudo cai nos detalhes do molde.

![A prévia do Importar ficha em PDF, com uma ficha de exemplo do Tormenta20](docs/importar-pdf.png)

## O sistema

| | Começa com |
| --- | --- |
| Atributos | FOR, DES, CON, INT, SAB e CAR, em 0, como no Jogo do Ano |
| Medidores | PV 20 e PM 6 |
| Identidade | jogador, raça, origem, classe, nível 1, divindade, experiência 0 |
| Combate | defesa 10, deslocamento 9m, armadura, escudo, proficiências |
| Perícias | as 30 da ficha, em 0 |
| Listas | Habilidades (raça e origem, classe e poderes, magias), Ataques, Equipamento (tibares) e Descrição (descrição, anotações) |
| Condições | Abalado, Apavorado, Confuso, Agarrado, Atordoado, Caído, Desprevenido, Fatigado, Enredado, Envenenado, Sangrando, Em chamas, Cego, Lento, Paralisado e Inconsciente |

A classe é texto, e não uma lista de opções: o personagem multiclasse escreve
"Guerreiro 3 / Clérigo 2", como na ficha. A campanha guarda até 16 condições;
as outras do livro o mestre acrescenta no cardápio. Envenenado, Sangrando e Em
chamas já vêm com o efeito na figura.

Aplicar junta ao que a campanha já tem: o que tiver o mesmo nome fica como o
mestre deixou.

## A ficha

O plugin lê a ficha **editável** (com formulário), a que tem os campos
`NOME DO PERSONAGEM`, `ModFor` e `PMs Totais`. A impressa, a digitalizada e a
que não tem formulário continuam entrando como anexo.

O PDF da ficha não vem no plugin: ela é da Jambô Editora.

## O que vira o quê

| Na ficha | No personagem |
| --- | --- |
| Nome | o nome |
| FOR, DES, CON, INT, SAB, CAR | atributos, pelo modificador (`ModFor`...), como no Jogo do Ano |
| PV e PM, atuais e totais | medidores PV e PM |
| Jogador, raça, origem, classe, nível, divindade, experiência | detalhes em Identidade |
| Defesa, deslocamento, armadura, escudo, proficiências | detalhes em Combate |
| As 30 perícias, pelo total | detalhes em Perícias |
| Habilidades de raça e origem, de classe, magias | detalhes em Habilidades |
| Descrição e anotações | detalhes em Descrição |
| Ataques (bônus, dano, crítico, tipo, alcance) | uma linha por ataque em Ataques |
| Itens e peso, tibares | Equipamento |

![A personagem criada a partir da ficha: atributos, PV e PM e a Identidade](docs/ficha.png)

![Os ataques da ficha, cada um com bônus, dano e crítico](docs/ataques.png)

O modificador e o total das perícias são calculados pela própria ficha. Quem
preenche num leitor de PDF que não recalcula (o navegador, a maioria dos
leitores no Linux) fica com eles desatualizados, e é isso que entra.

## Instalar

No ATO20: Configurações → Plugins → **Catálogo**, e **Instalar** no Tormenta20.
Quando sair versão nova, o mesmo botão vira **Atualizar**.

Pede o ATO20 com a API de plugins 10.

Num ATO20 sem o catálogo:

1. Clone o repositório (ou baixe o zip dele):

   ```
   git clone https://github.com/ato20-org/ato20.tormenta20.plugin
   ```

2. No ATO20, Configurações, Plugins, **Importar plugin**, e escolha a pasta.
