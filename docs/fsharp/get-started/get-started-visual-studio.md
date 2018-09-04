---
title: 'Introdução ao F # no Visual Studio'
description: 'Saiba como usar o F # com o Visual Studio.'
ms.date: 07/03/2018
ms.openlocfilehash: 3dac8466501338873aeb308ceac9274a7934a8a9
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43563840"
---
# <a name="get-started-with-f-in-visual-studio"></a>Introdução ao F # no Visual Studio

Há suporte no F # e as ferramentas do Visual F # no IDE do Visual Studio.

Para começar, certifique-se de que você tenha [Visual Studio instalado com o F #](install-fsharp.md#install-f-with-visual-studio).

## <a name="creating-a-console-application"></a>Criando um aplicativo de console

Um dos projetos mais básicos no Visual Studio é o aplicativo de Console.  Veja como fazer isso.  Após abrir o Visual Studio:

1. Sobre o **arquivo** , aponte para **New**e, em seguida, escolha **projeto**.

2.  Na nova caixa de diálogo projeto, sob **modelos**, você deverá ver **Visual F #**.  Escolha esta opção para mostrar os modelos do F #.

3. Selecione a **aplicativo de Console do .NET Core** ou **aplicativo de Console**.

3. Escolha o **Okey** botão para criar o projeto do F #!  Agora você verá um projeto F # no Gerenciador de soluções.

## <a name="writing-your-code"></a>Escrever seu código

Vamos começar escrevendo um código pela primeira vez.  Certifique-se de que o `Program.fs` arquivo está aberto e, em seguida, substitua seu conteúdo pelo seguinte:

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

No exemplo de código anterior, uma função `square` tenha sido definido, que usa uma entrada denominada `x` e multiplica por si só.  Como o F # usa [inferência](../language-reference/type-inference.md), o tipo de `x` não precisa ser especificado.  O compilador F # compreende os tipos em que a multiplicação é válida e atribuirá um tipo para `x` com base em como `square` é chamado.  Se você focalizar `square`, você deve ver o seguinte:

```
val square: x:int -> int
```

Esse é o que é conhecido como assinatura de tipo da função.  Ele pode ser lido como esta: "quadrado é uma função que usa um número inteiro denominado x e produz um número inteiro".  Observe que o compilador forneceu `square` as `int` tipo por ora - isso é porque a multiplicação não é genérica entre *todos os* tipos, mas em vez disso, é genérico em um conjunto fechado de tipos.  O compilador F # escolhido `int` neste ponto, mas ele se ajustará a assinatura de tipo se você chamar `square` com outro tipo de entrada, como um `float`.

Outra função, `main`, é definido, que é decorado com o `EntryPoint` atributo para indicar ao compilador F # que a execução do programa deve iniciar lá.  Ele segue a mesma convenção que outro [linguagens de programação C-style](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), em que os argumentos de linha de comando podem ser passados para essa função, e um código inteiro será retornado (normalmente `0`).

É nessa função que podemos chamar o `square` função com um argumento de `12`.  O compilador F #, em seguida, atribui o tipo de `square` ser `int -> int` (ou seja, uma função que usa um `int` e produz um `int`).  A chamada para `printfn` é uma função de impressão formatada que usa uma cadeia de formato, semelhante a linguagens de programação C-style, parâmetros que correspondem aos especificados na cadeia de caracteres de formato e, em seguida, imprime o resultado e uma nova linha.

## <a name="running-your-code"></a>Execução do código

Você pode executar o código e ver resultados pressionando **Ctrl**+**F5**.  Isso executa o programa sem depuração e permite que você veja os resultados.  Como alternativa, você pode escolher o **Debug** menu de nível superior do item no Visual Studio e escolha **Start Without Debugging**.

Agora, você verá o seguinte mostrado na janela de console que surge do Visual Studio:

```
12 squared is 144!
```

Parabéns!  Criou seu primeiro projeto F # no Visual Studio, escrito que uma função F # impresso os resultados da chamada de função e execute o projeto para ver alguns resultados.

## <a name="next-steps"></a>Próximas etapas

Se você ainda não fez isso, confira a [Tour do F #](../tour.md), que aborda alguns dos principais recursos da linguagem F #.  Ele lhe dá uma visão geral de alguns dos recursos da linguagem F # e fornecem exemplos de código amplo que você pode copiar para o Visual Studio e executar.  Também existem alguns ótimos recursos externos, você pode usar, foi apresentada na [guia de F #](../index.md).

## <a name="see-also"></a>Consulte também

- [Tour do F#](../tour.md)
- [Referência da linguagem F #](../language-reference/index.md)
- [Inferência de tipo](../language-reference/type-inference.md)
- [Referência de símbolo e o operador](../language-reference/symbol-and-operator-reference/index.md)
