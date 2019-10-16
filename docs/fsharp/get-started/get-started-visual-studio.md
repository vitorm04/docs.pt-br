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

O IDE do Visual Studio tem suporte ao F# e às ferramentas do Visual F#.

Para começar, verifique se você tem o Visual Studio instalado com F#.

## <a name="creating-a-console-application"></a>Criando um aplicativo de console

Um dos projetos mais básicos do Visual Studio é o aplicativo de console. Veja como fazer isso. Quando o Visual Studio estiver aberto:

1. No menu **arquivo** , selecione a opção **novo** e, em seguida, escolha **projeto**.

2. Na caixa de diálogo Novo projeto, em **modelos**, você deve ver **Visual F#**. Escolha esta seleção para mostrar os modelos para F#.

3. Selecione o aplicativo de **console do .NET Core** ou o **aplicativo de console**.


4. Escolha o botão **OK** para criar o projeto de F#! Agora você deve ver um projeto de F# no Gerenciador de soluções.

## <a name="writing-your-code"></a>Escrevendo seu código

Vamos começar escrevendo um pouco de código. Verifique se o arquivo `Program.fs` está aberto e, em seguida, substitua seu conteúdo pelo seguinte:

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

No exemplo de código anterior, foi definida uma função `square` que recebe uma entrada chamada `x` e a multiplica por si só. Como o F# usa a [inferência de tipos](../language-reference/type-inference.md), o tipo de `x` não precisa ser especificado. O compilador do F# compreende os tipos em que uma multiplicação é válida e atribuirá um tipo para `x` com base em como `square` é chamada. Se você passar o mouse por cima de `square`, verá o seguinte:


```fsharp
val square: x:int -> int
```


Isso é conhecido como assinatura do tipo da função. Ela pode ser lida da seguinte maneira: "Square é uma função que recebe um inteiro chamado x e produz um inteiro". Observe que o compilador define por hora o tipo do `square` como `int` – isso ocorre porque a multiplicação não é genérica em *todos os* tipos, mas sim em um conjunto fechado de tipos. O compilador do F# escolheu `int` neste caso, mas ajustará a assinatura de tipo se você chamar `square` com um tipo de entrada diferente, como um `float`.

Outra função, `main`, é definida e decorada com o atributo `EntryPoint` para informar ao compilador do F# que a execução do programa deve iniciar lá. Ele segue a mesma convenção que outras [linguagens de programação em estilo C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), em que argumentos de linha de comando podem ser passados para essa função e um código inteiro é retornado (normalmente `0`).


É nessa função que chamamos a função `square` com o argumento `12`. Em seguida, o compilador do F# atribui o tipo de `square` a `int -> int` (ou seja, uma função que recebe um `int` e produz um `int`). A chamada para `printfn` é uma função de impressão formatada que usa uma cadeia de formato, semelhante a linguagens de programação em estilo C, parâmetros que correspondem àqueles especificados na cadeia de formato e, em seguida, imprime o resultado e uma nova linha.

## <a name="running-your-code"></a>Execução do código

Você pode executar o código e ver os resultados pressionando **Ctrl**+**F5**.  Isso executa o programa sem depuração e permite que você veja os resultados.  Como alternativa, você pode escolher o item de menu de nível superior de **depuração** no Visual Studio e escolher **Iniciar sem depuração**.

Agora você deve ver o seguinte texto impresso na janela do console que o Visual Studio abriu:

```console
12 squared is 144!
```


Parabéns! Você criou seu primeiro projeto de F# no Visual Studio, escreveu uma função de F#, imprimiu os resultados da chamada dessa função e executou o projeto para ver os resultados.

## <a name="next-steps"></a>Próximas etapas

Se você ainda não fez isso, confira o [Tour do F# ](../tour.md), que abrange alguns dos principais recursos da linguagem F#. Ele fornecerá uma visão geral de alguns dos recursos do F# e amplos exemplos de código que você pode copiar para o Visual Studio e executar. Também há alguns ótimos recursos externos que você pode usar, demonstrados no [ guia do F#](../index.md).


## <a name="see-also"></a>Consulte também

- [Tour do F#](../tour.md)
- [F#referência de linguagem](../language-reference/index.md)
- [Inferência de tipos](../language-reference/type-inference.md)
- [Referência de símbolo e operador](../language-reference/symbol-and-operator-reference/index.md)
