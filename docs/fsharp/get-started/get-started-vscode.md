---
title: Introdução ao F# no Visual Studio Code
description: Saiba como usar F# o com Visual Studio Code e o pacote de plug-in Ionide.
ms.date: 12/23/2018
ms.openlocfilehash: 2fa0518488d37b2130aaba96028ac92dac77eb97
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082993"
---
# <a name="get-started-with-f-in-visual-studio-code"></a>Introdução ao F# no Visual Studio Code

Você pode escrever F# em [Visual Studio Code](https://code.visualstudio.com) com o [plug-in Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) para obter uma experiência excelente de plataforma cruzada, ambiente de desenvolvimento integrado leve (IDE) com IntelliSense e refatoração de código básico. Visite [Ionide.Io](http://ionide.io) para saber mais sobre o plug-in.

Para começar, verifique se você tem [ F# o e o plug-in Ionide instalado corretamente](install-fsharp.md#install-f-with-visual-studio-code).

> [!NOTE]
> O Ionide vai gerar F# projetos de .NET Framework, não o núcleo dotnet, que pode ter problemas de compatibilidade entre plataformas. Se você estiver executando no **Linux** ou no **OSX**, uma maneira mais simples de começar é usar as [ferramentas de linha de comando](get-started-command-line.md).

## <a name="creating-your-first-project-with-ionide"></a>Criando seu primeiro projeto com o Ionide

Para criar um novo F# projeto, abra Visual Studio Code em uma nova pasta (você pode nomeá-lo como desejar).

Em seguida, abra a paleta de comandos (**exibir > paleta de comandos**) e digite o seguinte:

```console
> F# new project
```

Isso é alimentado pelo projeto [de forjação](https://github.com/fsharp-editing/Forge).

> [!NOTE]
> Se você não vir opções de modelo, tente atualizar modelos executando o seguinte comando na paleta de comandos: `>F#: Refresh Project Templates`.

Selecione "F#: Novo projeto "ao pressionar **Enter**. Isso levará você para a próxima etapa, que é para selecionar um modelo de projeto.

Escolha o `classlib` modelo e pressione **Enter**.

Em seguida, escolha um diretório no qual criar o projeto. Se você deixá-lo em branco, ele usará o diretório atual.

Por fim, nomeie o projeto na etapa final. F#usa o [caso do Pascal](http://c2.com/cgi/wiki?PascalCase) para nomes de projeto. Este artigo usa `ClassLibraryDemo` como o nome. Depois de inserir o nome desejado para o seu projeto, pressione **Enter**.

Se você seguiu a etapa anterior, deverá obter o espaço de trabalho Visual Studio Code no lado esquerdo para aparecer com o seguinte:

1. O F# projeto em si, sob `ClassLibraryDemo` a pasta.
2. A estrutura de diretório correta para adicionar pacotes [`Paket`](https://fsprojects.github.io/Paket/)via.
3. Um script de Build de plataforma cruzada com [`FAKE`](https://fsharp.github.io/FAKE/).
4. O `paket.exe` executável que pode buscar pacotes e resolver dependências para você.
5. Um `.gitignore` arquivo se você quiser adicionar este projeto ao controle do código-fonte baseado em git.

## <a name="writing-some-code"></a>Escrevendo código

Abra a pasta *ClassLibraryDemo* .  Você deve ver os seguintes arquivos:

1. `ClassLibraryDemo.fs`, um F# arquivo de implementação com uma classe definida.
2. `ClassLibraryDemo.fsproj`, um F# arquivo de projeto usado para compilar este projeto.
3. `Script.fsx`, um F# arquivo de script que carrega o arquivo de origem.
4. `paket.references`, um arquivo paket que especifica as dependências do projeto.

Abra `Script.fsx`o e adicione o seguinte código ao final dele:

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

Essa função converte uma palavra em uma forma de [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin). A próxima etapa é avaliá-lo F# usando o Interactive (FSI).

Realce a função inteira (deve ter 11 linhas). Depois de realçado, mantenha pressionada a tecla **ALT** e pressione **Enter**. Você notará uma janela pop-up abaixo e deverá mostrar algo assim:

![Exemplo de F# saída interativa com Ionide](./media/getting-started-vscode/vscode-fsi.png)

Isso fazia três coisas:

1. Ele iniciou o processo FSI.
2. Ele enviou o código realçado sobre o processo FSI.
3. O processo do FSI avaliou o código que você enviou.

Como o que você enviou foi uma [função](../language-reference/functions/index.md), agora você pode chamar essa função com o FSI! Na janela interativa, digite o seguinte:

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

A função parece estar funcionando conforme o esperado. Parabéns, você acabou de escrever sua F# primeira função em Visual Studio Code e a avaliou com o FSI!

> [!NOTE]
> Como você deve ter notado, as linhas no FSI são encerradas `;;`com. Isso ocorre porque o FSI permite que você insira várias linhas. O `;;` no final permite que o FSI saiba quando o código é concluído.

## <a name="explaining-the-code"></a>Explicando o código

Se você não tiver certeza sobre o que o código está realmente fazendo, aqui está um passo a passo.

Como você pode ver, `toPigLatin` é uma função que usa uma palavra como sua entrada e a converte em uma representação Pig-Latin dessa palavra. As regras para isso são as seguintes:

Se o primeiro caractere em uma palavra começar com uma vogal, adicione "Sim" ao final da palavra. Se não começar com uma vogal, mova o primeiro caractere para o final da palavra e adicione "o".

Você pode ter notado o seguinte no FSI:

```fsharp
val toPigLatin : word:string -> string
```

Isso declara que `toPigLatin` é uma função que usa `string` como entrada (chamada `word`) e retorna outra `string`. Isso é conhecido como a [assinatura de tipo da função](https://fsharpforfunandprofit.com/posts/function-signatures/), uma parte fundamental da F# chave para entender F# o código. Você também observará isso se passar o mouse sobre a função em Visual Studio Code.

No corpo da função, você observará duas partes distintas:

1. Uma função interna, chamada `isVowel`, que determina se um determinado caractere (`c`) é uma vogal verificando se ele corresponde a um dos padrões fornecidos por meio de [correspondência de padrões](../language-reference/pattern-matching.md):

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. Uma [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expressão que verifica se o primeiro caractere é uma vogal e constrói um valor de retorno dos caracteres de entrada com base em se o primeiro caractere era uma vogal ou não:

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

O fluxo de `toPigLatin` é assim:

Verifique se o primeiro caractere da palavra de entrada é uma vogal. Se for, anexe "Sim" ao final da palavra. Caso contrário, mova esse primeiro caractere para o final da palavra e adicione "

Há uma coisa final a ser observada sobre isso: não há nenhuma instrução explícita para retornar da função, ao contrário de muitas outras linguagens. Isso ocorre porque F# o é baseado em expressão e a última expressão no corpo de uma função é o valor de retorno. Como `if..then..else` o próprio é uma expressão, o corpo `then` do bloco `else` ou o corpo do bloco será retornado dependendo do valor de entrada.

## <a name="moving-your-script-code-into-the-implementation-file"></a>Movendo o código do script para o arquivo de implementação

As seções anteriores neste artigo demonstraram uma primeira etapa comum na escrita F# de código: escrever uma função inicial e executá-la interativamente com o FSI. Isso é conhecido como desenvolvimento controlado por REPL, em que [repl](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) significa "Read-Evaluate-Print loop". É uma ótima maneira de experimentar a funcionalidade até que você tenha algo funcionando.

A próxima etapa no desenvolvimento controlado por REPL é mover o código funcional para um F# arquivo de implementação. Em seguida, ele pode ser compilado F# pelo compilador em um assembly que pode ser executado.

Para começar, abra `ClassLibraryDemo.fs`.  Você observará que algum código já está lá. Vá em frente e exclua a definição de classe, mas lembre- [`namespace`](../language-reference/namespaces.md) se de deixar a declaração na parte superior.

Em seguida, crie um [`module`](../language-reference/modules.md) novo `PigLatin` chamado e copie `toPigLatin` a função para ele da seguinte maneira:

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

Em seguida, abra `Script.fsx` o arquivo novamente e exclua a `toPigLatin` função inteira, mas certifique-se de manter as duas linhas a seguir no arquivo:

```fsharp
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

Selecione as duas linhas de texto e pressione Alt + Enter para executar essas linhas no FSI. Eles carregarão o conteúdo da biblioteca Pig Latin no processo FSI e `open` o `ClassLibraryDemo` namespace para que você tenha acesso à funcionalidade.

Em seguida, na janela do FSI, chame a função com `PigLatin` o módulo que você definiu anteriormente:

```console
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

Êxito! Você Obtém os mesmos resultados que antes, mas agora é carregado de F# um arquivo de implementação. A principal diferença aqui é que F# os arquivos de origem são compilados em assemblies que podem ser executados em qualquer lugar, não apenas no FSI.

## <a name="summary"></a>Resumo

Neste artigo, você aprendeu:

1. Como configurar Visual Studio Code com o Ionide.
2. Como criar seu primeiro F# projeto com o Ionide.
3. Como usar F# o script para escrever sua primeira F# função em Ionide e executá-la no FSI.
4. Como migrar seu código de script F# para origem e, em seguida, chamar esse código do FSI.

Agora você está equipado para escrever muito mais F# código usando Visual Studio Code e Ionide.

## <a name="troubleshooting"></a>Solução de problemas

Aqui estão algumas maneiras de solucionar alguns problemas que você pode encontrar:

1. Para obter os recursos de edição de código do Ionide F# , os arquivos precisam ser salvos em disco e dentro de uma pasta que está aberta no espaço de trabalho Visual Studio Code.
2. Se você fez alterações no seu sistema ou instalou os pré-requisitos do Ionide com Visual Studio Code abrir, reinicie o Visual Studio Code.
3. Verifique se você pode usar o F# compilador e F# interativo da linha de comando sem um caminho totalmente qualificado. Você pode fazer isso digitando `fsc` uma linha de comando para o F# compilador e `fsi` ou `fsharpi` para as ferramentas visuais F# no Windows e mono no Mac/Linux, respectivamente.
4. Se você tiver caracteres inválidos em seus diretórios de projeto, o Ionide poderá não funcionar.  Renomeie os diretórios do projeto se esse for o caso.
5. Se nenhum dos comandos Ionide estiver funcionando, verifique suas [associações de teclas Visual Studio Code](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) para ver se você está substituindo-as por acidente.
6. Se o Ionide for interrompido em seu computador e nenhuma das opções acima tiver corrigido o problema, tente remover `ionide-fsharp` o diretório em seu computador e reinstalar o pacote de plug-in.

Ionide é um projeto de software livre criado e mantido por membros da F# comunidade. Informe os [problemas e fique à vontade para contribuir no Ionide-VSCode: Repositório](https://github.com/ionide/ionide-vscode-fsharp)do GitHub do FSharp.

Se você tiver um problema para relatar, siga [as instruções para obter os logs a serem usados ao relatar um problema](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).

Você também pode pedir ajuda para os desenvolvedores e F# a Comunidade do Ionide no [canal Ionide Gitter](https://gitter.im/ionide/ionide-project).

## <a name="next-steps"></a>Próximas etapas

Para saber mais sobre F# os recursos do idioma, confira o [Tour do F# ](../tour.md).
