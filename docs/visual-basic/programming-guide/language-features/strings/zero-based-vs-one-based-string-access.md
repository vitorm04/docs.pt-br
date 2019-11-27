---
title: Acesso de cadeia de caracteres baseado em zero versus um
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: 97e60038bc7ec0f030939d0980b786bffebcfb9a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354295"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a>Acesso à cadeia de caracteres com base em zero versus em um no Visual Basic
Este tópico compara como Visual Basic e o .NET Framework fornecem acesso aos caracteres em uma cadeia de caracteres. O .NET Framework sempre fornece acesso baseado em zero aos caracteres em uma cadeia de caracteres, enquanto Visual Basic fornece acesso baseado em zero e um baseado em um, dependendo da função.  
  
## <a name="one-based"></a>Baseado em um  
 Para obter um exemplo de uma função de Visual Basic baseada em um, considere a função `Mid`. Ele usa um argumento que indica a posição do caractere na qual a subcadeia de caracteres será iniciada, começando com a posição 1. O método .NET Framework <xref:System.String.Substring%2A?displayProperty=nameWithType> usa um índice do caractere na cadeia de caracteres na qual a subcadeia de caracteres é iniciada, começando com a posição 0. Portanto, se você tiver uma cadeia de caracteres "ABCDE", os caracteres individuais serão numerados como 1, 2, 3, 4, 5 para uso com a função `Mid`, mas 0, 1, 2, 3, 4 para uso com o método <xref:System.String.Substring%2A?displayProperty=nameWithType>.  
  
## <a name="zero-based"></a>Baseado em zero  
 Para obter um exemplo de uma função de Visual Basic com base em zero, considere a função `Split`. Ele divide uma cadeia de caracteres e retorna uma matriz que contém as subcadeias de caracteres. O método .NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> também divide uma cadeia de caracteres e retorna uma matriz que contém as subcadeias de caracteres. Como a função `Split` e o método <xref:System.String.Split%2A> retornam .NET Framework matrizes, elas devem ser baseadas em zero.  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [Introdução às cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
