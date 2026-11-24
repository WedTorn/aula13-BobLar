# Registro · Aula 13 · Explorando o Bootstrap

**Aluno:** Wesley Ferreira
**Disciplina:** Desenvolvimento para Internet · Prof. Felipe Santos de Jesus
**Projeto:** Bob Lar · Adoção de Cães

## 1. Tema, público e finalidade
- **Tema:** adoção responsável de cães. O nome homenageia o Bob, meu cachorro, que é o mascote do abrigo.
- **Público:** pessoas e famílias que pensam em adotar um cão.
- **Finalidade:** apresentar o abrigo (fictício), mostrar os cães disponíveis e explicar como adotar. O contato é feito por e-mail (`mailto:`); o site não simula cadastro, reserva nem envio de formulário.

## 2. Organização dos arquivos
```
bob-lar/
├── index.html        (página principal: as 6 áreas do modelo)
├── caes-2.html       (segunda página da lista de cães · paginação)
├── estilo.css        (CSS próprio, carregado DEPOIS do Bootstrap)
├── registro.md
├── imagens/          (fotos recortadas e otimizadas)
├── esbocos/          (esboco-computador.png e esboco-celular.png)
└── capturas/         (2 páginas × 3 telas)
```
Bootstrap **5.3.8** carregado pela CDN (jsDelivr), como na Aula 13: o CSS no `head`, antes do `estilo.css`, e o `bootstrap.bundle.min.js` uma única vez, antes de fechar o `body`. Sem jQuery. O projeto precisa de internet para carregar o Bootstrap.

## 3. As seis áreas do modelo
| Área | Onde | Conteúdo |
|---|---|---|
| Menu | as duas páginas | Marca "Bob Lar" e 4 destinos reais: Início, Destaques, Cães, Como adotar. |
| 1 · Apresentação | `index.html#inicio` | Título principal, parágrafo autoral, botões "Conhecer os cães" e "Como adotar", foto do Bob. |
| 2 · Destaques | `index.html#destaques` | Carrossel com 3 fotos e legendas: Resgate, Passeios diários, Uma nova família. |
| 3 · Coleção | `#caes` nas duas páginas | 6 cards (3 por página), cada um com foto, nome, idade/porte, descrição e botão. |
| 4 · Paginação | abaixo dos cards | Liga a página 1 e a página 2 nos dois sentidos. |
| 5 · Sobre | `index.html#como-adotar` | Texto sobre adoção responsável e 4 passos. |
| 6 · Rodapé | as duas páginas | Autoria, contato fictício e fontes de todas as imagens. |

## 4. Componentes Bootstrap (5 tipos)
Obrigatórios: navbar, buttons, cards. Escolhidos: **carousel** (interativo) e **pagination**.

- **Navbar:** Usei a navbar no topo das duas páginas para navegar entre as seções. Adaptei a cor de fundo (azul-petróleo da marca, `.bg-marca`), deixei o menu fixo no topo (`sticky-top`) e alinhei os links à direita (`ms-auto`). Testei o botão ☰ em 375px: o menu abre e fecha, e o `aria-expanded` muda de `false` para `true`.
- **Buttons:** Usei botões na apresentação, nos cards e em "Como adotar" para levar à lista de cães ou abrir o e-mail. Adaptei as cores das variantes `btn-primary` e `btn-outline-primary` pelas variáveis `--bs-btn-*` no meu CSS. Testei os links e o foco pelo teclado.
- **Card:** Usei cards na seção Cães para apresentar cada cão. Adaptei a imagem para a proporção 4:3 com `object-fit: cover`, tirei a borda, arredondei os cantos e coloquei o botão sempre no fim do card (`d-flex flex-column` + `mt-auto`). Testei a grade em 375px (1 coluna), 768px (2 colunas) e 992px (3 colunas).
- **Carousel:** Usei o carrossel na seção Destaques para mostrar o resgate, o passeio e a adoção. Adaptei a legenda com um degradê escuro para ficar legível, aumentei os controles com um fundo circular e, no celular, deixei a foto em 4:3 para a legenda não cobrir o cão. Testei "Próxima" três vezes (1 → 2 → 3 → 1) e "Anterior" uma vez (1 → 3). Ele não avança sozinho: sem `data-bs-ride`.
- **Pagination:** Usei a paginação abaixo dos cards para dividir a lista de cães em duas páginas com cães diferentes. Adaptei as cores pelas variáveis `--bs-pagination-*` e centralizei a lista (`justify-content-center`). Testei os dois sentidos: na página 1, "2" e "Próxima" levam à página 2; na página 2, "1" e "Anterior" voltam. A página atual tem `active` e `aria-current="page"`, e o texto "Página 1 de 2" não depende só da cor.

