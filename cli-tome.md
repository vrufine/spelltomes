# _Command-Line Interface_

Uma das primeiras formas de se comunicar com computadores foi através de texto.
Estes primeiros terminais eram conectados a impressoras de telégrafo ([teletipos](https://pt.wikipedia.org/wiki/Teletipo)) que imprimiam em papel o que lhes era pedido.
Até hoje pode-se encontrar resquício disso, o termo _tty_ é uma abreviação para teletipo (_teletype_ em inglês) que também é um nome para terminal.

Mais tarde, monitores com a tecnologia de [tubos de raios catódicos (CRT)](https://pt.wikipedia.org/wiki/Tubo_de_raios_cat%C3%B3dicos) foram conectados a computadores.
A transição foi simplesmente trocar o papel pela tela. Ao invés de imprimir em tinta, imprimia-se no monitor.
As vantagens mais óbvias estavam na economia de papel e velocidade em que a informação era impressa na tela.

Como a programação consiste em escrever textos para serem interpretados por computadores,
essa interface de comandos, há tanto tempo criada, ainda se mostra bastante prática.

## _Shell_

A camada responsável por interpretar os comandos do usuário para a máquina é chamada de _shell_ (concha ou casca).
O _shell_ encobre a camada mais baixa de um sistema operacional, o seu _kernel_, escondendo suas complexidades e dos detalhes técnicos de sua interface.

Existem várias implementações diferentes de _shells_, a mais antiga era chamada somente de _shell_ foi distribuido no _Unix_ de 1971 a 1975.
Porém este _shell_ foi completamente reescrito por Setephen Bourne e distribuido a partir de 1979 no _Unix_, esta implementação é chamada de _Bourne Shell_.

Atualmente existem diversos _shells_, o mais comum sendo o `bash` ou _Bourne Again Shell_ que é uma brincadeira com o termo _Born again_ ("nascido de novo" em inglês).

## O _Shell_ `bash`

A linguagem de comandos `bash` está presente na maioria dos sistemas operacionais descendentes ou inspirados no _Unix_ como _shell_.
O _macOS X_ e diversas distribuições _Linux_ são exemplos desses sistemas.

Então é pelo `bash` que temos uma interface de comunicação com o computador, através de comandos implementados neste _shell_ podemos interagir com a máquina.

[Mais…](shell/bash.md)

## Comandos

Todo comando é um programa que pode ser chamado pelo `bash`.
Estes comandos ficam instalados em locais especificos do sistema em que o `bash` está configurado para buscar.

A maioria destes comandos terão nomes extremamente curtos para serem rápidos de digitar.

[Mais…](shell/bash.md)

## Comando `ls`

O comando `ls` lista o conteúdo do diretório.
Se você acabou de abrir o seu emulador de terminal, provavelmente o que lhe será apresentado como reposta é o conteúdo de seu diretório _home_.
Para visualizar uma lista do que temos no diretório basta digitar `ls` e apertar `↵` (_Enter_):

![ls no diretório home](media/ls.gif)

Este diretório que é seu "lar" (_home_) é representado também como til (`~`).
O motivo para isto é histórico, os teclados dos anos 70 (ADM-3A) para se digitar o til utilizava-se a tecla _home_.

[Mais…](file-system/ls.md)

## Estrutura de diretórios

Diretórios (ou pastas) no _Linux_ e nos _Unix_ são bastante diferentes do _Windows_.
Por exemplo, quando um _pendrive_ é conectado ele não vai aparecer como um novo disco, não existe sequer um `C:\`.
Pode-se parecer desnecessário e confusa a complexidade da estrutura de diretórios dos _Linux_ e _Unix_,
porém essa mesma complexidade permite uma maleabilidade enorme destes sistemas quando se trata de gerenciamento de discos e arquivos.

A estrutura de diretórios nos _Linux_ e _Unix_ consiste em um diretório raíz (em inglês: _root_) que é onde todos os outros diretórios e arquivos podem ser criados.

O diretório raís é referenciado por uma barra (`/`) e a partir dele é possível chegar a qualquer arquivo ou outro diretório dentro do sistema.

O diretório _home_ que é representado pelo `~` (til) encontra-se pelo caminho `/home/` e tem o nome de seu usuário, que seria por exemplo `/home/wizard/` para um usuario nomeado _wizard_,
Para o usuário _wizard_, o `~` referencia este diretório.
Estes são caminhos "absolutos", tem essa denominação pelo motivo de que estes caminhos indicam como chegar a um diretório (ou arquivo) a partir da raís do sistema.
Isso porque este caminho (ou _path_, em inglês) inicia com `/`, sem qualquer palavra antes desta barra, a única referencia que se pode assumir é que esta é a referencia à raís.

Um caminho como `Documents/arquivo_de_texto.txt` é chamado de caminho "relativo" por não apresentar o "trajeto" inteiro desde a raís do sistema, dessa forma este caminho será relativo à algum outro local.
Caminhos relativos fazem sentido por exemplo quando você quer abrir um diretório ou arquivo logo onde você está, sem ter que referenciar todo o caminho novamente a partir da raís.

Existem mais dois pontos a serem abordados sobre caminhos relativos:
1. o `.` (ponto);
2. e o `..` (ponto duplo, ou ponto-ponto).

O `.` é uma referência ao diretório atual, considerando que você esteja em `/home/wizard/Documents/`, o `.` é uma referência para este diretório.

Enquanto o `..` é uma referência ao diretório "pai" (ou _parent_), o diretório que contém o diretório atual, neste caso seria o `/home/wizard/`.

Todo diretório possui uma referência a ele mesmo (`.`) e ao seu _parent_ (`..`), no caso do diretório `/`, seu parent é ele mesmo.
O `.` é muito utilizado em casos que queremos executar algum arquivo que está logo no diretório que estamos:

![executa asciiquarium](media/executa-asciiquarium.gif)

Neste exemplo, existe um arquivo executável chamado `asciiquarium` no diretório que estamos e para poder executá-lo, precisamos informar que estamos executando algo do diretório atual.
Isso acontece por questões de segurança, executar alguma coisa sempre envolve algum risco e esta característica traz clareza a o que o usuário está querendo executar.

## Comando `pwd`

É uma sigla para _print the working directory_, ou seja, mostre o diretório em que estou trabalhando no momento.

![pwd no diretório home](media/pwd.gif)

O _output_ (ou resposta) do `pwd` então é o _path_ (caminho) "absoluto" de onde executamos este comando.

## Parâmetros

Ou também chamados de argumentos, são valores informados à direita de algum comando.
estes parâmetros são repassados para o comando que tem então seu comportamento alterado.

O uso de parâmetros é bastante intuitivo,
cada palavra ou número separada por um ou mais espaços em branco (` `) será considerada um parâmetro diferente.

Existem outros caracteres que tem uma importância especial para o `bash`, que vai além do seu significado literal.
Portanto são tratados de uma forma diferenciada e não são repassados como parâmetros.
Para ver a lista completa destes caracteres, veja a sessão de [caracteres especiais para o bash](shell/bash.md#caracteres-especiais).

Nos casos onde algum destes caracteres deveria fazer parte do parâmetro que você quer passar, a solução é simples:
basta colocar o parâmetro todo entre aspas simples (`'`), exemplo:
```bash
echo 'Olá mundo!'
```

Outra forma de fazer o mesmo é utilizando a barra invertida (`\`) antes do caractere que deveria ser ignorado por esse tratamento especial do `bash` e só repassada adiante.
Exemplo:
```bash
echo Olá\ mundo\!
```

Neste exemplo, o espaço logo após a palavra `Olá` está sendo ignorado pelo interpretador `bash` e simplesmente entendido como parte do parâmetro, da mesma forma que o ponto de exclamação.
Por causa deste comportamento, a barra invertida também é chamada de caractere de escape.

[Mais…](shell/bash.md)

## Comando `cd`

Para navegar por estes diretórios existe o comando `cd` (_change directory_).
Ele aceita um parâmetro, o diretório para o qual você pretende ir.

Por exemplo, para navegar até o diretório raíz, basta digitar o exemplo abaixo e apertar `↵` (_Enter_) ao final:
```bash
cd /
```

Caso não informado qualquer parâmetro para o comando `cd` o que irá acontecer é que o comando irá assumir o valor padrão e nos levará para o diretório _home_.
Isso porquê o valor padrão para o parâmetro deste comando é o seu _home_. Exemplo:
```bash
cd
```

Dessa forma, executar `cd` sem passar um diretório é a mesma coisa que usar a referência `~` ao _home_ como parâmetro:
```bash
cd ~
```

A forma fácil de se navegar para o direito "pai" do atual é usando a referência `..` vista anteriormente, exemplo:
```bash
cd ..
```

Uma outra referência que o `cd` oferece para facilitar é o `-` (sinal de menos),
usa-lo como parâmetro serve para voltar ao diretório que se estava antes da última execução do `cd`:
```bash
cd -
```

## Ganhando agilidade com o _autocomplete_

O "segredo" para ganhar agilidade na digitação na interface de comandos do `bash` é o _autocomplete_ ativado pela tecla [`Tab`](https://pt.wikipedia.org/wiki/Tabula%C3%A7%C3%A3o).
Este é um recurso bastante inteligente que nos poupa digitação.

Quando se está digitando qualquer coisa e preciona-se o `Tab`, é feita uma busca por todos os possíveis valores para a palavra que está sendo digitada.
Caso só exista uma opção, a palavra é completada automaticamente com um espaço ao final para continuar a digitar outras coisas.

Caso existam mais opções, somente será auto-completada a palavra até o ponto em comum com as outras opções:

![autocomplete file .bash_profile](media/autocomplete.gif)

Caso esteja digitando algo e o _autocomplete_ não completar nada é porque já existe mais de uma opção para o próximo caracter.
Apertar mais uma vez o `Tab` nesta situação resulta em uma lista dos possíveis valores para o que se está sendo digitado.

Caso a lista de valores possíveis seja grande, o `bash` irá perguntar se tem certeza que deseja listar todas as opções.

## Comando `file`

Uma característica interessante dos sistemas operacionais _Linux_ e _Unix_ é que estes não dependem de extensões (ex: `.jpg`, `.pdf`, `.doc`, etc.) dos arquivos para determinar o seu tipo.
O que acontece é que existem outras formas de se determinar o tipo de um arquivo, o uso de extensões que foi popularizado pelo _Windows_ não é a única forma.

Outras formas de se fazer isso é com base no início do conteúdo de o arquivo buscando por uma assinatura ([file signatures](https://en.wikipedia.org/wiki/List_of_file_signatures) - em inglês),
ou buscando pelo [_MIME Type_](https://pt.wikipedia.org/wiki/Tipo_de_m%C3%ADdia_da_Internet).

O comando `file` serve para identificarmos o tipo de um arquivo. Este comando recebe um parâmetro, que é o nome do arquivo que deseja-se identificar.

![file asciiquarium](media/file.gif)

Caso pergunte por um diretório, a resposta será simplesmente `file-system: directory`.

## Comando `locate`

- `updatedb`

## Comando `mv`

## Comando `cp`

## Comando `rm`

## Comando `mkdir`

## Comando `rmdir`

## Comando `touch`

- atualiza a data de edição de um arquivo

- caso não exista o arquivo requisitado, cria o arquivo vazio

## Comando `history`

## O atalho **Control C**

## Os comandos `whatis` e `man`

## As _Flags_

## Os _Status_ que os comandos retornam
