---
title: 'Gerenciamento de recursos: A palavra-chave use'
description: Saiba mais sobre F# a palavra-chave ' use ' e a função ' Using ', que podem controlar a inicialização e a versão dos recursos.
ms.date: 05/16/2016
ms.openlocfilehash: 5e0838401bee02050343b2f6dcc646a8dc8b4dc0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627262"
---
# <a name="resource-management-the-use-keyword"></a>Gerenciamento de recursos: A palavra-chave use

Este tópico descreve a palavra `use` -chave `using` e a função, que podem controlar a inicialização e a liberação de recursos.

## <a name="resources"></a>Recursos

O termo *recurso* é usado de mais de uma maneira. Sim, os recursos podem ser dados que um aplicativo usa, como cadeias de caracteres, gráficos e similares, mas neste contexto, os *recursos* referem-se a recursos de software ou do sistema operacional, como contextos de dispositivo de gráficos, identificadores de arquivos, rede e banco de dados conexões, objetos de simultaneidade, como identificadores de espera e assim por diante. O uso desses recursos por aplicativos envolve a aquisição do recurso do sistema operacional ou de outro provedor de recursos, seguido pela versão posterior do recurso para o pool, para que ele possa ser fornecido a outro aplicativo. Os problemas ocorrem quando os aplicativos não liberam recursos de volta para o pool comum.

## <a name="managing-resources"></a>Gerenciando recursos

Para gerenciar com eficiência e responsabilidade os recursos em um aplicativo, você deve liberar recursos de forma imediata e de maneira previsível. O .NET Framework ajuda você a fazer isso fornecendo a `System.IDisposable` interface. Um tipo que implementa `System.IDisposable` o tem `System.IDisposable.Dispose` o método, que libera corretamente os recursos. Os aplicativos bem escritos garantem `System.IDisposable.Dispose` que o seja chamado imediatamente quando qualquer objeto que mantém um recurso limitado não for mais necessário. Felizmente, a maioria das linguagens .NET oferece suporte para tornar isso F# mais fácil e não é exceção. Há duas construções de linguagem úteis que dão suporte ao padrão Dispose: a `use` associação e a `using` função.

## <a name="use-binding"></a>usar Associação

A `use` palavra-chave tem um formulário semelhante ao `let` da associação:

usar*expressão* de *valor* = 

Ele fornece a mesma funcionalidade que uma `let` associação, mas adiciona uma chamada `Dispose` para no valor quando o valor sai do escopo. Observe que o compilador insere uma verificação nula no valor, de modo que, se o valor `null`for, a chamada `Dispose` para não será tentada.

O exemplo a seguir mostra como fechar um arquivo automaticamente usando a `use` palavra-chave.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6301.fs)]

> [!NOTE]
> Você pode usar `use` em expressões de computação, caso em que uma versão personalizada `use` da expressão é usada. Para obter mais informações, consulte [Sequências](sequences.md), [fluxos de trabalho assíncronos](asynchronous-workflows.md)e [expressões de computação](computation-expressions.md).

## <a name="using-function"></a>usando a função

A `using` função tem o seguinte formato:

`using` (*expression1*) *function-or-lambda*

Em uma `using` expressão, *expressão1* cria o objeto que deve ser Descartado. O resultado de *expression1* (o objeto que deve ser descartado) torna-se um argumento, um *valor*, para *Function-ou-lambda*, que é uma função que espera um único argumento restante de um tipo que corresponda ao valor produzido por  *expression1*ou uma expressão lambda que espera um argumento desse tipo. No final da execução da função, o tempo de execução chama `Dispose` e libera os recursos (a menos que o valor seja `null`; nesse caso, a chamada para Dispose não é tentada).

O exemplo a seguir demonstra `using` a expressão com uma expressão lambda.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6302.fs)]

O exemplo a seguir mostra `using` a expressão com uma função.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6303.fs)]

Observe que a função pode ser uma função que já tem alguns argumentos aplicados. O código de exemplo a seguir demonstra isso. Ele cria um arquivo que contém a cadeia `XYZ`de caracteres.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6304.fs)]

A `using` função e a `use` associação são praticamente equivalentes a realizar a mesma coisa. A `using` palavra-chave fornece mais controle `Dispose` sobre quando é chamado. Quando você usa `using`, `Dispose` é chamado no final da função ou expressão lambda; quando você usa a `use` palavra-chave, `Dispose` é chamado no final do bloco de código que o contém. Em geral, você deve preferir usar `use` em vez `using` da função.

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
