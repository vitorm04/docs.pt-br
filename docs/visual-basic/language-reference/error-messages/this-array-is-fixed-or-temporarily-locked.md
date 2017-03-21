---
title: "Essa matriz é fixa ou está temporariamente bloqueada (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID10
dev_langs:
- VB
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
caps.latest.revision: 8
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9863e286549ee752fce6fa63254b7aaa3dd9c992
ms.lasthandoff: 03/13/2017

---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a>Esta matriz é fixa ou está temporariamente bloqueada (Visual Basic)
Este erro possui as seguintes causas possíveis:  
  
-   Usando `ReDim` para alterar o número de elementos de uma matriz de tamanho fixo.  
  
-   Redimensioning uma matriz dinâmica de nível de módulo, na qual um elemento foi passado como um argumento para um procedimento. Se um elemento for passado, a matriz é bloqueada para impedir desalocando memória para o parâmetro de referência dentro do procedimento.  
  
-   Tentativa de atribuir um valor para um `Variant` variável que contém uma matriz, mas o `Variant` está bloqueado no momento.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique a matriz original dinâmico em vez de fixo por declará-la com `ReDim` (se a matriz declarada dentro de um procedimento), ou por declará-la sem especificar o número de elementos (se a matriz é declarada no nível de módulo.  
  
2.  Determine se você realmente precisa passar o elemento, já que é visível em todos os procedimentos no módulo.  
  
3.  Determinar o que está bloqueando o `Variant` e corrigi-lo.  
  
## <a name="see-also"></a>Consulte também  
 [Matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md)
