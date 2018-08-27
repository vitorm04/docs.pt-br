---
title: Membros aptos para expressão (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e58afadae78d3f6b15a8e859edc8d554d84c393
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "42911900"
---
# <a name="expression-bodied-members-c-programming-guide"></a>Membros aptos para expressão (Guia de Programação em C#)
As definições de corpo da expressão permitem que você forneça uma implementação de um membro em uma forma bastante concisa e legível. Você pode usar uma definição de corpo da expressão sempre que a lógica para qualquer membro com suporte, como um método ou propriedade, consiste em uma única expressão. Uma definição de corpo da expressão tem a seguinte sintaxe geral:

```csharp
member => expression;
```

em que *expression* é uma expressão válida. 

O suporte para definições no corpo da expressão foi introduzido para acessadores get de propriedade e de métodos no C# 6 e foi expandido no C# 7.0. As definições de corpo da expressão podem ser usadas com os membros de tipo listados na tabela a seguir: 

|Membro  |Com suporte desde... |
|---------|---------|
|[Método](#methods)  |C# 6 |
|[Construtor](#constructors)   |C# 7.0 |
|[Finalizador](#finalizers)     |C# 7.0 |
|[Get da propriedade](#property-get-statements)  |C# 6 |
|[Set da propriedade](#property-set-statements)  |C# 7.0 |
|[Indexador](#indexers)       |C# 7.0 |

## <a name="methods"></a>Métodos

Um método apto para expressão consiste em uma única expressão que retorna um valor cujo tipo corresponde ao tipo de retorno do método, ou, para métodos que retornam `void`, que executam uma operação. Por exemplo, os tipos que substituem o método <xref:System.Object.ToString%2A> normalmente incluem uma única expressão que retorna a representação da cadeia de caracteres do objeto atual. 

O exemplo a seguir define uma classe `Person` que substitui o método <xref:System.Object.ToString%2A> por uma definição de corpo da expressão. Ele também define um método `DisplayName` que exibe um nome para o console. Observe que a palavra-chave `return` não é usada na definição de corpo da expressão `ToString`.

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

Para obter mais informações, consulte [Métodos (Guia de Programação em C#)](../classes-and-structs/methods.md).
 
## <a name="constructors"></a>Construtores

Uma definição de corpo da expressão para um construtor normalmente consiste em uma expressão de atribuição simples ou uma chamada de método que manipula os argumentos do construtor ou inicializa o estado da instância. 

O exemplo a seguir define uma classe `Location` cujo construtor tem um único parâmetro de cadeia de caracteres chamado *nome*. A definição de corpo da expressão atribui o argumento à propriedade `Name`.

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

Para obter mais informações, consulte [Construtores (Guia de Programação em C#)](../classes-and-structs/constructors.md).

## <a name="finalizers"></a>Finalizadores

Uma definição de corpo da expressão para um finalizador normalmente contém instruções de limpeza, como instruções que liberam recursos não gerenciados.

O exemplo a seguir define um finalizador que usa uma definição de corpo da expressão para indicar que o finalizador foi chamado.

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

Para obter mais informações, consulte [Finalizadores (Guia de Programação em C#)](../classes-and-structs/destructors.md).

## <a name="property-get-statements"></a>Instruções get da propriedade

Se você optar por implementar um acessador get da propriedade por conta própria, poderá usar uma definição de corpo da expressão para expressões únicas que retornam simplesmente o valor da propriedade. Observe que a instrução `return` não é usada.

O exemplo a seguir define uma propriedade `Location.Name` cujo acessador get da propriedade retorna o valor do campo `locationName` particular que sustenta a propriedade. 

[!code-csharp[expression-bodied-property-getter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

As propriedades somente leitura que usam uma definição de corpo da expressão podem ser implementadas sem uma instrução `set` explícita. A sintaxe é:

```csharp
PropertyName => returnValue;
```

O exemplo a seguir define uma classe `Location` cuja propriedade `Name` somente leitura é implementada como uma definição de corpo da expressão que retorna o valor do campo `locationName` particular.

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

Para obter mais informações, consulte [Propriedades (Guia de Programação em C#)](../classes-and-structs/properties.md).

## <a name="property-set-statements"></a>Instruções set da propriedade

Se você optar por implementar um acessador set da propriedade por conta própria, poderá usar uma definição de corpo da expressão para uma expressão de linha única que atribui um valor ao campo que sustenta a propriedade.

O exemplo a seguir define uma propriedade `Location.Name` cujo acessador set da propriedade designa seu argumento de entrada ao campo `locationName` particular que sustenta a propriedade.

[!code-csharp[expression-bodied-property-setter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

Para obter mais informações, consulte [Propriedades (Guia de Programação em C#)](../classes-and-structs/properties.md).

## <a name="indexers"></a>Indexadores

Como as propriedades, os acessadores get e set do indexador consistirão em definições de corpo da expressão se o acessador get consistir em uma única instrução que retorna um valor ou o acessador set executar uma designação simples.

O exemplo a seguir define uma classe chamada `Sports` que inclui uma matriz <xref:System.String> interna que contém os nomes de vários esportes. Os acessadores get e set do indexador são implementados como definições de corpo da expressão.

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)] 

Para obter mais informações, consulte [Indexadores (Guia de Programação em C#)](../indexers/index.md).

