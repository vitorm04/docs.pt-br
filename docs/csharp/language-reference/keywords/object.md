---
title: object – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- object_CSharpKeyword
- object
helpviewer_keywords:
- object keyword [C#]
ms.assetid: 93f60c0b-e17a-40a9-9362-cca5fb77b0e7
ms.openlocfilehash: 99ce5300d06c500d2e45897a6bd57153dc40d34e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633382"
---
# <a name="object-c-reference"></a>object (Referência de C#)

O tipo `object` é um alias de <xref:System.Object> no .NET. No sistema de tipos unificado do C#, todos os tipos, predefinidos e definidos pelo usuário, tipos de referência e tipos de valor, herdam direta ou indiretamente de <xref:System.Object>. Você pode atribuir valores de qualquer tipo a variáveis do tipo `object`. Quando uma variável de um tipo de valor é convertida para um objeto, ela é chamada de *boxed*. Quando uma variável do objeto do tipo é convertida para um tipo de valor, ela é chamada de *unboxed*. Para obter mais informações, consulte [Boxing e unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como variáveis do tipo `object` podem aceitar valores de qualquer tipo de dados e como as variáveis do tipo `object` pode usar métodos <xref:System.Object> do .NET Framework.

[!code-csharp[csrefKeywordsTypes#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#16)]

## <a name="c-language-specification"></a>Especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Palavras-chave do C#](index.md)
- [Tipos de referência](reference-types.md)
- [Tipos de valor](value-types.md)
