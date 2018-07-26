---
title: Fluxos de trabalho assíncronos (F#)
description: 'Saiba mais sobre o suporte a idioma para executar cálculos de forma assíncrona, de programação F # que são executadas sem bloquear a execução de outro trabalho.'
ms.date: 05/16/2016
ms.openlocfilehash: 9516a281701b6c431fc950fe6881359f9c8a672b
ms.sourcegitcommit: dc02d7d95f1e3efcc7166eaf431b0ec0dc9d8dca
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37143499"
---
# <a name="asynchronous-workflows"></a>Fluxos de trabalho assíncronos

> [!NOTE]
O link de referência da API levará você até o MSDN.  A referência da API docs.microsoft.com não está completa.

Este tópico descreve o suporte em F # para executar cálculos de forma assíncrona, ou seja, sem bloquear a execução de outro trabalho. Por exemplo, as computações assíncronas podem ser usadas para gravar aplicativos que têm interfaces do usuário que permaneçam responsivos a usuários conforme o aplicativo execute outro trabalho.

## <a name="syntax"></a>Sintaxe

```fsharp
async { expression }
```

## <a name="remarks"></a>Comentários

Na sintaxe anterior, a computação é representado por `expression` está configurado para ser executado de forma assíncrona, ou seja, sem bloquear o thread atual de cálculo quando operações de suspensão assíncrona, e/s e outras operações assíncronas são executadas. Computações assíncronas normalmente são iniciadas em um thread em segundo plano durante a execução continua no thread atual. O tipo da expressão é `Async<'T>`, onde `'T` é o tipo retornado pela expressão quando o `return` palavra-chave é usada. O código em uma expressão é conhecido como um *bloco assíncrono*, ou *bloco assíncrono*.

Há várias maneiras de programação assíncrona e o [ `Async` ](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7) classe fornece métodos que oferecem suporte a vários cenários. A abordagem geral é criar `Async` objetos que representam o cálculo ou cálculos que você deseja executar de maneira assíncrona e, em seguida, iniciar esses cálculos usando uma das funções de disparo. As várias funções de disparo fornecem maneiras diferentes de executar cálculos assíncronos e qual deles usar depende se você deseja usar o thread atual, um thread em segundo plano ou um objeto de tarefa do .NET Framework, e se há continuação funções que devem ser executados quando o cálculo seja concluído. Por exemplo, para iniciar uma computação assíncrona no thread atual, você pode usar [ `Async.StartImmediate` ](https://msdn.microsoft.com/library/2f71d1cc-187f-48cf-ac66-e7fda41c46e3). Quando você inicia uma computação assíncrona do thread de interface do usuário, você não bloqueiam o loop principal do evento que processa as ações do usuário, como pressionamentos de tecla e atividade do mouse, para que seu aplicativo permaneça responsivo.

## <a name="asynchronous-binding-by-using-let"></a>Vinculação assíncrona usando let!

Em um fluxo de trabalho assíncrono, algumas expressões e operações são síncronas, e alguns são mais cálculos que são projetados para retornar um resultado de forma assíncrona. Quando você chama um método de forma assíncrona, em vez de um comum `let` associando, use `let!`. O efeito de `let!` é permitir a execução continue em outros cálculos ou threads como a computação está sendo executada. Após o lado direito do `let!` associação retorna, o restante do fluxo de trabalho assíncrono retoma a execução.

O código a seguir mostra a diferença entre `let` e `let!`. A linha de código que usa `let` apenas cria uma computação assíncrona como um objeto que pode ser executado posteriormente, usando, por exemplo, `Async.StartImmediate` ou [ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b). A linha de código que usa `let!` inicia o cálculo e, em seguida, o thread está suspenso até que o resultado esteja disponível, em que ponto a execução continua.

```fsharp
// let just stores the result as an asynchronous operation.
let (result1 : Async<byte[]>) = stream.AsyncRead(bufferSize)
// let! completes the asynchronous operation and returns the data.
let! (result2 : byte[])  = stream.AsyncRead(bufferSize)
```

Além `let!`, você pode usar `use!` para realizar ligações assíncronas. A diferença entre `let!` e `use!` é o mesmo que a diferença entre `let` e `use`. Para `use!`, o objeto é descartado no fechamento do escopo atual. Observe que na versão atual da linguagem F #, `use!` não permite que um valor a ser inicializada como nula, mesmo que `use` faz.

## <a name="asynchronous-primitives"></a>Primitivos assíncronos

Um método que executa uma única tarefa assíncrona e retorna o resultado é chamado um *primitivo assíncrono*, e elas foram desenvolvidas especificamente para uso com `let!`. Vários primitivos assíncronos são definidos na biblioteca de núcleo do F #. Dois métodos para aplicativos da Web são definidos no módulo [ `Microsoft.FSharp.Control.WebExtensions` ](https://msdn.microsoft.com/library/95ef17bc-ee3f-44ba-8a11-c90fcf4cf003): [ `WebRequest.AsyncGetResponse` ](https://msdn.microsoft.com/library/09a60c31-e6e2-4b5c-ad23-92a86e50060c) e [ `WebClient.AsyncDownloadString` ](https://msdn.microsoft.com/library/8a85a9b7-f712-4cac-a0ce-0a797f8ea32a). Ambos os primitivos de download de dados de uma página da Web, dada um URL. `AsyncGetResponse` produz um `System.Net.WebResponse` objeto, e `AsyncDownloadString` produz uma cadeia de caracteres que representa o HTML para uma página da Web.

Vários primitivos para operações de e/s assíncronas são incluídos na [ `Microsoft.FSharp.Control.CommonExtensions` ](https://msdn.microsoft.com/library/2edb67cb-6814-4a30-849f-b6dbdd042396) módulo. Esses métodos de extensão do `System.IO.Stream` classe estão [ `Stream.AsyncRead` ](https://msdn.microsoft.com/library/85698aaa-bdda-47e6-abed-3730f59fda5e) e [ `Stream.AsyncWrite` ](https://msdn.microsoft.com/library/1b0a2751-e42a-47e1-bd27-020224adc618).

Você também pode escrever seus próprios primitivos assíncronos, definindo uma função cujo corpo completo é colocado em um bloco assíncrono.

Para usar métodos assíncronos no .NET Framework que são projetados para outros modelos assíncronos com o F # modelo de programação assíncrona, você cria uma função que retorna da F # `Async` objeto. A biblioteca F # tem funções que tornam isso mais fácil de fazer.

Um exemplo de como usar fluxos de trabalho assíncronos é incluído aqui; Há muitas outras na documentação para os métodos do [classe Async](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).

Este exemplo mostra como usar fluxos de trabalho assíncronos para executar cálculos em paralelo.

No exemplo de código, uma função `fetchAsync` obtém o texto HTML é retornado de uma solicitação da Web. O `fetchAsync` função contém um bloco assíncrono de código. Quando uma associação é feita para o resultado de um primitivo assíncrono, neste caso [ `AsyncDownloadString` ](https://msdn.microsoft.com/library/8a85a9b7-f712-4cac-a0ce-0a797f8ea32a), let! é usado em vez de let.

Use a função [ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) para executar uma operação assíncrona e esperar seu resultado. Por exemplo, você pode executar várias operações assíncronas em paralelo usando o [ `Async.Parallel` ](https://msdn.microsoft.com/library/aa9b0355-2d55-4858-b943-cbe428de9dc4) funcionar junto com o `Async.RunSynchronously` função. O `Async.Parallel` função utiliza uma lista da `Async` objetos, define o código para cada `Async` objeto de tarefa para ser executado em paralelo e retorna um `Async` objeto que representa a computação paralela. Como acontece com uma única operação, você deve chamar `Async.RunSynchronously` para iniciar a execução.

O `runAll` função inicia três fluxos de trabalho assíncronos em paralelo e aguarda até que elas sejam concluídas.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet8003.fs)]

## <a name="see-also"></a>Consulte também

[Referência da Linguagem F#](index.md)

[Expressões de Computação](computation-expressions.md)

[Classe Control. Async](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.async-class-%5bfsharp%5d)
