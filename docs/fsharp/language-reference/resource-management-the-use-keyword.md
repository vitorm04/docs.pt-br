---
title: 'Gerenciamento de recursos: a palavra-chave use (F#)'
description: "Saiba mais sobre o F # palavra-chave 'use' e a função 'usando', que pode controlar a inicialização e a liberação de recursos."
ms.date: 05/16/2016
ms.openlocfilehash: c75783080d1d87c6ee75aede500d3d0b3fdf8355
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564892"
---
# <a name="resource-management-the-use-keyword"></a>Gerenciamento de recursos: a palavra-chave use

Este tópico descreve a palavra-chave `use` e `using` função, que pode controlar a inicialização e a liberação de recursos.

## <a name="resources"></a>Recursos
O termo *recurso* é usado em mais de uma maneira. Sim, os recursos podem ser dados que usa um aplicativo, como cadeias de caracteres, gráficos e assim por diante, mas nesse contexto, *recursos* refere-se aos recursos de software ou sistema operacional, como os contextos de dispositivo de gráficos, identificadores de arquivos, rede banco de dados e conexões, objetos de simultaneidade, como identificadores de espera e assim por diante. O uso desses recursos por aplicativos envolve a aquisição de recursos do sistema operacional ou outro provedor de recursos, seguido da versão mais recente do recurso para o pool para que ele pode ser fornecido para outro aplicativo. Ocorrer problemas quando os aplicativos não liberar recursos de volta para o pool comum.

## <a name="managing-resources"></a>Gerenciamento de recursos
Para e de forma eficiente com responsabilidade gerenciar recursos em um aplicativo, você deve liberar recursos imediatamente e de maneira previsível. O .NET Framework ajuda você a fazer isso, fornecendo o `System.IDisposable` interface. Um tipo que implementa `System.IDisposable` tem o `System.IDisposable.Dispose` método, o que libera corretamente os recursos. Aplicativos escritos bem garantem que `System.IDisposable.Dispose` é chamado imediatamente quando qualquer objeto que contém um recurso limitado não for mais necessário. Felizmente, a maioria das linguagens .NET fornecem suporte para facilitar essa tarefa, e F # não é exceção. Há duas construções de linguagem úteis que suportam o padrão dispose: o `use` associação e o `using` função.

## <a name="use-binding"></a>usar associação
O `use` palavra-chave tem um formulário que se assemelha a do `let` associação:

Use *valor* = *expressão*

Ele fornece a mesma funcionalidade de um `let` de associação, mas adiciona uma chamada para `Dispose` no valor quando o valor sai do escopo. Observe que o compilador insere uma verificação de nulos no valor, para que, se o valor seja `null`, a chamada para `Dispose` não é realizada.

O exemplo a seguir mostra como fechar um arquivo automaticamente usando o `use` palavra-chave.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6301.fs)]

>[!NOTE]
Você pode usar `use` em expressões de cálculo, caso em que uma versão personalizada do `use` expressão é usada. Para obter mais informações, consulte [sequências](sequences.md), [fluxos de trabalho assíncronos](asynchronous-workflows.md), e [expressões de computação](computation-expressions.md).


## <a name="using-function"></a>usando a função
O `using` função tem a seguinte forma:

`using` (*expression1*) *função ou lambda*

Em um `using` expressão, *expression1* cria o objeto deve ser descartado. O resultado de *expression1* (o objeto deve ser descartado) torna-se um argumento, *valor*, *função ou lambda*, que é a uma função que espera um único restantes argumento de um tipo que corresponde ao valor produzido por *expression1*, ou uma expressão lambda que espera um argumento de tipo. No final da execução da função, o tempo de execução chama `Dispose` e libera os recursos (a menos que o valor é `null`, caso em que a chamada Dispose não é realizada).

O exemplo a seguir demonstra o `using` expressão com uma expressão lambda.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6302.fs)]

A exemplo a seguir mostra o `using` expressão com uma função.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6303.fs)]

Observe que a função pode ser uma função que tem alguns argumentos já aplicados. O código de exemplo a seguir demonstra isso. Ele cria um arquivo que contém a cadeia de caracteres `XYZ`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6304.fs)]

O `using` função e o `use` associação são praticamente equivalentes maneiras de realizar a mesma coisa. O `using` palavra-chave fornece mais controle sobre quando `Dispose` é chamado. Quando você usa `using`, `Dispose` é chamado no final da expressão lambda ou de função; quando você usar o `use` palavra-chave, `Dispose` é chamado no final do bloco de código. Em geral, você deve preferir usar `use` em vez do `using` função.


## <a name="see-also"></a>Consulte também
[Referência da Linguagem F#](index.md)
