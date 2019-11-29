---
title: Introdução ao F# no Visual Studio
description: Saiba como usar F# o com o Visual Studio.
ms.date: 07/03/2018
ms.openlocfilehash: 80b4fc5b7631eace719832fe32003cad578ead27
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552830"
---
# <a name="get-started-with-f-in-visual-studio"></a>Introdução ao F# no Visual Studio

F#e as ferramentas F# visuais têm suporte no IDE do Visual Studio.

Para começar, verifique se você tem o [Visual Studio instalado F#com ](install-fsharp.md#install-f-with-visual-studio)o.

## <a name="creating-a-console-application"></a>Criando um aplicativo de console

Um dos projetos mais básicos do Visual Studio é o aplicativo de console.  Veja como fazer isso.  Quando o Visual Studio estiver aberto:

1. No menu **arquivo** , aponte para **novo**e, em seguida, escolha **projeto**.

2. Na caixa de diálogo novo projeto, em **modelos**, você deve **Ver F#Visual** .  Escolha esta seleção para mostrar F# os modelos.

3. Selecione o aplicativo de **console do .NET Core** ou o **aplicativo de console**.

4. Escolha o botão **OK** para criar o F# projeto!  Agora você deve ver um F# projeto no Gerenciador de soluções.

## <a name="writing-your-code"></a>Escrevendo seu código

Vamos começar escrevendo um pouco de código primeiro.  Verifique se o arquivo de `Program.fs` está aberto e, em seguida, substitua seu conteúdo pelo seguinte:

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

No exemplo de código anterior, uma função `square` foi definida, o que recebe uma entrada chamada `x` e a multiplica por si só.  Como F# o usa a [inferência de tipos](../language-reference/type-inference.md), o tipo de `x` não precisa ser especificado.  O F# compilador compreende os tipos em que a multiplicação é válida e atribuirá um tipo a `x` com base em como `square` é chamado.  Se você passar o mouse sobre `square`, verá o seguinte:

```fsharp
val square: x:int -> int
```

Isso é o que é conhecido como assinatura do tipo da função.  Ele pode ser lido da seguinte maneira: "Square é uma função que recebe um inteiro chamado x e produz um inteiro".  Observe que o compilador define por hora o tipo do `square` como `int` – isso ocorre porque a multiplicação não é genérica em *todos os* tipos, mas sim em um conjunto fechado de tipos.  O compilador do F# escolheu `int` neste caso, mas ajustará a assinatura de tipo se você chamar `square` com um tipo de entrada diferente, como um `float`.

Outra função, `main`, é definida, que é decorada com o atributo `EntryPoint` para informar F# ao compilador que a execução do programa deve iniciar lá.  Ele segue a mesma convenção que outras [linguagens de programação em estilo C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), em que argumentos de linha de comando podem ser passados para essa função e um código inteiro é retornado (normalmente `0`).

É nessa função que chamamos a função `square` com um argumento de `12`.  Em F# seguida, o compilador atribui o tipo de `square` a ser `int -> int` (ou seja, uma função que usa um `int` e produz um `int`).  A chamada para `printfn` é uma função de impressão formatada que usa uma cadeia de caracteres de formato, semelhante a linguagens de programação em estilo C, parâmetros que correspondem àquelas especificadas na cadeia de caracteres de formato e, em seguida, imprime o resultado e uma nova linha.

## <a name="running-your-code"></a>Execução do código

Você pode executar o código e ver os resultados pressionando **Ctrl**+**F5**.  Isso executa o programa sem depuração e permite que você veja os resultados.  Como alternativa, você pode escolher o item de menu de nível superior de **depuração** no Visual Studio e escolher **Iniciar sem depuração**.

Agora você deve ver o seguinte impresso na janela do console que o Visual Studio abriu:

```console
12 squared is 144!
```

Parabéns!  Você criou seu primeiro F# projeto no Visual Studio, escreveu uma F# função imprimiu os resultados da chamada dessa função e executou o projeto para ver alguns resultados.

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

Se você ainda não fez isso, confira o [Tour do F# ](../tour.md), que abrange alguns dos principais recursos do F# idioma.  Ele fornecerá uma visão geral de alguns dos recursos do F#e fornecerá amplos exemplos de código que você pode copiar para o Visual Studio e executar.  Você também pode saber mais sobre a F# documentação na [ F# home page do docs](../index.yml).

## <a name="see-also"></a>Consulte também

- [Tour do F#](../tour.md)
- [F#referência de linguagem](../language-reference/index.md)
- [Inferência de tipos](../language-reference/type-inference.md)
- [Referência de símbolo e operador](../language-reference/symbol-and-operator-reference/index.md)
