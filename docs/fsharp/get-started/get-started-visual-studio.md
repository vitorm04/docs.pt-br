---
title: Introdução ao F# no Visual Studio
description: Saiba como usar F# o com o Visual Studio.
ms.date: 12/20/2019
ms.openlocfilehash: 9bf47fb08ea3df0aa0d5064043d94f030d45d568
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337345"
---
# <a name="get-started-with-f-in-visual-studio"></a>Introdução ao F# no Visual Studio

F#e as ferramentas F# visuais têm suporte no IDE (ambiente de desenvolvimento integrado) do Visual Studio.

Para começar, verifique se você tem o [Visual Studio instalado F# com suporte](install-fsharp.md#install-f-with-visual-studio).

## <a name="create-a-console-application"></a>Criar um aplicativo de console

Um dos projetos mais básicos do Visual Studio é o aplicativo de console. Veja como criar um:

1. Abra o Visual Studio 2019.

2. Na tela Iniciar, selecione **Criar um novo projeto**.

3. Na página **criar um novo projeto** , escolha **F#** na lista idioma.

4. Escolha o modelo **aplicativo de console (.NET Core)** e, em seguida, escolha **Avançar**.

5. Na página **configurar seu novo projeto** , insira um nome na caixa **nome do projeto** . Em seguida, escolha **Criar**.

   O Visual Studio cria o F# novo projeto. Você pode vê-lo na janela de Gerenciador de Soluções.

## <a name="write-the-code"></a>Escreva o código

Vamos começar escrevendo um pouco de código. Verifique se o arquivo `Program.fs` está aberto e, em seguida, substitua seu conteúdo pelo seguinte:

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

O exemplo de código anterior define uma função chamada `square` que usa uma entrada chamada `x` e a multiplica por si só. Como F# o usa a [inferência de tipos](../language-reference/type-inference.md), o tipo de `x` não precisa ser especificado. O F# compilador compreende os tipos em que a multiplicação é válida e atribui um tipo a `x` com base em como `square` é chamado. Se você passar o mouse por cima de `square`, verá o seguinte:

```fsharp
val square: x:int -> int
```

Isso é o que é conhecido como assinatura do tipo da função. Ele pode ser lido da seguinte maneira: "Square é uma função que usa um inteiro chamado x e produz um inteiro". O compilador ofereceu `square` o tipo de `int` por enquanto; Isso ocorre porque a multiplicação não é genérica em *todos os* tipos, mas sim um conjunto fechado de tipos. O F# compilador ajustará a assinatura de tipo se você chamar `square` com um tipo de entrada diferente, como um `float`.

Outra função, `main`, é definida, que é decorada com o atributo `EntryPoint`. Esse atributo informa ao F# compilador que a execução do programa deve iniciar lá. Ele segue a mesma convenção que outras [linguagens de programação em estilo C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), em que argumentos de linha de comando podem ser passados para essa função e um código inteiro é retornado (normalmente `0`).

Ele está na função de ponto de entrada, `main`, que você chama a função `square` com um argumento de `12`. Em F# seguida, o compilador atribui o tipo de `square` a ser `int -> int` (ou seja, uma função que usa um `int` e produz um `int`). A chamada para `printfn` é uma função de impressão formatada que usa uma cadeia de caracteres de formato e imprime o resultado (e uma nova linha). A cadeia de caracteres de formato, semelhante às linguagens de programação em estilo C, tem parâmetros (`%d`) que correspondem aos argumentos que são passados para ele, nesse caso, `12` e `(square 12)`.

## <a name="run-the-code"></a>Executar o código

Você pode executar o código e ver os resultados pressionando **Ctrl**+**F5**. Como alternativa, você pode escolher a > de **depuração** **Iniciar sem depuração** na barra de menus de nível superior. Isso executa o programa sem depuração.

A saída a seguir é impressa na janela do console aberta pelo Visual Studio:

```console
12 squared is: 144!
```

Parabéns! Você criou seu primeiro F# projeto no Visual Studio, escreveu uma F# função que calcula e imprime um valor e executa o projeto para ver os resultados.

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

Se você ainda não fez isso, confira o [Tour do F# ](../tour.md), que abrange alguns dos principais recursos da linguagem F#. Ele fornece uma visão geral de alguns dos recursos do F# e exemplos de código abrangentes que você pode copiar para o Visual Studio e executar.

> [!div class="nextstepaction"]
> [Tour do F#](../tour.md)

## <a name="see-also"></a>Veja também

- [F#referência de linguagem](../language-reference/index.md)
- [Inferência de tipos](../language-reference/type-inference.md)
- [Referência de símbolo e operador](../language-reference/symbol-and-operator-reference/index.md)
