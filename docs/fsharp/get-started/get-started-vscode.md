---
title: "Guia de Introdução com F # em código do Visual Studio com Ionide"
description: "Saiba como usar o F # com o código do Visual Studio e o conjunto de plug-in de Ionide."
keywords: "o Visual f #, f #, funcional de programação, o vscode .NET, o código do Visual Studio, Ionide"
author: cartermp
ms.author: phcart
ms.date: 09/28/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 49775139-082e-442f-b5a2-dd402399b5d2
ms.openlocfilehash: 336316eaf474f4c10d63657f178ce4a336ad7a54
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="getting-started-with-f-in-visual-studio-code-with-ionide"></a>Guia de Introdução com F # em código do Visual Studio com Ionide

Você pode escrever F # em [código do Visual Studio](https://code.visualstudio.com) com o [Ionide plug-in](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp), para obter uma ótima experiência IDE de leve e de plataforma cruzada com o IntelliSense e refatorações código básico.  Visite [Ionide.io](http://ionide.io) para saber mais sobre o conjunto de plug-in.

## <a name="prerequisites"></a>Pré-requisitos

F # 4.0 ou superior deve ser instalado em seu computador para usar Ionide.

Você também deve ter [git instalado](https://git-scm.com/download) e está disponível no seu caminho para fazer uso dos modelos de projeto em Ionide.  Você pode verificar se ele está instalado corretamente, digitando `git` em um pressionamento de prompt.and comando **Enter**.

### <a name="windows"></a>Windows

Se você estiver no Windows, você tem duas opções para a instalação do F #.

Se você já tiver instalado o Visual Studio e não tiver F #, você pode [instalar o Visual F # Tools](get-started-visual-studio.md#installing-f).  Isso instalará todos os componentes necessários para escrever, compilar e executar código F #.

Se você preferir não instalar o Visual Studio, use as instruções a seguir:

1. Instalar [do .NET Framework 4.5 ou superior](https://www.microsoft.com/en-US/download/details.aspx?id=30653) se você estiver executando o Windows 7.  Se você estiver usando o Windows 8 ou superior, você não precisa fazer isso.

2. Instale o SDK do Windows para o seu sistema operacional:

    * [Windows 10 SDK](https://dev.windows.com/en-US/downloads/windows-10-sdk)
    * [Windows 8.1 SDK](http://msdn.microsoft.com/windows/desktop/bg162891)
    * [Windows 8 SDK](http://msdn.microsoft.com/windows/hardware/hh852363.aspx)
    * [Windows 7 SDK](http://www.microsoft.com/download/details.aspx?id=8279)

3. Instalar o [Microsoft Build Tools 2015](https://www.microsoft.com/en-us/download/details.aspx?id=48159).  Você também precisa instalar [Microsoft Build Tools 2013](https://www.microsoft.com/en-us/download/details.aspx?id=40760).

4. Instalar o [ferramentas Visual F #](https://www.microsoft.com/en-us/download/details.aspx?id=48179).

No Windows de 64 bits, o compilador e ferramentas estão localizadas aqui:

```
C:\Program Files (x86)\Microsoft SDKs\F#\4.0\Framework\v4.0\fsc.exe
C:\Program Files (x86)\Microsoft SDKs\F#\4.0\Framework\v4.0\fsi.exe
C:\Program Files (x86)\Microsoft SDKs\F#\4.0\Framework\v4.0\fsiAnyCpu.exe
```

No Windows de 32 bits, as ferramentas de compilador estão localizadas aqui:

```
C:\Program Files\Microsoft SDKs\F#\4.0\Framework\v4.0\fsc.exe
C:\Program Files\Microsoft SDKs\F#\4.0\Framework\v4.0\fsi.exe
C:\Program Files\Microsoft SDKs\F#\4.0\Framework\v4.0\fsiAnyCpu.exe
```

Ionide detecta automaticamente o compilador e ferramentas, mas se ele não por algum motivo (por exemplo, o Visual F # Tools foi instalado para um diretório diferente), você pode adicionar manualmente a pasta que contém (`...\Microsoft SDKs\F#\4.0`) ao seu caminho.

### <a name="macos"></a>macOS

Em macOS, usa Ionide [Mono](http://www.mono-project.com).  A maneira mais fácil de instalar Mono em macOS é por meio de Homebrew.  Simplesmente digite o seguinte em seu terminal:

```
brew install mono
```

### <a name="linux"></a>Linux

No Linux, Ionide também usa [Mono](http://www.mono-project.com).  Se você estiver em Debian ou Ubuntu, você pode usar o seguinte:

```
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

## <a name="installing-visual-studio-code-and-the-ionide-plugin"></a>Instalando o plug-in Ionide e código do Visual Studio

Você pode instalar o Visual Studio Code do [code.visualstudio.com](https://code.visualstudio.com) site.  Depois disso, há duas maneiras de localizar o plug-in Ionide:

1. Use a paleta de comando (Ctrl + Shift + P no Windows, ⌘ + Shift + P em macOS, Ctrl + Shift + P no Linux) e digite o seguinte:

    ```
    >ext install Ionide
    ```

2. Clique no ícone de extensões e procure "Ionide":

    ![](media/getting-started-vscode/vscode-ext.png)

O plug-in somente necessário para suporte a F # no código do Visual Studio é [Ionide fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).  No entanto, você também pode instalar [Ionide FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) e obter [FORJAR](http://fsharp.github.io/FAKE/) suporte e [Ionide Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) para obter [Paket](https://fsprojects.github.io/Paket/) suporte.  FORJAR e Paket são ferramentas de comunidade adicionais F # para desenvolver projetos e gerenciar as dependências, respectivamente.

## <a name="creating-your-first-project-with-ionide"></a>Criando seu primeiro projeto com Ionide

Para criar um novo projeto de F #, abra o código do Visual Studio em uma nova pasta (você pode nomeá-lo como desejar).

![](media/getting-started-vscode/vscode-open-dir.png)

Em seguida, abra a paleta de comando (Ctrl + Shift + P no Windows, ⌘ + Shift + P em macOS, Ctrl + Shift + P no Linux) e digite o seguinte:

```
>f#: New Project
```

Isso é alimentado pelo [FORGE](https://github.com/fsharp-editing/Forge) projeto.  Você deve ver algo parecido com isso:

![](media/getting-started-vscode/vscode-new-proj.png)

> [!NOTE]
Se você não vir o acima, tente atualizar modelos executando o seguinte comando na paleta de comando: `>F#: Refresh Project Templates`.

Selecione "F #: novo projeto" acessando **Enter**, que levará você para esta etapa:

![](media/getting-started-vscode/vscode-proj-type.png)

Isso irá selecionar um modelo para um tipo específico de projeto.  Há algumas opções aqui, como um [FsLab](http://fslab.org) modelo para ciência de dados ou [Suave](https://suave.io) modelo de programação da Web.  Este artigo usa o `classlib` modelo, para realçar que e pressione **Enter**.  Em seguida, você vai chegar a etapa a seguir:

![](media/getting-started-vscode/vscode-new-dir.png)

Isso permite que você criar o projeto em um diretório diferente, se desejar.  Deixe em branco por enquanto.  Ele criará o projeto no diretório atual.  Depois que você pressionar **Enter**, você vai chegar a etapa a seguir:

![](media/getting-started-vscode/vscode-proj-name.png)

Permite que você nomeie seu projeto.  F # usa [Pascal case](http://c2.com/cgi/wiki?PascalCase) para os nomes de projeto.  Este artigo usa `ClassLibraryDemo` como o nome.  Depois de inserir o nome que você deseja para seu projeto, pressione **Enter**.

Se você seguiu as etapas da etapa anterior, você deve obter o Visual Studio código espaço de trabalho no lado esquerdo para algo parecido com isto:

![](media/getting-started-vscode/vscode-new-proj-explorer.png)

Esse modelo gera algumas coisas que você encontrará úteis:

1. O F # projeto em si, sob o `ClassLibraryDemo` pasta.
2. A estrutura de diretório correto para a adição de pacotes por meio de [ `Paket` ](http://fsprojects.github.io/Paket/).
3. Uma plataforma cruzada criar script com [ `FAKE` ](http://fsharp.github.io/FAKE/).
4. O `paket.exe` executável que pode buscar pacotes e resolver as dependências para você.
5. Um `.gitignore` de arquivo se deseja adicionar este projeto ao controle de origem com base no Git.

## <a name="writing-some-code"></a>Escrevendo um código

Abra o *ClassLibraryDemo* pasta.  Você deve ver os seguintes arquivos:

1. `ClassLibraryDemo.fs`, um arquivo de implementação do F # com uma classe definida.
2. `CassLibraryDemo.fsproj`, um arquivo de projeto F # usado para compilar este projeto.
3. `Script.fsx`, um arquivo de script F # que carrega o arquivo de origem.
4. `paket.references`, um arquivo Paket que especifica as dependências do projeto.

Abra `Script.fsx`e adicione o seguinte código ao final dele:

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

Esta função converte uma palavra em uma forma de [Pig latino](https://en.wikipedia.org/wiki/Pig_Latin).  A próxima etapa é avaliar usando F # interativo (FSI).

Realce a função inteira (deve ser 11 linhas).  Depois de selecioná-la, mantenha o **Alt** chave e clique em **Enter**.  Você observará que uma janela pop-up abaixo, e ele deverá mostrar algo assim:

![](media/getting-started-vscode/vscode-fsi.png)

Isso foi três coisas:

1. Iniciar o processo de FSI.
2. Ele enviado o código realçado sobre o processo FSI.
3. O processo FSI avaliado o código enviados pela.

Porque foi enviado por um [função](../language-reference/functions/index.md), agora você pode chamar essa função com FSI!  Na janela interativa, digite o seguinte:

```fsharp
toPigLatin "banana";;
```

Você deve ver o seguinte resultado:

```fsharp
val it : string = "ananabay"
```

Agora, vamos tentar com uma vogal como a primeira letra. Insira o seguinte:

```fsharp
toPigLatin "apple";;
```

Você deve ver o seguinte resultado:

```fsharp
val it : string = "appleyay"
```

A função parece estar funcionando conforme o esperado.  Parabéns, você criou sua primeira função F # em código do Visual Studio e avaliadas-lo com FSI apenas!

>[!NOTE]
Como você pode ter observado, as linhas no FSI são finalizadas com `;;`.  Isso ocorre porque FSI permite que você insira várias linhas.  O `;;` no final permite FSI saber quando o código for concluído.

## <a name="explaining-the-code"></a>Explicando o código

Se você não tiver certeza sobre o que o código está realmente fazendo, aqui está um passo a passo.

Como você pode ver, `toPigLatin` é uma função que usa uma palavra como sua entrada e o converte em uma representação de Pig-latino da palavra.  As regras para isso são da seguinte maneira:

Se o primeiro caractere em uma palavra começar com uma vogal, adicione "Sim" para o fim da palavra.  Se ele não começa com uma vogal, mover o primeiro caractere para o fim da palavra e "em" adicionar a ele.

Você pode ter observado FSI o seguinte:

```
val toPigLatin : word:string -> string
```

Isso indica que `toPigLatin` é uma função que aceita um `string` como entrada (chamado `word`) e retorna outro `string`.  Isso é conhecido como o [assinatura de tipo da função](https://fsharpforfunandprofit.com/posts/function-signatures/), uma parte fundamental da linguagem F # que é a chave para compreender o código F #.  Você também observa isso se você passar o mouse sobre a função no código do Visual Studio.

O corpo da função, você observará duas partes distintas:

1. Uma função interna, chamada `isVowel`, que determina se um determinado caractere (`c`) é uma vogal, verificando se ele corresponde a um dos padrões fornecidos por meio de [correspondência de padrões](../language-reference/pattern-matching.md):

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. Um [ `if..then..else` ](../language-reference/conditional-expressions-if-then-else.md) que verifica se o primeiro caractere é uma vogal e constrói um valor de retorno sem os caracteres de entrada com base em se o primeiro caractere a expressão era uma vogal ou não:

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

O fluxo de `toPigLatin` é assim:

Verifique se o primeiro caractere da palavra entrada é uma vogal.  Se for, anexe "Sim" para o fim da palavra.  Caso contrário, mover o primeiro caractere para o fim da palavra e "em" adicionar a ele.

Há uma coisa final a observar sobre isso: não há nenhuma instrução explícita para retornar da função, ao contrário de muitos outros idiomas lá.  Isso ocorre porque o F # é baseada em expressão, e a última expressão no corpo de uma função é o valor de retorno.  Porque `if..then..else` em si for uma expressão, o corpo do `then` bloco ou o corpo do `else` bloco será retornado, dependendo do valor de entrada.

## <a name="moving-your-script-code-into-the-implementation-file"></a>Movendo o código de script para o arquivo de implementação

As seções anteriores neste artigo demonstrou uma primeira etapa comum gravar código F #: gravar uma função inicial e executá-la interativamente com FSI.  Isso é conhecido como o desenvolvimento controlado por REPL, onde REPL significa "Loop de impressão avaliar leitura".  É uma ótima maneira de experimentar a funcionalidade até que você tenha algo em funcionamento.

A próxima etapa no desenvolvimento controlado por REPL é mover o código de trabalho em um arquivo de implementação do F #.  Ele então pode ser compilado pelo compilador F # em um assembly que pode ser executado.

Para começar, abra `ClassLibraryDemo.fs`.  Você observará que algum código já está em lá.  Vá em frente e excluir a definição de classe, mas deixe o [ `namespace` ](../language-reference/namespaces.md) declaração na parte superior.

Em seguida, crie um novo [ `module` ](../language-reference/modules.md) chamado `PigLatin` e copie o `toPigLatin` função nele assim:

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

Essa é uma das várias maneiras que você pode organizar funções no código F # e uma abordagem comum, se você deseja chamar o código do c# ou projetos do Visual Basic.

Em seguida, abra o `Script.fsx` novamente e excluir todo o `toPigLatin` funcionarão, mas certifique-se de manter as duas linhas seguintes no arquivo:

```
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

A primeira linha é necessária para FSI script para carregar `ClassLibraryDemo.fs`.  A segunda linha é uma conveniência: omiti-lo é opcional, mas você precisará digitar `open ClassLibraryDemo` em uma janela FSI se você quiser colocar o `ToPigLatin` módulo no escopo.

Em seguida, na janela FSI, chame a função com o `PigLatin` módulo definido anteriormente:

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

Sucesso!  Obter os mesmos resultados como antes, mas agora carregado de um arquivo de implementação do F #.  A principal diferença é que os arquivos de origem F # são compilados em assemblies que podem ser executados em qualquer lugar, não apenas em FSI.

## <a name="summary"></a>Resumo

Neste artigo, você aprendeu:

1. Como configurar o código do Visual Studio com Ionide.
2. Como criar seu primeiro projeto F # com Ionide.
3. Como usar o F # script para gravar sua primeira função F # em Ionide e, em seguida, execute-o no FSI.
4. Como migrar o código de script com fonte de F # e, em seguida, chamar esse código de FSI.

Você agora está pronto para escrever muito mais código F #, usando o código do Visual Studio e Ionide.

## <a name="troubleshooting"></a>Solução de problemas

Aqui estão algumas maneiras que você pode solucionar determinados problemas que possam ser executadas em:

1. Para obter recursos de Ionide de edição de código, os arquivos de F # precisam ser salvo em disco e dentro de uma pasta que está aberta no espaço de trabalho de código do Visual Studio.
2. Se tiver sido feitas alterações no sistema ou instalado Ionide pré-requisitos com código do Visual Studio abrir, reinicie o código do Visual Studio.
3. Verifique que você pode usar o compilador F # e F # interativo da linha de comando sem um caminho totalmente qualificado.  Você pode fazer isso digitando `fsc` em uma linha de comando para o compilador de F #, e `fsi` ou `fsharpi` para o Visual F # ferramentas no Windows e Mono no Mac/Linux, respectivamente.
4. Se você tem caracteres inválidos em seus diretórios de projeto, Ionide podem não funcionar.  Se esse for o caso, renomeie os diretórios do projeto.
5. Se nenhum dos comandos Ionide está trabalhando, verifique seu [associações de código do Visual Studio](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) para ver se você estiver substituindo-os por engano.
6. Se Ionide é dividido em seu computador e nenhum deles corrigiu o problema, tente remover o `ionide-fsharp` diretório em seu computador e reinstale o conjunto de plug-in.

Ionide é um projeto de código aberto criado e mantido por membros da comunidade do F #.  Reportar problemas e fique à vontade para contribuir no [Ionide-o VSCode: repositório FSharp GitHub](https://github.com/ionide/ionide-vscode-fsharp).

Se você tiver um problema ao relatório, siga [as instruções para obter logs para usar ao relatar um problema](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).

Você também pode pedir para obter ajuda da comunidade do F # em e desenvolvedores Ionide o [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).

## <a name="next-steps"></a>Próximas etapas

Para saber mais sobre F # e os recursos do idioma, check-out [Tour do F #](../tour.md).

## <a name="see-also"></a>Consulte também

[Tour do F#](../tour.md)

[Referência da Linguagem F#](../language-reference/index.md)

[Funções](../language-reference/functions/index.md)

[Módulos](../language-reference/modules.md)

[Namespaces](../language-reference/namespaces.md)

[O VSCode do Ionide: FSharp](https://github.com/ionide/ionide-vscode-fsharp)
