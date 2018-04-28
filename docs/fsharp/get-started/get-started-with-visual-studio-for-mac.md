---
title: 'Introdução ao F # no Visual Studio para Mac'
description: 'Saiba como usar F # com o Visual Studio para Mac.'
author: cartermp
ms.author: phcart
ms.date: 02/13/2017
ms.topic: conceptual
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 232235952ec43f682dc21de4ef7dde9c1b553364
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a>Introdução ao F # no Visual Studio para Mac

F # e as ferramentas do Visual F # têm suporte no Visual Studio para Mac IDE.  Para começar, você deve [baixar o Visual Studio para Mac](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs), se ainda não o fez.  Este artigo usa o Visual Studio de 2017 de comunidade para Mac, mas você pode usar F # com a versão de sua escolha.

## <a name="installing-f"></a>Instalando a F # #

Depois de baixar o Visual Studio para Mac, ele solicitará que você escolher o que você deseja instalar.  Para os fins deste artigo, estará deixando os padrões.  Em contraste com o Visual Studio para Windows, não é necessário instalar especificamente o suporte de F #.  Clique em "Instalar" para continuar.

Depois de concluir a instalação, escolha "Iniciar o Visual Studio".  Você também pode iniciá-lo por meio de localizador em macOS.

## <a name="creating-a-console-application"></a>Criando um aplicativo de console

Um dos projetos no Visual Studio para Mac mais básicos é o aplicativo de Console.  Veja como fazer isso.  Depois de abrir o Visual Studio para Mac:

1. Sobre o **arquivo** , aponte para **nova solução**.

2.  Na caixa de diálogo Novo projeto, há 2 modelos diferentes para o aplicativo de Console.  Há um sob outros -> .NET que tem como alvo o .NET Framework.  O outro modelo é em .NET Core -> aplicativo que tem como alvo o núcleo do .NET.  O modelo deve funcionar com a finalidade deste artigo.

3. Em aplicativo de console, altere c# para F # se necessário.  Escolha o **próximo** botão Avançar!  

4. Nomeie o projeto e escolha as opções desejadas para o aplicativo.  Observe, o painel de visualização para o lado da tela que mostra a estrutura de diretório será criada com base nas opções selecionadas.  

5. Clique em **Criar**.  Agora você deve ver um projeto F # no Gerenciador de soluções.

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

Você pode executar o código e ver os resultados, basta clicar em **executar** no menu de nível superior e, em seguida, **Start Without Debugging**.  Isso executará o programa sem depuração e permite que você veja os resultados.

Agora, você verá o seguinte mostrado na janela de console que surge do Visual Studio para Mac:

```
12 squared is 144!
```

Parabéns!  Criou seu primeiro projeto F # no Visual Studio para Mac, escrito que uma função de F # impressos os resultados da chamada de função e execute o projeto para ver alguns resultados.

## <a name="using-f-interactive"></a>Usando F # interativo

Um dos melhores recursos do Visual F # ferramentas no Visual Studio para Mac é a janela interativa F #.  Ele permite que você envie código sobre a um processo em que você pode chamar esse código e ver o resultado de forma interativa.

Para começar a usá-lo, realce o `square` função definida no seu código.  Em seguida, clique em **editar** no menu de nível superior.  Em seguida selecione **enviar seleção para F # interativo**.  Isso executa o código na janela interativa F #.  Como alternativa, você pode clique com o botão direito na seleção e escolha **enviar seleção para F # interativo**.  Você deverá ver a janela interativa F # com o seguinte:

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

As opções acima define uma nova função, `isOdd`, que usa um `int` e verifica se ele for ímpar!  Você pode chamar essa função para ver o que retorna com entradas diferentes.  Você pode chamar funções em chamadas de função:

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

Isso é apenas uma visão rápida sobre o que você pode fazer com F # interativo.  Para saber mais, confira [de programação com F # interativo](../tutorials/fsharp-interactive/index.md).

## <a name="next-steps"></a>Próximas etapas

Se você ainda não fez isso, confira o [Tour do F #](../tour.md), que aborda alguns dos principais recursos da linguagem F #.  Ele fornece uma visão geral de alguns dos recursos do F # e fornece exemplos de código bastante que você pode copiar para o Visual Studio para Mac e executar.  Também há alguns ótimos recursos externos, você pode usar, foi apresentada no [guia F #](../index.md).

## <a name="see-also"></a>Consulte também
 [Visual F#](../index.md)  
 [Tour do F#](../tour.md)  
 [Referência da linguagem F #](../language-reference/index.md)  
 [Inferência de tipo](../language-reference/type-inference.md)  
 [Símbolo e o operador de referência](../language-reference/symbol-and-operator-reference/index.md)  
