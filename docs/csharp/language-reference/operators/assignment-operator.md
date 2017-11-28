---
title: "Operador = (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: =_CSharpKeyword
helpviewer_keywords: = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4c7188abe54cb69678720b4dbbf4dbdea1be4abe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>Operador = (Referência de C#)
O operador de atribuição (`=`) armazena o valor do operando direito no local de armazenamento, propriedade ou indexador indicado pelo operando esquerdo e retorna o valor como resultado. Os operandos devem ser do mesmo tipo (ou o operando direito deve ser implicitamente conversível para o tipo do operando esquerdo).  
  
## <a name="remarks"></a>Comentários  
 O operador de atribuição não pode ser sobrecarregado. No entanto, é possível definir operadores de conversão implícita para um tipo, o que permite usar o operador de atribuição com esses tipos. Para obter mais informações, consulte [Usando Operadores de Conversão](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csRefOperators#49](../../../csharp/language-reference/operators/codesnippet/CSharp/assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)
