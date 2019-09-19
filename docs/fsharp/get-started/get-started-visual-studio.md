---
title: Introdução ao F# no Visual Studio
description: Saiba como usar F# o com o Visual Studio.
ms.date: 07/03/2018
ms.openlocfilehash: e573af67a1fc00b0a340f8c73ab1ee0ed2b97810
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082694"
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

Vamos começar escrevendo um pouco de código primeiro.  Verifique se o `Program.fs` arquivo está aberto e, em seguida, substitua seu conteúdo pelo seguinte:

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

No exemplo de código anterior, foi definida `square` uma função que recebe uma entrada chamada `x` e a multiplica por si só.  Como o F# usa a [inferência de tipos](../language-reference/type-inference.md), o tipo de  `x` não precisa ser especificado.  O F# compilador compreende os tipos em que a multiplicação é válida e atribuirá um tipo `x` a com base `square` em como é chamado.  Se você passar o `square`mouse, verá o seguinte:

```fsharp
val square: x:int -> int
```

Isso é o que é conhecido como assinatura de tipo da função.  Ele pode ser lido da seguinte maneira: "Square é uma função que usa um inteiro chamado x e produz um inteiro".  Observe que o compilador `square` fornecia `int` o tipo por enquanto-isso ocorre porque a multiplicação não é genérica em *todos os* tipos, mas sim em um conjunto fechado de tipos.  O F# compilador escolheu `int` neste ponto, mas ajustará a assinatura de tipo se você chamar `square` com um tipo de entrada diferente, como um `float`.

Outra função, `main`, é definida, que é decorada com `EntryPoint` o atributo para informar F# ao compilador que a execução do programa deve iniciar lá.  Ele segue a mesma convenção que outras [linguagens de programação em estilo C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), em que argumentos de linha de comando podem ser passados para essa função e um código inteiro é `0`retornado (normalmente).

É nessa função que chamamos a `square` função com um argumento de. `12`  Em F# seguida, o compilador atribui o tipo de `square` a `int -> int` (ou seja, uma função que usa um `int` e produz um `int`).  A chamada para `printfn` é uma função de impressão formatada que usa uma cadeia de caracteres de formato, semelhante a linguagens de programação em estilo C, parâmetros que correspondem àquelas especificadas na cadeia de caracteres de formato e, em seguida, imprime o resultado e uma nova linha.

## <a name="running-your-code"></a>Execução do código

Você pode executar o código e ver os resultados pressionando **Ctrl**+**F5**.  Isso executa o programa sem depuração e permite que você veja os resultados.  Como alternativa, você pode escolher o item de menu de nível superior de **depuração** no Visual Studio e escolher **Iniciar sem depuração**.

Agora você deve ver o seguinte impresso na janela do console que o Visual Studio abriu:

```console
12 squared is 144!
```

Parabéns!  Você criou seu primeiro F# projeto no Visual Studio, escreveu uma F# função imprimiu os resultados da chamada dessa função e executou o projeto para ver alguns resultados.

## <a name="next-steps"></a>Próximas etapas

Se você ainda não fez isso, confira o [Tour do F# ](../tour.md), que abrange alguns dos principais recursos do F# idioma.  Ele fornecerá uma visão geral de alguns dos recursos do F#e fornecerá amplos exemplos de código que você pode copiar para o Visual Studio e executar.  Também há alguns ótimos recursos externos que você pode usar, demonstrados no [ F# guia](../index.md).

## <a name="see-also"></a>Consulte também

- [Tour do F#](../tour.md)
- [F#referência de linguagem](../language-reference/index.md)
- [Inferência de tipos](../language-reference/type-inference.md)
- [Referência de símbolo e operador](../language-reference/symbol-and-operator-reference/index.md)
