---
title: 'Introdução à linguagem F # no Visual Studio'
description: 'Saiba como usar o F # com o Visual Studio.'
author: cartermp
ms.author: phcart
ms.date: 02/13/2017
ms.topic: conceptual
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 29e24f755e6d97c4b31c0d01b254bf90cf77bf17
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="get-started-with-f-in-visual-studio"></a>Introdução à linguagem F # no Visual Studio

F # e as ferramentas do Visual F # têm suporte no Visual Studio IDE.  Para começar, você deve [baixar o Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs), se ainda não o fez.  Este artigo usa o Visual Studio 2017 Community Edition, mas você pode usar F # com a versão de sua escolha.

## <a name="installing-f"></a>Instalando a F # #

Se você estiver baixando o Visual Studio pela primeira vez, ele será instalado primeiro o instalador do Visual Studio.  Instale qualquer versão do Visual Studio de 2017 do instalador. Se você já tiver instalado, clique em **modificar**.

Em seguida, você verá uma lista de cargas de trabalho. Você pode instalar o F # por meio de qualquer uma das seguintes cargas de trabalho:

|Carga de trabalho|Ação|
|--------|------|
| Desenvolvimento de plataforma cruzada do .NET Core | Nenhuma ação - F # é instalada por padrão |
| Desenvolvimento do ASP.NET e para a Web | Nenhuma ação - F # é instalada por padrão |
| Desenvolvimento do Azure | Nenhuma ação - F # é instalada por padrão |
| Desenvolvimento móvel com o .NET | Nenhuma ação - F # é instalada por padrão |
| Ciência de dados e aplicativos analíticos | Nenhuma ação - F # é instalada por padrão |
| Desenvolvimento de área de trabalho do .NET | Selecione **suporte de idioma da área de trabalho do F #** do lado direito |
| Armazenamento de dados e processamento | Selecione **suporte de idioma da área de trabalho do F #** do lado direito |

Em seguida, clique em **modificar** na parte inferior direita.  Isso irá instalar tudo o que você selecionou.  Você pode em seguida, abra 2017 do Visual Studio com o suporte da linguagem F # **iniciar**.

## <a name="creating-a-console-application"></a>Criando um aplicativo de console

Um dos projetos mais básicos no Visual Studio é o aplicativo de Console.  Veja como fazer isso.  Depois de abrir o Visual Studio:

1. Sobre o **arquivo** , aponte para **novo**e, em seguida, escolha **projeto**.

2.  No novo projeto caixa de diálogo, em **modelos**, você deve ver **Visual F #**.  Escolha esta opção para mostrar os modelos de F #.

3. Selecione **.NET Core aplicativo de Console** ou **aplicativo de Console**.

3. Escolha o **Okey** botão para criar o projeto F #!  Agora você deve ver um projeto F # no Gerenciador de soluções.

## <a name="writing-your-code"></a>Escrever seu código

Vamos começar escrevendo um código primeiro.  Verifique se o `Program.fs` arquivo está aberto e, em seguida, substitua o seu conteúdo com o seguinte:

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

No exemplo de código anterior, uma função `square` foi definido que usa uma entrada denominada `x` e multiplica por si só.  Como F # usa [inferência de tipo](../language-reference/type-inference.md), o tipo de `x` não precisa ser especificado.  O compilador F # compreende os tipos de onde a multiplicação é válida e atribuirá um tipo para `x` com base em como `square` é chamado.  Se você focalizar `square`, você deve ver o seguinte:

```
val square: x:int -> int
```

Isso é conhecido como assinatura de tipo da função.  Ele pode ser lido como esta: "quadrada é uma função que usa um número inteiro denominado x e produz um número inteiro".  Observe que o compilador deu `square` o `int` tipo agora - isso é porque a multiplicação não é genérica em *todos os* tipos, mas em vez disso é genérico em um conjunto fechado de tipos.  O compilador F # escolhido `int` neste ponto, mas ele ajustará a assinatura de tipo se você chamar `square` com outro tipo de entrada, como um `float`.