## 5. Responsividade (grade do Bootstrap)
| Largura | Menu | Apresentação | Cards |
|---|---|---|---|
| até 767px | recolhido no botão ☰ | texto em cima, foto embaixo | 1 por linha (`col-12`) |
| 768px a 991px (`md`) | links visíveis (`navbar-expand-md`) | texto e foto lado a lado (`col-md-6`) | 2 por linha (`col-md-6`), o 3º embaixo |
| a partir de 992px (`lg`) | links visíveis | lado a lado | 3 por linha (`col-lg-4`) |

Abaixo de 576px, o carrossel usa fotos 4:3 (media query no `estilo.css`).

## 6. Imagens
Todas foram recortadas para proporções iguais (carrossel 16:9 e cards 4:3), reduzidas e salvas em JPG otimizado.

| Arquivo | Onde | Autoria e origem |
|---|---|---|
| `bob.jpg` | Apresentação | Acervo pessoal do autor (o Bob é meu cachorro). |
| `carrossel-passeio.jpg` | Carrossel | Acervo pessoal do autor. |
| `cao-zeca.jpg` | Card (página 2) | Acervo pessoal do autor. |
| `carrossel-resgate.jpg` | Carrossel | jacksonmoccelin · Pixabay · imagem 8590529. |
| `carrossel-familia.jpg` | Carrossel | huynhly024 · Pixabay · imagem 6518232. |
| `cao-canela.jpg` | Card (página 1) | Engin Akyurt · Pixabay · imagem 6934895. |
| `cao-pipoca.jpg` | Card (página 1) | Pexels · Pixabay · imagem 1851108. |
| `cao-neve.jpg` | Card (página 1) | usuário 3194556 · Pixabay · imagem 1903313. |
| `cao-rengar.jpg` | Card (página 2) | mtajmr · Pixabay · imagem 2679639. |
| `cao-boneco.jpg` | Card (página 2) | rebeccaspictures · Pixabay · imagem 5232065. |

As fotos do Pixabay seguem a Licença de Conteúdo do Pixabay (uso gratuito). Nomes, idades e histórias dos cães são fictícios.

## 7. Acessibilidade
- `lang="pt-BR"`, `charset="utf-8"` e `meta viewport` nas duas páginas; zoom não bloqueado.
- Todas as fotos têm `alt` descritivo; `width` e `height` no HTML reservam a proporção.
- Hierarquia: um `h1` por página, `h2` nas seções e `h3` nos cards e legendas.
- Foco visível em todos os links e botões: contorno escuro no fundo claro (10,2:1) e amarelo no menu e no rodapé (3,7:1 e 5,3:1). Foi preciso usar seletores mais específicos que os do Bootstrap, que trocam o contorno por uma sombra discreta.
- Contraste do texto: 12,5:1; branco sobre os botões: 7,6:1.
- Controles do carrossel com texto escondido ("Anterior", "Próxima") e indicadores "Imagem 1 de 3".

## 8. Testes
Feitos no Chromium (modo responsivo). "Rolagem lateral" conferida comparando a largura do documento com a da janela.

| Página | Largura × altura | Observado | Problema | Correção |
|---|---|---|---|---|
| Ambas | 320 × 640 | Menu recolhido, tudo em 1 coluna | — | Passou |
| Ambas | 375 × 812 | Menu recolhido, cards em 1 coluna | Legenda do carrossel cobria a foto | Foto 4:3 abaixo de 576px |
| Ambas | 767 × 900 | Ainda 1 coluna e menu ☰ | — | Passou |
| Ambas | 768 × 1024 | Menu aberto; cards 2 + 1 | — | Passou |
| Ambas | 991 / 992 | 991: 2 colunas; 992: 3 colunas | — | Passou |
| Ambas | 1366 × 768 | 3 cards na mesma linha | — | Passou |
| Ambas | todas | Fotos esticadas na altura | `height` do HTML fixava a altura | `img { height: auto; }` no CSS |
| index | Menu ☰ | Abre, fecha e leva à seção | — | Passou |
| index | Carrossel | Próxima/Anterior funcionam; parado após 6 s | — | Passou |
| Ambas | Paginação | Vai para a página 2 e volta | — | Passou |
| Ambas | Tab | Foco não aparecia nos links do menu e nos botões | Regra do Bootstrap mais específica | Seletores `.btn:focus-visible` etc. |
| Ambas | Sem rolagem lateral | Nenhuma largura teve rolagem lateral | — | Passou |

## 9. Esboços e capturas
- `esbocos/esboco-computador.png` e `esbocos/esboco-celular.png`: as seis áreas numeradas, o que fica lado a lado e o que é empilhado.
- `capturas/`: `index-375x812.png`, `index-768x1024.png`, `index-1366x768.png`, `caes-2-375x812.png`, `caes-2-768x1024.png`, `caes-2-1366x768.png`.
