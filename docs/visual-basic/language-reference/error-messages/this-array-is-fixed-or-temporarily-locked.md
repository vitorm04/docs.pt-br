---
title: Esta matriz é fixa ou está temporariamente bloqueada (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: c74d9524ff64101ba6002e133b93c9b80e8f50a9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59337962"
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a>Esta matriz é fixa ou está temporariamente bloqueada (Visual Basic)
Esse erro tem as seguintes causas possíveis:  
  
-   Usando `ReDim` para alterar o número de elementos de uma matriz de tamanho fixo.  
  
-   Redimensioning uma matriz dinâmica de nível de módulo, no qual um elemento foi passado como um argumento para um procedimento. Se um elemento for passado, a matriz é bloqueada para impedir desalocando memória para o parâmetro de referência dentro do procedimento.  
  
-   Tentativa de atribuir um valor para um `Variant` variável que contém uma matriz, mas o `Variant` está bloqueado no momento.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Verifique a matriz original dinâmico e não fixados pelas declará-la com `ReDim` (se a matriz é declarada dentro de um procedimento), ou ao declará-la sem especificar o número de elementos (se a matriz é declarada no nível de módulo.  
  
2. Determine se você realmente precisa passar o elemento, já que é visível em todos os procedimentos no módulo.  
  
3. Determinar o que está bloqueando o `Variant` e corrigi-lo.  
  
## <a name="see-also"></a>Consulte também

- [Matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md)
