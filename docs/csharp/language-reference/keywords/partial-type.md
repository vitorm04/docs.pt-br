---
title: tipo parcial – Referência em C#
ms.date: 07/20/2015
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
helpviewer_keywords:
- partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
ms.openlocfilehash: 551145b9cdf5fa24f3ae365665e8ff06cf5e9307
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715216"
---
# <a name="partial-type-c-reference"></a>tipo parcial (Referência em C#)

Definições de tipo parcial permitem que a definição de uma classe, struct ou interface seja dividida em vários arquivos.

Em *File1.cs*:

[!code-csharp[csrefKeywordsContextual#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#3)]  

Em *File2.cs* a declaração:

[!code-csharp[csrefKeywordsContextual#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#4)]  

## <a name="remarks"></a>Comentários

Dividir um tipo de classe, struct ou interface em vários arquivos pode ser útil quando você está trabalhando com projetos grandes ou com o código gerado automaticamente, como o código fornecido pelo [Designer de Formulários do Windows](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md). Um tipo parcial pode conter um [método parcial](partial-method.md). Para obter mais informações, consulte [Classes parciais e métodos](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).

## <a name="c-language-specification"></a>especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Confira também

- [C# Referência](../index.md)
- [C# Guia de Programação](../../programming-guide/index.md)
- [Modificadores](index.md)
- [Introdução aos genéricos](../../programming-guide/generics/index.md)
