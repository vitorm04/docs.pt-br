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

A IDE do Visual Studio tem suporte ao F# e as ferramentas visuais do F#.

Para começar, verifique se você tem o [Visual Studio instalado F#com ](install-fsharp.md#install-f-with-visual-studio).

## <a name="creating-a-console-application"></a>Criando um aplicativo console

Um dos projetos mais básicos do Visual Studio é um aplicativo console.  Veja como fazer isso.  Depois de abrir o Visual Studio:

1. No menu **arquivo** , selecione a opção **novo**, em seguida escolha **projeto**.

2. Na caixa de diálogo de novo projeto, em **modelos**, você deve ver **Visual F#** .  Escolha esta seleção para mostrar os modelos para F#.

3. Selecione o aplicativo de **.NET Core Console** ou o **Console Aplicativo**.

4. Escolha o botão **OK** para criar o projeto F#! Agora você deve ver um projeto F# no Gerenciador de soluções.

## <a name="writing-your-code"></a>Escrevendo seu código

Vamos começar escrevendo um pouco de código.  Verifique se o `Program.fs` arquivo está aberto, substitua seu conteúdo pelo seguinte:

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

No exemplo de código anterior, foi definido `square` uma função que recebe uma entrada chamada `x` e a multiplica por ela mesma.  Como o F# usa [inferência de tipos](../language-reference/type-inference.md), o tipo de  `x` não precisa ser especificado.  O compilador do F#  compreende os tipos em que uma multiplicação é válida e atribuirá esse tipo para `x` com base no corpo da função `square`.  Se você passar o mouse por cima do `square`, verá o seguinte:

```fsharp
val square: x:int -> int
```

Isso é conhecido como assinatura do tipo da função.  Ela pode ser lida da seguinte maneira: "Square é uma função que recebe um inteiro chamado x e retorna um inteiro".  Observe que o compilador define por hora o tipo do `square` como  `int`  - isso ocorre porque a multiplicação não é genérica em *todos os* tipos, mas sim em um conjunto fechado de tipos.  O compilador do F# escolheu `int` neste casp, mas ajustará a assinatura de tipo se você chamar `square` com um tipo de entrada diferente, como um `float`.

Outra função, `main`, é definida, que é decorada com `EntryPoint` o atributo para informar ao compilador do F# que a execução do programa deve iniciar lá.  Ele segue a mesma convenção que outras [linguagens de programação em estilo C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), em que argumentos de linha de comando podem ser passados para essa função e um código inteiro é  retornado. (normalmente `0`).

É nessa função que chamamos a função `square` com o argumento `12`.  Em seguida, o compilador do F# atribui o tipo de `square` a `int -> int` (ou seja, uma função que recebe um `int` e retorna um `int`).  A chamada para `printfn` é uma função de impressão formatada que usa uma cadeia de caracteres formatavel, semelhante a linguagens de programação em estilo C, recebe parâmetros que correspondem àquelas especificadas na cadeia de caracteres, em seguida, imprime o resultado e uma nova linha.

## <a name="running-your-code"></a>Execução do código

Você pode executar o código e ver os resultados pressionando **Ctrl**+**F5**.  Isso executa o programa sem depuração e permite que você veja os resultados.  Como alternativa, você pode escolher o item de menu de nível superior de **depuração** no Visual Studio e escolher **Iniciar sem depuração**.

Agora você deve ver o seguinte texto impresso na janela do console que o Visual Studio abriu:

```console
12 squared is 144!
```

Parabéns!  Você criou seu primeiro projeto F# no Visual Studio, escreveu uma função F# que imprimiu os resultados da chamada dessa função e executou o projeto para ver os resultados.

## <a name="next-steps"></a>Próximas etapas

Se você ainda não fez isso, confira o [Tour do F# ](../tour.md), que abrange alguns dos principais recursos do F#.  Ele fornecerá uma visão geral de alguns dos recursos do F# e fornecerá amplos exemplos de código que você pode copiar para o Visual Studio e executar.  Também há alguns ótimos recursos externos que você pode usar, demonstrados no [ F# guia](../index.md).

## <a name="see-also"></a>Consulte também

- [Tour do F#](../tour.md)
- [F#referência de linguagem](../language-reference/index.md)
- [Inferência de tipos](../language-reference/type-inference.md)
- [Referência de símbolo e operador](../language-reference/symbol-and-operator-reference/index.md)
