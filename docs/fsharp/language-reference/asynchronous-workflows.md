---
title: Fluxos de trabalho assíncronos
description: Saiba mais sobre o F# suporte na linguagem de programação para executar computações de forma assíncrona, que são executadas sem bloquear a execução de outro trabalho.
ms.date: 05/16/2016
ms.openlocfilehash: 2d967f6bfe46b4f3916648b3063210d1ba1c210f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630005"
---
# <a name="asynchronous-workflows"></a>Fluxos de trabalho assíncronos

> [!NOTE]
> O link de referência da API levará você até o MSDN.  A referência da API docs.microsoft.com não está completa.

Este tópico descreve o suporte F# no para executar cálculos de forma assíncrona, ou seja, sem bloquear a execução de outro trabalho. Por exemplo, as Computações assíncronas podem ser usadas para gravar aplicativos que têm interfaces do usuário que permanecem responsivas aos usuários enquanto o aplicativo executa outro trabalho.

## <a name="syntax"></a>Sintaxe

```fsharp
async { expression }
```

## <a name="remarks"></a>Comentários

Na sintaxe anterior, a computação representada por `expression` é configurada para ser executada de forma assíncrona, ou seja, sem bloquear o thread de computação atual quando operações de suspensão assíncronas, e/s e outras operações assíncronas são executadas. As Computações assíncronas geralmente são iniciadas em um thread em segundo plano enquanto a execução continua no thread atual. O tipo da expressão é `Async<'T>`, em que `'T` é o tipo retornado pela expressão quando a `return` palavra-chave é usada. O código nessa expressão é conhecido como um *bloco assíncrono*ou um *bloco assíncrono*.

