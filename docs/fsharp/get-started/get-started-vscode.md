---
title: Introdução ao F# no Visual Studio Code
description: Saiba como usar F# o com Visual Studio Code e o pacote de plug-in Ionide.
ms.date: 12/23/2018
ms.openlocfilehash: 2802438144eb2352c3abeeccfc126b16c6a87d8f
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204906"
---
# <a name="get-started-with-f-in-visual-studio-code"></a>Introdução ao F# no Visual Studio Code

Você pode gravar F# em [Visual Studio Code](https://code.visualstudio.com) com o [plug-in Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) para obter uma experiência excelente de plataforma cruzada e leve em ambiente de desenvolvimento integrado com IntelliSense e refatoração de código. Visite [Ionide.Io](http://ionide.io) para saber mais sobre o plug-in.

Para começar, verifique se você tem [ F# o e o plug-in Ionide instalado corretamente](install-fsharp.md#install-f-with-visual-studio-code).

## <a name="create-your-first-project-with-ionide"></a>Criar seu primeiro projeto com o Ionide

Para criar um novo F# projeto, abra uma linha de comando e crie um novo projeto com o CLI do .NET Core:

```dotnetcli
dotnet new console -lang F# -o FirstIonideProject
```

Após a conclusão, altere o diretório para o projeto e abra Visual Studio Code:

```console
cd FirstIonideProject
code .
```

Depois que o projeto for carregado no Visual Studio Code, você deverá F# ver o painel de Gerenciador de soluções no lado esquerdo da janela aberta. Isso significa que o Ionide carregou com êxito o projeto que você acabou de criar. Você pode escrever código no editor antes desse ponto no tempo, mas assim que isso acontecer, tudo concluiu o carregamento.

## <a name="configure-f-interactive"></a>Configurar F# interativo

Primeiro, verifique se o script do .NET Core é o seu ambiente de script padrão:

1. Abra as configurações de Visual Studio Code (**código** > **preferências** > **configurações**).
1. Procure o termo  **F# script**.
1. Clique na caixa de seleção que diz **FSharp: usar scripts do SDK**.

Isso é necessário no momento devido a alguns comportamentos herdados em scripts baseados em .NET Framework que não funcionam com o script do .NET Core e o Ionide está se empenhando atualmente para a compatibilidade com versões anteriores. No futuro, o script do .NET Core se tornará o padrão.

### <a name="write-your-first-script"></a>Escreva seu primeiro script

Depois de configurar Visual Studio Code para usar o script do .NET Core, navegue até o modo de exibição do Explorer em Visual Studio Code e crie um novo arquivo. Nomeie-o como *MyFirstScript. fsx*.

Agora, adicione o seguinte código a ele:

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

Essa função converte uma palavra em uma forma de [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin). A próxima etapa é avaliá-lo F# usando o Interactive (FSI).

Realce a função inteira (deve ter 11 linhas). Depois de realçar, mantenha pressionada a tecla **ALT** e pressione **Enter**. Você notará uma janela de terminal exibida na parte inferior da tela e ela deverá ser semelhante a esta:

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
> Como você deve ter notado, as linhas no FSI são encerradas com `;;`. Isso ocorre porque o FSI permite que você insira várias linhas. O `;;` no final permite que o FSI saiba quando o código é concluído.

## <a name="explaining-the-code"></a>Explicando o código

Se você não tiver certeza sobre o que o código está realmente fazendo, aqui está um passo a passo.

Como você pode ver, `toPigLatin` é uma função que usa uma palavra como sua entrada e a converte em uma representação Pig-Latin dessa palavra. As regras para isso são as seguintes:

Se o primeiro caractere em uma palavra começar com uma vogal, adicione "Sim" ao final da palavra. Se não começar com uma vogal, mova o primeiro caractere para o final da palavra e adicione "o".

Você pode ter notado o seguinte no FSI:

```fsharp
val toPigLatin : word:string -> string
```

Isso declara que `toPigLatin` é uma função que usa uma `string` como entrada (chamada `word`) e retorna outra `string`. Isso é conhecido como a [assinatura de tipo da função](https://fsharpforfunandprofit.com/posts/function-signatures/), uma parte fundamental da F# chave para entender F# o código. Você também observará isso se passar o mouse sobre a função em Visual Studio Code.

No corpo da função, você observará duas partes distintas:

1. Uma função interna, chamada `isVowel`, que determina se um determinado caractere (`c`) é uma vogal verificando se ele corresponde a um dos padrões fornecidos por meio de [correspondência de padrões](../language-reference/pattern-matching.md):

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. Uma [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expressão que verifica se o primeiro caractere é uma vogal e constrói um valor de retorno dos caracteres de entrada com base em se o primeiro caractere era uma vogal ou não:

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

O fluxo de `toPigLatin` é assim:

Verifique se o primeiro caractere da palavra de entrada é uma vogal. Se for, anexe "Sim" ao final da palavra. Caso contrário, mova esse primeiro caractere para o final da palavra e adicione "

Há uma coisa final a ser observada sobre isso: não há nenhuma instrução explícita para retornar da função, ao contrário de muitas outras linguagens. Isso ocorre porque F# o é baseado em expressão e a última expressão no corpo de uma função é o valor de retorno. Como `if..then..else` é, em si, uma expressão, o corpo do bloco de `then` ou o corpo do bloco de `else` será retornado dependendo do valor de entrada.

## <a name="turn-the-console-app-into-a-pig-latin-generator"></a>Transforme o aplicativo de console em um gerador de Pig Latin

As seções anteriores neste artigo demonstraram uma primeira etapa comum na escrita F# de código: escrever uma função inicial e executá-la interativamente com o FSI. Isso é conhecido como desenvolvimento controlado por REPL, em que [repl](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) significa "Read-Evaluate-Print loop". É uma ótima maneira de experimentar a funcionalidade até que você tenha algo funcionando.

A próxima etapa no desenvolvimento controlado por REPL é mover o código funcional para um F# arquivo de implementação. Em seguida, ele pode ser compilado F# pelo compilador em um assembly que pode ser executado.

Para começar, abra o arquivo *Program. FS* criado anteriormente com o CLI do .NET Core. Você observará que algum código já está lá.

Em seguida, crie um novo [`module`](../language-reference/modules.md) chamado `PigLatin` e copie a função `toPigLatin` que você criou anteriormente como tal:

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

Esse módulo deve estar acima da função `main` e abaixo da declaração `open System`. A ordem das declarações é F#importante no, portanto, você precisará definir a função antes de chamá-la em um arquivo.

Agora, na função `main`, chame sua função de gerador Pig Latin nos argumentos:

```fsharp
[<EntryPoint>]
let main argv =
    for name in argv do
        let newName = PigLatin.toPigLatin name
        printfn "%s in Pig Latin is: %s" name newName

    0
```

Agora você pode executar o aplicativo de console na linha de comando:

```console
dotnet run apple banana
```

E você verá que ele gera o mesmo resultado que o arquivo de script, mas desta vez como um programa em execução!

## <a name="troubleshooting-ionide"></a>Solução de problemas do Ionide

Aqui estão algumas maneiras de solucionar alguns problemas que você pode encontrar:

1. Para obter os recursos de edição de código do Ionide F# , os arquivos precisam ser salvos em disco e dentro de uma pasta que está aberta no espaço de trabalho Visual Studio Code.
1. Se você fez alterações no seu sistema ou instalou os pré-requisitos do Ionide com Visual Studio Code abrir, reinicie o Visual Studio Code.
1. Se você tiver caracteres inválidos em seus diretórios de projeto, o Ionide poderá não funcionar.  Renomeie os diretórios do projeto se esse for o caso.
1. Se nenhum dos comandos Ionide estiver funcionando, verifique suas [associações de teclas Visual Studio Code](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) para ver se você está substituindo-as por acidente.
1. Se o Ionide for interrompido em seu computador e nenhuma das opções acima tiver corrigido o problema, tente remover o diretório `ionide-fsharp` em seu computador e reinstalar o pacote de plug-in.
1. Se um projeto não for carregado (o F# Gerenciador de soluções mostrará isso), clique com o botão direito do mouse no projeto e clique em **Ver detalhes** para obter mais informações de diagnóstico.

Ionide é um projeto de software livre criado e mantido por membros da F# comunidade. Informe os problemas e fique à vontade para contribuir no [repositório GitHub ionide-vscode-FSharp](https://github.com/ionide/ionide-vscode-fsharp).

Você também pode pedir ajuda para os desenvolvedores e F# a Comunidade do Ionide no [canal Ionide Gitter](https://gitter.im/ionide/ionide-project).

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

Para saber mais sobre F# os recursos do idioma, confira o [Tour do F# ](../tour.md).
