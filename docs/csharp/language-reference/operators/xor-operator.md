---
title: Operador ^ – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ^_CSharpKeyword
helpviewer_keywords:
- ^ operator [C#]
- bitwise exclusive OR operator [C#]
ms.assetid: b09bc815-570f-4db6-a637-5b4ed99d014a
ms.openlocfilehash: f6f09f197502af1bc38bcdef97dd1db0ad9c7c08
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236941"
---
# <a name="-operator-c-reference"></a>Operador ^ (Referência de C#)
Os operadores binários `^` são predefinidos para os tipos integrais e `bool`. Para os tipos integrais, o `^` computa o OR exclusivo bit a bit de seus operandos. Para operandos `bool`, o `^` computa o OR exclusivo lógico de seus operandos; ou seja, o resultado será `true` se e somente se exatamente um dos operandos for `true`.  
  
## <a name="remarks"></a>Comentários  
 Os tipos definidos pelo usuário podem sobrecarregar o operador `^` (consulte [operador](../../../csharp/language-reference/keywords/operator.md)). As operações em tipos integrais geralmente são permitidas na enumeração.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csRefOperators#30](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-operator_1.cs)]  
  
 O cálculo de `0xf8 ^ 0x3f` no exemplo anterior executa um OR exclusivo bit a bit dos dois valores binários a seguir, que correspondem aos valores hexadecimais F8 e 3F:  
  
 `1111 1000`  
  
 `0011 1111`  
  
 O resultado do OR exclusivo é `1100 0111`, que é igual a C7 em hexadecimal.  
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Operadores do C#](../../../csharp/language-reference/operators/index.md)
