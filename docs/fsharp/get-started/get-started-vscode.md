---
title: 'Introdução ao F # no Visual Studio Code'
description: 'Saiba como usar F # com o Visual Studio Code e o conjunto de plug-in de Ionide.'
ms.date: 05/28/2018
ms.openlocfilehash: e962be2796cf0d6eb90d459730659e492f864716
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192662"
---
# <a name="get-started-with-f-in-visual-studio-code"></a>Introdução ao F # no Visual Studio Code

Você pode escrever F # no [Visual Studio Code](https://code.visualstudio.com) com o [plug-in do Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) para obter uma ótima experiência de ambiente de desenvolvimento integrado (IDE) de plataforma cruzada, mais leve, com o IntelliSense e o código básico refatorações. Visite [Ionide.io](http://ionide.io) para saber mais sobre o plug-in.

Para começar, certifique-se de que você tenha [F # e o plug-in Ionide instalado corretamente](install-fsharp.md#install-f-with-visual-studio-code).

## <a name="creating-your-first-project-with-ionide"></a>Criando seu primeiro projeto com Ionide

Para criar um novo projeto F #, abra o Visual Studio Code em uma nova pasta (você pode nomeá-lo que você quiser).

Em seguida, abra a paleta de comandos (**exibição > Paleta de comandos**) e digite o seguinte:

```
> F# new project
```

Isso é alimentado pela [FORJAR](https://github.com/fsharp-editing/Forge) projeto.

> [!NOTE]
Se você não vir Opções de modelo, tente atualizar modelos executando o seguinte comando na paleta de comandos: `>F#: Refresh Project Templates`.

Selecione ": novo projeto de F #" pressionando **Enter**. Isso leva você para a próxima etapa é selecionar um modelo de projeto.

Escolher o `classlib` modelo e pressione **Enter**.

Em seguida, escolha um diretório para criar o projeto no. Se você deixar em branco, ele usa o diretório atual.

Por fim, nomeie o projeto na etapa final. F # usa [Pascal case](http://c2.com/cgi/wiki?PascalCase) para nomes de projetos. Este artigo usa `ClassLibraryDemo` como o nome. Depois de inserir o nome que você deseja para seu projeto, pressione **Enter**.

Se você seguiu a etapa anterior, você deve obter o Visual Studio código espaço de trabalho no lado esquerdo seja exibido com o seguinte:

1. O F # projeto em si, sob o `ClassLibraryDemo` pasta.
2. A estrutura de diretório correto para adicionar pacotes via [ `Paket` ](https://fsprojects.github.io/Paket/).
3. Script com de construção de uma plataforma cruzada [ `FAKE` ](https://fsharp.github.io/FAKE/).
4. O `paket.exe` executável que pode buscar pacotes e resolver as dependências para você.
5. Um `.gitignore` arquivo se você deseja adicionar este projeto ao controle de origem com base em Git.

## <a name="writing-some-code"></a>Escrever o código

Abra o *ClassLibraryDemo* pasta.  Você verá os seguintes arquivos:

1. `ClassLibraryDemo.fs`, um arquivo de implementação do F # com uma classe definida.
2. `ClassLibraryDemo.fsproj`, um arquivo de projeto F # usado para compilar esse projeto.
3. `Script.fsx`, um arquivo de script F # que carrega o arquivo de origem.
4. `paket.references`, um arquivo de Paket que especifica as dependências do projeto.

Abra `Script.fsx`e adicione o seguinte código ao final dele:

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

Esta função converte uma palavra em uma forma de [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin). A próxima etapa é avaliá-lo usando a linguagem F # interativo (FSI).

Realce a função inteira (deve ser 11 linhas de comprimento). Depois que ele é realçado, mantenha o **Alt** chave e clique em **Enter**. Você observará uma janela pop-up abaixo, e ele deve mostrar algo parecido com isto:

![Exemplo de saída de F # interativo com Ionide](media/getting-started-vscode/vscode-fsi.png)

Isso fazia três coisas:

1. Ele iniciou o processo FSI.
2. Ele enviado o código realçado ao longo do processo FSI.
3. O processo FSI avaliado o código enviado ao longo.

Porque era enviados por um [função](../language-reference/functions/index.md), agora você pode chamar essa função com FSI! Na janela interativa, digite o seguinte:

```fsharp
toPigLatin "banana";;
```

Você deverá ver o seguinte resultado:

```fsharp
val it : string = "ananabay"
```

Agora, vamos tentar com uma vogal como a primeira letra. Insira o seguinte:

```fsharp
toPigLatin "apple";;
```

Você deverá ver o seguinte resultado:

```fsharp
val it : string = "appleyay"
```

A função parece estar funcionando conforme o esperado. Parabéns, você escreveu sua primeira função F # no Visual Studio Code e avaliado-lo com FSI apenas!

>[!NOTE]
Como você pode ter notado, as linhas no FSI são finalizadas com `;;`. Isso ocorre porque FSI permite que você insira várias linhas. O `;;` no final informa FSI quando o código for concluído.

## <a name="explaining-the-code"></a>Explicando o código

Se você não tiver certeza sobre o que o código está realmente fazendo, aqui está um passo a passo.

Como você pode ver, `toPigLatin` é uma função que leva a uma palavra como sua entrada e o converte em uma representação de Pig Latin dessa palavra. As regras para isso são da seguinte maneira:

Se o primeiro caractere em uma palavra começa com uma vogal, adicione "Sim" ao final da palavra. Se ele não começa com uma vogal, mover desse primeiro caractere para o fim da palavra e "em" adicionar a ele.

Você talvez tenha observado a seguir no FSI:

```fsharp
val toPigLatin : word:string -> string
```

Isso indica que `toPigLatin` é uma função que usa um `string` como entrada (chamado `word`) e retorna outra `string`. Isso é conhecido como o [assinatura de tipo da função](https://fsharpforfunandprofit.com/posts/function-signatures/), uma parte fundamental do F # que é a chave para entender o código F #. Você também perceberá isso se você passar o mouse sobre a função no Visual Studio Code.

O corpo da função, você observará duas partes distintas:

1. Uma função interna, chamada `isVowel`, que determina se um determinado caractere (`c`) é uma vogal, verificando se ele corresponder a um dos padrões fornecidos via [correspondência de padrões](../language-reference/pattern-matching.md):

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. Uma [ `if..then..else` ](../language-reference/conditional-expressions-if-then-else.md) expressão que verifica se o primeiro caractere é uma vogal e construções de um retorno de valor sem os caracteres de entrada com base em se o primeiro caractere foi uma vogal ou não:

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

O fluxo de `toPigLatin` , portanto, é:

Verifique se o primeiro caractere da palavra entrada é uma vogal. Se for, anexe "Sim" para o fim da palavra. Caso contrário, mover desse primeiro caractere para o fim da palavra e "em" adicionar a ele.

Há uma coisa final a observar sobre isso: não há nenhuma instrução explícita para retornar da função, ao contrário de muitos outros idiomas por aí. Isso ocorre porque o F # é baseada em expressão, e a última expressão no corpo de uma função é o valor retornado. Porque `if..then..else` em si for uma expressão, o corpo dos `then` bloco ou no corpo do `else` bloco será retornado, dependendo do valor de entrada.

## <a name="moving-your-script-code-into-the-implementation-file"></a>Mover o código de script no arquivo de implementação

As seções anteriores deste artigo demonstrou uma primeira etapa comum ao escrever código F #: gravar uma função inicial e executá-lo interativamente com FSI. Isso é conhecido como o desenvolvimento controlado por REPL, onde [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) significa "Loop de leitura-avaliação-impressão". É uma ótima maneira de experimentar a funcionalidade até que você tenha algo em funcionamento.

A próxima etapa no desenvolvimento controlado por REPL é mover o código de trabalho para um arquivo de implementação F #. Ele, em seguida, pode ser compilado pelo compilador do F # em um assembly que pode ser executado.

Para começar, abra `ClassLibraryDemo.fs`.  Você observará que algum código já está em lá. Vá em frente e exclua a definição de classe, mas deixe o [ `namespace` ](../language-reference/namespaces.md) declaração na parte superior.

Em seguida, crie um novo [ `module` ](../language-reference/modules.md) chamado `PigLatin` e copie o `toPigLatin` função nele assim:

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

Em seguida, abra o `Script.fsx` novamente e excluir todo o `toPigLatin` funcionar, mas certifique-se de manter as duas linhas seguintes no arquivo:

```fsharp
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

A primeira linha é necessária para FSI de script para carregar `ClassLibraryDemo.fs`. A segunda linha é uma conveniência: omiti-lo é opcional, mas você precisará digitar `open ClassLibraryDemo` em uma janela FSI se você quiser colocar o `ToPigLatin` módulo dentro do escopo.

Em seguida, na janela FSI, chame a função com o `PigLatin` módulo que você definiu anteriormente:

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

Sucesso! Obter os mesmos resultados que antes, mas agora é carregado de um arquivo de implementação F #. A principal diferença é que os arquivos de origem do F # são compilados em assemblies que podem ser executados em qualquer lugar, não apenas na FSI.

## <a name="summary"></a>Resumo

Neste artigo, você aprendeu:

1. Como configurar o Visual Studio Code com Ionide.
2. Como criar seu primeiro projeto F # com Ionide.
3. Como usar o F # script para escrever sua primeira função F # em Ionide e, em seguida, execute-o na FSI.
4. Como migrar seu código de script para o código-fonte do F # e, em seguida, chama esse código de FSI.

Você agora está pronto para escrever muito mais código do F # usando o Visual Studio Code e Ionide.

## <a name="troubleshooting"></a>Solução de problemas

Aqui estão algumas maneiras que você pode solucionar alguns problemas que você pode executar:

1. Para obter recursos de Ionide de edição de código, os arquivos de F # precisam ser salvos em disco e de dentro de uma pasta que está aberta no espaço de trabalho do Visual Studio Code.
2. Se você fez alterações ao seu sistema ou instalar pré-requisitos de Ionide abrir o Visual Studio Code, reinicie o Visual Studio Code.
3. Verifique que você pode usar o compilador F # e F # interativo da linha de comando sem um caminho totalmente qualificado. Você pode fazer isso digitando `fsc` em uma linha de comando para o compilador F #, e `fsi` ou `fsharpi` para o Visual F # ferramentas no Windows e o Mono no Mac/Linux, respectivamente.
4. Se você tiver caracteres inválidos em seus diretórios de projeto, Ionide pode não funcionar.  Se esse for o caso, renomeie os diretórios de projeto.
5. Se nenhum dos comandos Ionide estão funcionando, verifique sua [associações de teclas do Visual Studio Code](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) para ver se você estiver substituindo-os por acidente.
6. Se Ionide é dividido em seu computador e nenhum deles tiver corrigido o problema, tente remover o `ionide-fsharp` diretório em seu computador e reinstale o pacote de plug-in.

Ionide é um projeto de código-fonte aberto criado e mantido por membros da comunidade do F #. Reportar problemas e fique à vontade contribuir com o [Ionide VSCode: repositório FSharp GitHub](https://github.com/ionide/ionide-vscode-fsharp).

Se você tiver um problema ao relatório, siga [as instruções para obter os logs para usar ao relatar um problema](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).

Você também pode fazer para obter ajuda dos desenvolvedores Ionide e comunidade do F # na [Ionide Gitter canal](https://gitter.im/ionide/ionide-project).

## <a name="next-steps"></a>Próximas etapas

Para saber mais sobre F # e os recursos da linguagem, fazer check-out [Tour do F #](../tour.md).
