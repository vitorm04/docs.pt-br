---
title: "Operador ++ (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ++_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
caps.latest.revision: 18
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: bee872ba489739149dacc777b776072a22306ddb
ms.lasthandoff: 03/13/2017

---
# <a name="-operator-c-reference"></a>Operador ++ (Referência de C#)
O operador de incremento (`++`) incrementa seu operando em 1. O operador de incremento pode ser exibido antes ou depois de seu operando: `++variable` e `variable++`.  
  
## <a name="remarks"></a>Comentários  
 A primeira forma é uma operação de incremento de prefixo. O resultado da operação será o valor do operando "depois" que ele for incrementado.  
  
 A segunda forma é uma operação de incremento pós-fixada. O resultado da operação será o valor do operando antes de ser incrementado.  
  
 Tipos numéricos e de enumeração têm operadores de incremento predefinidos. Os tipos definidos pelo usuário podem sobrecarregar o operador `++`. As operações em tipos integrais geralmente são permitidas na enumeração.  
  
## <a name="example"></a>Exemplo  
 [!code-cs[csRefOperators#3](../../../csharp/language-reference/operators/codesnippet/CSharp/increment-operator_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)
