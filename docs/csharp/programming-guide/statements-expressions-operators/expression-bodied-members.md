---
title: Membros aptos para expressão – Guia de Programação em C#
ms.date: 02/06/2019
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
ms.openlocfilehash: f212bb707d3dd2d4a7cc917d335a83cff01ed0cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75711981"
---
# <a name="expression-bodied-members-c-programming-guide"></a>Membros aptos para expressão (Guia de Programação em C#)

As definições de corpo da expressão permitem que você forneça uma implementação de um membro em uma forma bastante concisa e legível. Você pode usar uma definição de corpo da expressão sempre que a lógica para qualquer membro com suporte, como um método ou propriedade, consiste em uma única expressão. Uma definição de corpo da expressão tem a seguinte sintaxe geral:

```csharp
member => expression;
```

em que *expression* é uma expressão válida.

O suporte para definições de corpo da expressão foi introduzido para métodos e propriedades somente leitura no C# 6 e foi expandido no C# 7.0. As definições de corpo da expressão podem ser usadas com os membros de tipo listados na tabela a seguir:

|Membro  |Com suporte desde... |
|---------|---------|
|[Método](#methods)  |C# 6 |
|[Propriedade somente leitura](#read-only-properties)   |C# 6  |
|[Propriedade](#properties)  |C# 7.0 |
|[Construtor](#constructors)   |C# 7.0 |
|[Finalizer](#finalizers)     |C# 7.0 |
|[Indexador](#indexers)       |C# 7.0 |

## <a name="methods"></a>Métodos

Um método apto para expressão consiste em uma única expressão que retorna um valor cujo tipo corresponde ao tipo de retorno do método, ou, para métodos que retornam `void`, que executam uma operação. Por exemplo, os tipos que substituem o método <xref:System.Object.ToString%2A> normalmente incluem uma única expressão que retorna a representação da cadeia de caracteres do objeto atual.

O exemplo a seguir define uma classe `Person` que substitui o método <xref:System.Object.ToString%2A> por uma definição de corpo da expressão. Ele também define um método `DisplayName` que exibe um nome para o console. Observe que a palavra-chave `return` não é usada na definição de corpo da expressão `ToString`.

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

Para obter mais informações, consulte [Métodos (Guia de Programação em C#)](../classes-and-structs/methods.md).

## <a name="read-only-properties"></a>Propriedades somente leitura

Começando no C# 6, você pode usar a definição de corpo da expressão para implementar uma propriedade somente leitura. Para isso, use a seguinte sintaxe:

```csharp
PropertyType PropertyName => expression;
```

O exemplo a seguir define uma classe `Location` cuja propriedade somente leitura `Name` é implementada como uma definição de corpo da expressão que retorna o valor do campo `locationName` particular:

[!code-csharp[expression-bodied-read-only-property](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

Para obter mais informações sobre as propriedades, confira [Propriedades (Guia de Programação em C#)](../classes-and-structs/properties.md).

## <a name="properties"></a>Propriedades

Começando no C# 7.0, você pode usar as definições de corpo da expressão para implementar a propriedade `get` e os acessadores `set`. O exemplo a seguir demonstra como fazer isso:

[!code-csharp[expression-bodied-property-get-set](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]

Para obter mais informações sobre as propriedades, confira [Propriedades (Guia de Programação em C#)](../classes-and-structs/properties.md).

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

## <a name="indexers"></a>Indexadores

Como nas propriedades, `get` `set` o indexador e os `get` acessórios consistem em definições de corpo `set` de expressão se o acessório consiste em uma única expressão que retorna um valor ou o acessório executa uma atribuição simples.

O exemplo a seguir define uma classe chamada `Sports` que inclui uma matriz <xref:System.String> interna que contém os nomes de vários esportes. Tanto o `get` indexador quanto `set` os acessórios são implementados como definições de corpo de expressão.

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)]

Para obter mais informações, consulte [Indexadores (Guia de Programação em C#)](../indexers/index.md).
