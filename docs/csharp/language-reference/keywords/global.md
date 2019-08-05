---
title: Palavra-chave contextual global – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- global
- global_CSharpKeyword
helpviewer_keywords:
- global keyword [C#]
ms.assetid: 8932c16a-6959-42c2-86e7-2c4221ab788b
ms.openlocfilehash: 9a8c7b5134cc29668aae53e8a3f86ddae4c8263a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627687"
---
# <a name="global-c-reference"></a>global (Referência de C#)

Quando a palavra-chave contextual `global` vem antes do [operador ::](../operators/namespace-alias-qualifier.md), refere-se ao namespace global, que é o namespace padrão para qualquer programa em C#, que não foi nomeado de outra maneira. Para obter mais informações, confira [Como: usar o alias de namespace global](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md).

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como usar a palavra-chave contextual `global` para especificar que a classe `TestApp` é definida no namespace global:

[!code-csharp[csrefKeywordsContextual#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#13)]

## <a name="see-also"></a>Consulte também

- [Namespaces](../../programming-guide/namespaces/index.md)
