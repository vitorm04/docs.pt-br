---
title: Esta matriz é fixa ou está temporariamente bloqueada (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: e912bd202603d9a0f427418708ad584c7d6203e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593558"
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a>Esta matriz é fixa ou está temporariamente bloqueada (Visual Basic)
Esse erro tem as seguintes causas possíveis:  
  
-   Usando `ReDim` para alterar o número de elementos de uma matriz de tamanho fixo.  
  
-   Redimensioning uma matriz de dinâmica de nível de módulo, em que um elemento foi passado como um argumento para um procedimento. Se um elemento for passado, a matriz está bloqueada para impedir desalocando memória para o parâmetro de referência dentro do procedimento.  
  
-   Tentativa de atribuir um valor para um `Variant` variável que contém uma matriz, mas o `Variant` está bloqueado no momento.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique a matriz original dinâmico, em vez de pela declará-la com `ReDim` (se a matriz declarada dentro de um procedimento), ou por declará-la sem especificar o número de elementos (se a matriz é declarada no nível de módulo.  
  
2.  Determine se você realmente precisar passar o elemento, pois ela é visível em todos os procedimentos no módulo.  
  
3.  Determinar o que está bloqueando o `Variant` e corrigi-lo.  
  
## <a name="see-also"></a>Consulte também  
 [Matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md)
