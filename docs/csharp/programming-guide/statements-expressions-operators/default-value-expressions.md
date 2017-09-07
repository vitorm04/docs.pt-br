---
title: "expressões de valor padrão (guia de programação em C#)"
description: "As expressões de valor padrão produzem o valor padrão para qualquer tipo de referência ou tipo de valor"
ms.date: 2017-08-23
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], default keyword
- default keyword [C#], generic programming
ms.assetid: b9daf449-4e64-496e-8592-6ed2c8875a98
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 1e548df4de2c07934313311a7ffcfae82be76000
ms.openlocfilehash: 7b5b53d7ed92c6f6377a3e494daf1d02a4cf0934
ms.contentlocale: pt-br
ms.lasthandoff: 08/29/2017

---
# <a name="default-value-expressions-c-programming-guide"></a>Expressões de valor padrão (Guia de Programação em C#)

Uma expressão de valor padrão produz o valor padrão para um tipo. As expressões de valores padrão são úteis principalmente em classes e métodos genéricos. Um problema que surge ao usar genéricos é como atribuir um valor padrão a um tipo parametrizado `T` quando você ainda não sabe o seguinte:

- Se `T` é um tipo de referência ou um tipo de valor.
- Quando `T` é um tipo de valor, se ele é um valor numérico ou um struct definido pelo usuário.

 Dada uma variável `t` de um tipo parametrizado `T`, a instrução `t = null` só será válida se `T` for um tipo de referência. A atribuição `t = 0` funciona apenas para tipos de valor numérico, mas não para structs. A solução é usar uma expressão de valor padrão, que retorna `null` para tipos de referência (tipos de classes e tipos de interface) e zero para tipos de valor numérico. Para estruturas definidas pelo usuário, ela retorna o struct inicializado para o padrão de bit zero, que produz 0 ou `null` para cada membro dependendo se tal membro é um tipo de valor ou de referência. Para tipos que permitem valor nulo, `default` retorna um <xref:System.Nullable%601?displayProperty=fullName>, que é inicializado como qualquer struct.

A expressão `default(T)` não é limitada a classes e métodos genéricos. As expressões de valor padrão podem ser usadas com qualquer tipo gerenciado. Todas estas expressões são válidas:

 [!code-cs[csProgGuideGenerics#1](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-value-expressions.cs)]

 O exemplo da classe `GenericList<T>` a seguir mostra como usar o operador `default(T)` em uma classe genérica. Para obter mais informações, consulte [Visão geral de genéricos](../generics/introduction-to-generics.md).

 [!code-cs[csProgGuideGenerics#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#Snippet41)]

## <a name="default-literal-and-type-inference"></a>Inferência de tipo e literal padrão

A partir do C# 7.1, o literal `default` pode ser usado para expressões de valor padrão quando o compilador pode inferir o tipo da expressão. O literal `default` produz o mesmo valor que o equivalente `default(T)`, em que `T` é o tipo inferido. Isso pode tornar código mais conciso, reduzindo a redundância de declarar um tipo mais de uma vez. O literal `default` pode ser usado em todos os locais a seguir:

- inicializador de variável
- atribuição de variável
- declarando o valor padrão para um parâmetro opcional
- fornecendo o valor para um argumento de chamada de método
- instrução de retorno (ou expressão em um membro no corpo da expressão)

O exemplo a seguir mostra vários tipos de uso do literal `default` em uma expressão de valor padrão:

[!code-cs[csProgGuideGenerics#3](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-literal.cs)]

## <a name="see-also"></a>Consulte também

 <xref:System.Collections.Generic>[Guia de Programação em C#](../index.md)   
 [Genéricos](../generics/index.md)   
 [Métodos Genéricos](../generics/generic-methods.md)   
 [Genéricos](~/docs/standard/generics/index.md)   

