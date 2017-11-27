---
title: Com base em zero vs. Acesso com base em uma cadeia de caracteres no Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 911f063d6ca9a3f5d88a1f50d9df7f908a488f66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a>Com base em zero vs. Acesso com base em uma cadeia de caracteres no Visual Basic
Este tópico compara como [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] e [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] fornecem acesso aos caracteres em uma cadeia de caracteres. O [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sempre fornece acesso baseado em zero aos caracteres em uma cadeia de caracteres, enquanto [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] fornece acesso baseado em zero e um, dependendo da função.  
  
## <a name="one-based"></a>Baseado em um  
 Para obter um exemplo de uma base de um [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] funcionar, considere o `Mid` função. Ela tem um argumento que indica a posição do caractere no qual a subcadeia de caracteres será iniciada, começando pela posição 1. O [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Substring%2A?displayProperty=nameWithType> método utiliza um índice de caractere na cadeia de caracteres na qual a subcadeia de caracteres é iniciada, começando pela posição 0. Portanto, se você tiver uma cadeia de caracteres "ABCDE", os caracteres individuais são numerados 1,2,3,4,5 para uso com o `Mid` função, mas 0,1,2,3,4 para uso com o <xref:System.String.Substring%2A?displayProperty=nameWithType> método.  
  
## <a name="zero-based"></a>Com base em zero  
 Para obter um exemplo de uma base zero [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] funcionar, considere o `Split` função. Ele divide uma cadeia de caracteres e retorna uma matriz que contém as subcadeias de caracteres. O [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Split%2A?displayProperty=nameWithType> método também divide uma cadeia de caracteres e retorna uma matriz que contém as subcadeias de caracteres. Porque o `Split` função e <xref:System.String.Split%2A> retorno do método [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] matrizes, eles devem ser com base em zero.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>  
 <xref:Microsoft.VisualBasic.Strings.Split%2A>  
 <xref:System.String.Substring%2A>  
 <xref:System.String.Split%2A>  
 [Introdução às cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