Outra função, `main`, é definido, que é decorado com o `EntryPoint` atributo para informar ao compilador F # que a execução do programa deve iniciar de lá.  Ele segue a mesma convenção de outros [linguagens de programação C-style](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), onde argumentos de linha de comando podem ser transmitidos para a função e um código inteiro será retornado (geralmente `0`).

É nessa função que chamamos de `square` função com um argumento de `12`.  O compilador F #, em seguida, atribui o tipo de `square` ser `int -> int` (ou seja, uma função que leva um `int` e produz um `int`).  A chamada para `printfn` é uma função de impressão formatada que usa uma cadeia de formato, semelhante a linguagens de programação C-style, os parâmetros que correspondem aos especificados na cadeia de formato e imprime os resultados e uma nova linha.

## <a name="running-your-code"></a>Execução do código

Você pode executar o código e ver os resultados pressionando **ctrl-f5**.  Isso executará o programa sem depuração e permite que você veja os resultados.  Como alternativa, você pode escolher o **depurar** menus de nível superior do item no Visual Studio e escolha **Start Without Debugging**.

Agora, você verá o seguinte mostrado na janela de console que surge do Visual Studio:

```
12 squared is 144!
```

Parabéns!  Criou seu primeiro projeto F # no Visual Studio, escrito que uma função de F # impressos os resultados da chamada de função e execute o projeto para ver alguns resultados.

## <a name="using-f-interactive"></a>Usando F # interativo

Um dos melhores recursos do Visual F # ferramentas no Visual Studio é a janela interativa F #.  Ele permite que você envie código sobre a um processo em que você pode chamar esse código e ver o resultado de forma interativa.

Para começar a usá-lo, realce o `square` função definida no seu código.  Em seguida, mantenha o **Alt** chave e pressione **Enter**.  Isso executa o código na janela interativa F #.  Você deverá ver a janela interativa F # com o seguinte:

```
>

val square : x:int -> int

>
```

Isso mostra a mesma assinatura de função para o `square` função, que você viu anteriormente quando colocado na função.  Porque `square` está agora definido no processo de F # interativo, você pode chamá-lo com valores diferentes:

```
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

Isso executa a função e associa o resultado para um novo nome `it`e exibe o tipo e o valor de `it`.  Observe que você deve encerrar a cada linha com `;;`.  Isso é como F # interativo sabe quando a chamada de função for concluída.  Você também pode definir novas funções em F # interativo:

```
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

As opções acima define uma nova função, `isOdd`, que usa um `int` e verifica se ele for ímpar! Você pode chamar essa função para ver o que retorna com entradas diferentes.  Você pode chamar funções em chamadas de função:

```
> isOdd (square 15);;
val it : bool = true
```

Você também pode usar o [operador pipe avanço](../language-reference/symbol-and-operator-reference/index.md) para o valor de pipeline para as duas funções:

```
> 15 |> square |> isOdd;;
val it : bool = true
```

O operador de avanço de pipe e muito mais, são abordados em tutoriais subsequentes.

Isso é apenas uma visão rápida sobre o que você pode fazer com F # interativo. Para saber mais, confira [de programação com F # interativo](../tutorials/fsharp-interactive/index.md).

## <a name="next-steps"></a>Próximas etapas

Se você ainda não fez isso, confira o [Tour do F #](../tour.md), que aborda alguns dos principais recursos da linguagem F #.  Ele fornece uma visão geral de alguns dos recursos do F # e fornece exemplos de código bastante que você pode copiar para o Visual Studio e executar.  Também há alguns ótimos recursos externos, você pode usar, foi apresentada no [guia F #](../index.md).

## <a name="see-also"></a>Consulte também
 [Visual F#](index.md)  
 [Tour do F#](../tour.md)  
 [Referência da linguagem F #](../language-reference/index.md)  
 [Inferência de tipo](../language-reference/type-inference.md)  
 [Símbolo e o operador de referência](../language-reference/symbol-and-operator-reference/index.md)  
