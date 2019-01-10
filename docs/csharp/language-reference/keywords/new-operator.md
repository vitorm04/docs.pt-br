---
title: Operador new – Referência em C#
ms.custom: seodec18
ms.date: 03/15/2018
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: e528771d7afeec705f35fa3093a3e4f534b3a1e4
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239846"
---
# <a name="new-operator-c-reference"></a>Operador new (Referência em C#)

Usado para criar objetos e invocar construtores. Por exemplo:

```csharp
Class1 obj  = new Class1();
```

Ele também é usado para criar instâncias de tipos anônimos:

```csharp
var query = from cust in customers
            select new { Name = cust.Name, Address = cust.PrimaryAddress };
```

O operador `new` também é usado para invocar o construtor padrão para tipos de valor. Por exemplo:

```csharp
int i = new int();
```

Na instrução anterior, `i` é inicializado como `0`, que é o valor padrão do tipo `int`. A instrução tem o mesmo efeito que o seguinte:

```csharp
int i = 0;
```

Para ver uma lista completa dos valores padrão, consulte [Tabela de valores padrão](default-values-table.md).

Lembre-se de que é um erro declarar um construtor padrão para um [struct](struct.md), porque cada tipo de valor tem implicitamente um construtor padrão público. É possível declarar construtores parametrizados em um tipo de struct para definir seus valores iniciais, mas isso só é necessário se valores diferentes do padrão forem necessários.

Tanto os objetos de tipo de valor, como structs, quanto os objetos de tipo de referência, como as classes, são destruídos automaticamente, mas os objetos de tipo de valor são destruídos quando o contexto que os contém é destruído, enquanto que os objetos de tipo de referência são destruídos pelo coletor de lixo em um momento não especificado, depois que a última referência a eles é removida. Para tipos que contêm recursos, como identificadores de arquivos ou conexões de rede, é desejável empregar limpeza determinística para garantir que os recursos que eles contêm sejam liberados assim que possível. Para obter mais informações, consulte [Instrução using](using-statement.md).

O operador `new` não pode ser sobrecarregado.

Se o operador `new` não conseguir alocar memória, ele gerará a exceção <xref:System.OutOfMemoryException>.

## <a name="example"></a>Exemplo

No exemplo a seguir, um objeto `struct` e um objeto de classe são criados e inicializados usando o operador `new` e, em seguida, valores atribuídos. Os valores padrão e atribuídos são exibidos.

[!code-csharp[csrefKeywordsOperator#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#7)]

Observe, no exemplo, que o valor padrão de uma cadeia de caracteres é `null`. Portanto, ele não é exibido.

## <a name="c-language-specification"></a>Especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../../language-reference/index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Palavras-chave do C#](index.md)
- [Palavras-chave do operador](operator-keywords.md)
- [new](new.md)
- [Tipos Anônimos](../../programming-guide/classes-and-structs/anonymous-types.md)