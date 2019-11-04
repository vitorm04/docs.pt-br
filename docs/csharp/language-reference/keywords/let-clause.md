---
title: Cláusula let – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: df3df279d2dbdb59a0a94d9afad37d1a7ddf7b57
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422693"
---
# <a name="let-clause-c-reference"></a>Cláusula let (Referência de C#)

Em uma expressão de consulta, às vezes é útil armazenar o resultado de uma subexpressão para usá-lo em cláusulas subsequentes. É possível fazer isso com a palavra-chave `let`, que cria uma nova variável de intervalo e a inicializa com o resultado da expressão fornecida. Depois de inicializado com um valor, a variável de intervalo não pode ser usada para armazenar outro valor. No entanto, se a variável de intervalo mantiver um tipo passível de consulta, ela poderá ser consultada.

## <a name="example"></a>Exemplo

No exemplo a seguir, `let` é usado de duas maneiras:

1. Para criar um tipo enumerável que pode ser pesquisado por si só.

2. Para permitir que a consulta chame `ToLower` apenas uma vez na variável de intervalo `word`. Sem usar `let`, seria necessário chamar `ToLower` em cada predicado na cláusula `where`.

[!code-csharp[cscsrefQueryKeywords#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Let.cs#28)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../../language-reference/index.md)
- [Palavras-chave de Consulta (LINQ)](query-keywords.md)
- [LINQ (Consulta Integrada à Linguagem)](../../linq/index.md)
- [Introdução a LINQ em C#](/dotnet/csharp/programming-guide/concepts/linq/)
- [Manipular exceções em expressões de consultas](../../linq/handle-exceptions-in-query-expressions.md)
