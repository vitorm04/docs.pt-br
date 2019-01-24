---
title: '- Operador - referência do C#'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- -_CSharpKeyword
helpviewer_keywords:
- '- operator [C#]'
- subtraction operator (-) [C#]
ms.assetid: 4de7a4fa-c69d-48e6-aff1-3130af970b2d
ms.openlocfilehash: 8cf6e8871a88e2b37b9531ecbd616289523473c7
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333753"
---
# <a name="--operator-c-reference"></a>Operador - (referência do C#)

O operador `-` pode funcionar como um operador unário ou binário.

## <a name="remarks"></a>Comentários

Os operadores `-` unários são predefinidos para todos os tipos numéricos. O resultado de uma operação `-` unária em um tipo numérico é a negação numérica do operando.

Os operadores `-` binários são predefinidos para todos os tipos numéricos e de enumeração para subtrair o segundo operando do primeiro.

Os tipos delegados também fornecem um operador `-` binário, que executa a remoção de delegados.

Tipos definidos pelo usuário podem sobrecarregar os operadores `-` unários e `-` binários. Para obter mais informações, confira a [palavra-chave operator](../keywords/operator.md).

## <a name="example"></a>Exemplo

[!code-csharp[csRefOperators#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#40)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)