Há várias maneiras de programar de forma assíncrona, e [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7) a classe fornece métodos que dão suporte a vários cenários. A abordagem geral é criar `Async` objetos que representem a computação ou cálculos que você deseja executar de forma assíncrona e, em seguida, iniciar esses cálculos usando uma das funções de disparo. As várias funções de disparo fornecem diferentes maneiras de executar Computações assíncronas e qual delas você usa depende se você deseja usar o thread atual, um thread em segundo plano ou um .NET Framework objeto de tarefa e se há continuação funções que devem ser executadas quando o cálculo é concluído. Por exemplo, para iniciar uma computação assíncrona no thread atual, você pode usar [`Async.StartImmediate`](https://msdn.microsoft.com/library/2f71d1cc-187f-48cf-ac66-e7fda41c46e3). Quando você inicia uma computação assíncrona do thread da interface do usuário, não bloqueia o loop de evento principal que processa ações do usuário, como pressionamentos de teclas e atividade do mouse, para que seu aplicativo permaneça responsivo.

## <a name="asynchronous-binding-by-using-let"></a>Associação assíncrona usando Let!

Em um fluxo de trabalho assíncrono, algumas expressões e operações são síncronas e algumas são computações mais longas que são projetadas para retornar um resultado de forma assíncrona. Ao chamar um método de forma assíncrona, em vez `let` de uma associação comum `let!`, você usa. O efeito do `let!` é permitir que a execução continue em outros cálculos ou threads à medida que o cálculo está sendo executado. Após o lado direito da `let!` Associação retornar, o restante do fluxo de trabalho assíncrono retomará a execução.

O código a seguir mostra a diferença `let` entre `let!`e. A linha de código que o `let` usa cria apenas uma computação assíncrona como um objeto que você pode executar mais tarde usando, por `Async.StartImmediate` exemplo [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b), ou. A linha de código que o `let!` usa inicia a computação e, em seguida, o thread é suspenso até que o resultado esteja disponível, no ponto em que a execução continua.

```fsharp
// let just stores the result as an asynchronous operation.
let (result1 : Async<byte[]>) = stream.AsyncRead(bufferSize)
// let! completes the asynchronous operation and returns the data.
let! (result2 : byte[])  = stream.AsyncRead(bufferSize)
```

Além disso `let!`, você pode usar `use!` o para executar associações assíncronas. A diferença entre `let!` e `use!` é a mesma que a diferença entre `let` e `use`. Para `use!`, o objeto é Descartado no fechamento do escopo atual. Observe que, na versão atual do F# idioma, `use!` o não permite que um valor seja inicializado como nulo, embora `use` o faça.

## <a name="asynchronous-primitives"></a>Primitivos assíncronos

Um método que executa uma única tarefa assíncrona e retorna o resultado é chamado de *primitivo assíncrono*, e eles são projetados especificamente para uso `let!`com o. Vários primitivos assíncronos são definidos na F# biblioteca principal. Dois métodos desse tipo para aplicativos Web são definidos no módulo [`Microsoft.FSharp.Control.WebExtensions`](https://msdn.microsoft.com/library/95ef17bc-ee3f-44ba-8a11-c90fcf4cf003): [`WebRequest.AsyncGetResponse`](https://msdn.microsoft.com/library/09a60c31-e6e2-4b5c-ad23-92a86e50060c) e [`WebClient.AsyncDownloadString`](https://msdn.microsoft.com/library/8a85a9b7-f712-4cac-a0ce-0a797f8ea32a). Os dois primitivos baixam dados de uma página da Web, dada uma URL. `AsyncGetResponse`produz um `System.Net.WebResponse` objeto e `AsyncDownloadString` produz uma cadeia de caracteres que representa o HTML de uma página da Web.

Vários primitivos para operações de e/s assíncronas estão [`Microsoft.FSharp.Control.CommonExtensions`](https://msdn.microsoft.com/library/2edb67cb-6814-4a30-849f-b6dbdd042396) incluídos no módulo. Esses métodos de extensão da `System.IO.Stream` classe são [`Stream.AsyncRead`](https://msdn.microsoft.com/library/85698aaa-bdda-47e6-abed-3730f59fda5e) e [`Stream.AsyncWrite`](https://msdn.microsoft.com/library/1b0a2751-e42a-47e1-bd27-020224adc618).

Você também pode escrever seus próprios primitivos assíncronos definindo uma função cujo corpo completo é colocado em um bloco assíncrono.

Para usar métodos assíncronos no .NET Framework que são criados para outros modelos assíncronos com F# o modelo de programação assíncrona, você cria uma função F# `Async` que retorna um objeto. A F# biblioteca tem funções que facilitam essa tarefa.

Um exemplo de uso de fluxos de trabalho assíncronos está incluído aqui; Há muitos outros na documentação para os métodos da [classe Async](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).

Este exemplo mostra como usar fluxos de trabalho assíncronos para executar cálculos em paralelo.

No exemplo de código a seguir, uma `fetchAsync` função obtém o texto HTML retornado de uma solicitação da Web. A `fetchAsync` função contém um bloco de código assíncrono. Quando uma associação é feita com o resultado de um primitivo assíncrono, neste caso [`AsyncDownloadString`](https://msdn.microsoft.com/library/8a85a9b7-f712-4cac-a0ce-0a797f8ea32a), Let! é usado em vez de Let.

Você usa a função [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) para executar uma operação assíncrona e aguardar seu resultado. Por exemplo, você pode executar várias operações assíncronas em paralelo usando a [`Async.Parallel`](https://msdn.microsoft.com/library/aa9b0355-2d55-4858-b943-cbe428de9dc4) função junto com a `Async.RunSynchronously` função. A `Async.Parallel` função usa uma lista `Async` dos objetos, configura o código para cada `Async` objeto de tarefa a ser executado em paralelo e retorna um `Async` objeto que representa a computação paralela. Assim como para uma única operação, você chama `Async.RunSynchronously` para iniciar a execução.

A `runAll` função inicia três fluxos de trabalho assíncronos em paralelo e aguarda até que todos tenham sido concluídos.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet8003.fs)]

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
- [Expressões de Computação](computation-expressions.md)
- [Classe Control. Async](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.async-class-%5bfsharp%5d)
