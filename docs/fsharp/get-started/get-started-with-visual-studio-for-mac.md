---
title: Introdução ao F# no Visual Studio para Mac
description: Saiba como usar F# o com Visual Studio para Mac.
ms.date: 07/03/2018
ms.openlocfilehash: cd45ab9c59cef76e4bf85a93f39d8e2ee063d200
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552363"
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a>Introdução ao F# no Visual Studio para Mac

F#e as ferramentas F# visuais têm suporte no IDE Visual Studio para Mac. Verifique se você tem [Visual Studio para Mac instalado](install-fsharp.md#install-f-with-visual-studio-for-mac).

## <a name="creating-a-console-application"></a>Criando um aplicativo de console

Um dos projetos mais básicos no Visual Studio para Mac é o aplicativo de console.  Veja como fazer isso.  Quando Visual Studio para Mac estiver aberto:

1. No menu **arquivo** , aponte para **nova solução**.

2. Na caixa de diálogo novo projeto, há dois modelos diferentes para o aplicativo de console.  Há um em outro-> .NET que tem como alvo o .NET Framework.  O outro modelo está em .NET Core – > aplicativo que tem como alvo o .NET Core.  O modelo deve funcionar para a finalidade deste artigo.

3. Em aplicativo de console, C# Altere F# para se necessário.  Escolha o botão **Avançar** para prosseguir!  

4. Dê um nome ao projeto e escolha as opções desejadas para o aplicativo.  Observe, no painel de visualização, o lado da tela que mostrará a estrutura de diretório que será criada com base nas opções selecionadas.  

5. Clique em **Criar**.  Agora você deve ver um F# projeto no Gerenciador de soluções.

## <a name="writing-your-code"></a>Escrevendo seu código

Vamos começar escrevendo um pouco de código primeiro.  Verifique se o arquivo de `Program.fs` está aberto e, em seguida, substitua seu conteúdo pelo seguinte:

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

No exemplo de código anterior, uma função `square` foi definida, o que recebe uma entrada chamada `x` e a multiplica por si só.  Como F# o usa a [inferência de tipos](../language-reference/type-inference.md), o tipo de `x` não precisa ser especificado.  O F# compilador compreende os tipos em que a multiplicação é válida e atribuirá um tipo a `x` com base em como `square` é chamado.  Se você passar o mouse sobre `square`, verá o seguinte:

```console
val square: x:int -> int
```

Isso é o que é conhecido como assinatura do tipo da função.  Ele pode ser lido da seguinte maneira: "Square é uma função que recebe um inteiro chamado x e produz um inteiro".  Observe que o compilador define por hora o tipo do `square` como `int` – isso ocorre porque a multiplicação não é genérica em *todos os* tipos, mas sim em um conjunto fechado de tipos.  O compilador do F# escolheu `int` neste caso, mas ajustará a assinatura de tipo se você chamar `square` com um tipo de entrada diferente, como um `float`.

Outra função, `main`, é definida, que é decorada com o atributo `EntryPoint` para informar F# ao compilador que a execução do programa deve iniciar lá.  Ele segue a mesma convenção que outras [linguagens de programação em estilo C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), em que argumentos de linha de comando podem ser passados para essa função e um código inteiro é retornado (normalmente `0`).

É nessa função que chamamos a função `square` com um argumento de `12`.  Em F# seguida, o compilador atribui o tipo de `square` a ser `int -> int` (ou seja, uma função que usa um `int` e produz um `int`).  A chamada para `printfn` é uma função de impressão formatada que usa uma cadeia de caracteres de formato, semelhante a linguagens de programação em estilo C, parâmetros que correspondem àquelas especificadas na cadeia de caracteres de formato e, em seguida, imprime o resultado e uma nova linha.

## <a name="running-your-code"></a>Execução do código

Você pode executar o código e ver os resultados clicando em **executar** no menu de nível superior e, em seguida, **Iniciar sem depuração**.  Isso executará o programa sem depuração e permitirá que você veja os resultados.

Agora você deve ver o seguinte impresso na janela do console que Visual Studio para Mac exibida:

```console
12 squared is 144!
```

Parabéns!  Você criou seu primeiro F# projeto no Visual Studio para Mac, escreveu uma F# função imprimiu os resultados da chamada dessa função e executou o projeto para ver alguns resultados.

## <a name="using-f-interactive"></a>Usando F# interativo

Um dos melhores recursos das ferramentas visuais F# no Visual Studio para Mac é a F# janela interativa.  Ele permite que você envie código para um processo no qual você pode chamar esse código e ver o resultado interativamente.

Para começar a usá-lo, realce a função `square` definida em seu código.  Em seguida, clique em **Editar** no menu de nível superior.  Em seguida, selecione **Enviar F# seleção para interativo**.  Isso executa o código na janela F# interativa.  Como alternativa, você pode clicar com o botão direito do mouse na seleção e escolher **Enviar seleção para F# interativo**.  Você deve ver a F# janela interativa aparecer com o seguinte:

```console
>

val square : x:int -> int

>
```

Isso mostra a mesma assinatura de função para a função `square`, que você viu anteriormente ao passar o mouse sobre a função.  Como `square` agora é definido no processo F# interativo, você pode chamá-lo com valores diferentes:

```console
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

Isso executa a função, associa o resultado a um novo nome `it`e exibe o tipo e o valor de `it`.  Observe que você deve encerrar cada linha com `;;`.  É assim F# que se sabe quando sua chamada de função está pronta.  Você também pode definir novas funções em F# interativo:

```console
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

O acima define uma nova função, `isOdd`, que usa um `int` e verifica se ele é estranho!  Você pode chamar essa função para ver o que ela retorna com entradas diferentes.  Você pode chamar funções em chamadas de função:

```console
> isOdd (square 15);;
val it : bool = true
```

Você também pode usar o [operador de encaminhamento de pipe](../language-reference/symbol-and-operator-reference/index.md) para canalizar o valor nas duas funções:

```console
> 15 |> square |> isOdd;;
val it : bool = true
```

O operador de encaminhamento de pipe e muito mais, são abordados em Tutoriais posteriores.

Isso é apenas uma visão do que você pode fazer com F# o Interactive.  Para saber mais, confira [programação interativa com F# ](../tutorials/fsharp-interactive/index.md).

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

Se você ainda não fez isso, confira o [Tour do F# ](../tour.md), que abrange alguns dos principais recursos do F# idioma.  Ele fornecerá uma visão geral de alguns dos recursos do F#e fornecerá amplos exemplos de código que você pode copiar para Visual Studio para Mac e executar.  Também há alguns ótimos recursos externos que você pode usar, demonstrados no [ F# guia](../index.yml).

## <a name="see-also"></a>Consulte também

- [F#orienta](../index.yml)
- [Tour do F#](../tour.md)
- [F#referência de linguagem](../language-reference/index.md)
- [Inferência de tipos](../language-reference/type-inference.md)
- [Referência de símbolo e operador](../language-reference/symbol-and-operator-reference/index.md)
