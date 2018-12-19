---
title: Expressões de valor padrão – Guia de Programação em C#
ms.custom: seodec18
description: As expressões de valor padrão produzem o valor padrão para qualquer tipo de referência ou tipo de valor
ms.date: 04/25/2018
helpviewer_keywords:
- generics [C#], default keyword
- default keyword [C#], generic programming
ms.openlocfilehash: 4b14714a55f77763425299ffc13ba579ead57810
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237279"
---
# <a name="default-value-expressions-c-programming-guide"></a>Expressões de valor padrão (Guia de Programação em C#)

Uma expressão de valor padrão `default(T)` produz o valor padrão de um tipo `T`. A tabela a seguir mostra os valores que são produzidos para vários tipos:

|Tipo|Valor padrão|
|---------|---------|
|Qualquer tipo de referência|`null`|
|Tipo de valor numérico|Zero|
|[bool](../../language-reference/keywords/bool.md)|`false`|
|[char](../../language-reference/keywords/char.md)|`'\0'`|
|[enum](../../language-reference/keywords/enum.md)|O valor é produzido pela expressão `(E)0`, em que `E` é o identificador de enumeração.|
|[struct](../../language-reference/keywords/struct.md)|O valor produzido pela configuração de todos os campos de tipo de valor para seus valores padrão e de todos os campos de tipo de referência para `null`.|
|Tipo que permite valor nulo|Uma instância para a qual a propriedade <xref:System.Nullable%601.HasValue%2A> é `false` e a propriedade <xref:System.Nullable%601.Value%2A> não está definida.|

As expressões de valores padrão são úteis principalmente em classes e métodos genéricos. Um problema que surge ao usar genéricos é como atribuir um valor padrão de um tipo parametrizado `T` quando você ainda não sabe o seguinte:

- Se `T` é um tipo de referência ou um tipo de valor.
- Se `T` é um tipo de valor, seja um valor numérico ou um struct.

 Dada uma variável `t` de um tipo parametrizado `T`, a instrução `t = null` só será válida se `T` for um tipo de referência. A atribuição `t = 0` funciona apenas para tipos de valor numérico, mas não para structs. Para resolver isso, use uma expressão de valor padrão:

```csharp
T t = default(T);
```

A expressão `default(T)` não é limitada a classes e métodos genéricos. As expressões de valor padrão podem ser usadas com qualquer tipo gerenciado. Todas estas expressões são válidas:

 [!code-csharp[csProgGuideGenerics#1](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-value-expressions.cs)]

 O exemplo da classe `GenericList<T>` a seguir mostra como usar o operador `default(T)` em uma classe genérica. Para obter mais informações, consulte [Introdução aos Genéricos](../generics/introduction-to-generics.md).

 [!code-csharp[csProgGuideGenerics#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#Snippet41)]

## <a name="default-literal-and-type-inference"></a>Inferência de tipo e literal padrão

A partir do C# 7.1, o literal `default` pode ser usado para expressões de valor padrão quando o compilador pode inferir o tipo da expressão. O literal `default` produz o mesmo valor que o equivalente `default(T)`, em que `T` é o tipo inferido. Isso pode tornar código mais conciso, reduzindo a redundância de declarar um tipo mais de uma vez. O literal `default` pode ser usado em todos os locais a seguir:

- inicializador de variável
- atribuição de variável
- declarando o valor padrão para um parâmetro opcional
- fornecendo o valor para um argumento de chamada de método
- instrução de retorno (ou expressão em um membro no corpo da expressão)

O exemplo a seguir mostra vários tipos de uso do literal `default` em uma expressão de valor padrão:

[!code-csharp[csProgGuideGenerics#3](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-literal.cs)]

## <a name="see-also"></a>Consulte também

- <xref:System.Collections.Generic>  
- [Guia de Programação em C#](../index.md)  
- [Genéricos (guia de programação em C#)](../generics/index.md)  
- [Métodos genéricos](../generics/generic-methods.md)  
- [Genéricos no .NET](~/docs/standard/generics/index.md)  
- [Tabela de valores padrão](../../language-reference/keywords/default-values-table.md)
