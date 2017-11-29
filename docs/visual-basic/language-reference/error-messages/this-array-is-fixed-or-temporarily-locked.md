---
title: "Esta matriz é fixa ou está temporariamente bloqueada (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: adff10d4ae61e45402df64ebaa3baf146371ff9e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
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
