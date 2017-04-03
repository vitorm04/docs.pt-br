---
title: "Operador = (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- =_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6df8ffe448c45ccc83ef9de23c564a40661707c6
ms.lasthandoff: 03/13/2017

---
# <a name="-operator-c-reference"></a>Operador = (Referência de C#)
O operador de atribuição (`=`) armazena o valor do operando direito no local de armazenamento, propriedade ou indexador indicado pelo operando esquerdo e retorna o valor como resultado. Os operandos devem ser do mesmo tipo (ou o operando direito deve ser implicitamente conversível para o tipo do operando esquerdo).  
  
## <a name="remarks"></a>Comentários  
 O operador de atribuição não pode ser sobrecarregado. No entanto, é possível definir operadores de conversão implícita para um tipo, o que permite usar o operador de atribuição com esses tipos. Para obter mais informações, consulte [Usando Operadores de Conversão](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).  
  
## <a name="example"></a>Exemplo  
 [!code-cs[csRefOperators#49](../../../csharp/language-reference/operators/codesnippet/CSharp/assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)
