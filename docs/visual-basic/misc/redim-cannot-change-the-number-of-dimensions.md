---
title: "&quot;ReDim&quot; não pode alterar o número de dimensões | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 04ecba253c66a255ff4a97e660f3d7271fce10a1
ms.lasthandoff: 03/13/2017

---
# <a name="39redim39-cannot-change-the-number-of-dimensions"></a>'ReDim' não pode alterar o número de dimensões
Uma operação tenta usar o `ReDim` instrução para alterar a classificação (número de dimensões) de uma matriz. `ReDim`pode alterar o tamanho de uma ou mais dimensões de um array que já foi formalmente declarado, mas ele não pode alterar o posto de um array.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Certifique-se de que você pretende alterar o posto do array e não os tamanhos das suas dimensões e se possível, use `Dim` para declarar um novo array com o posto desejado.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral NOTINBUILD de matrizes no Visual Basic](http://msdn.microsoft.com/en-us/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)   
 [NOTINBUILD matrizes multidimensionais no Visual Basic](http://msdn.microsoft.com/en-us/d92cad25-07e2-4d79-8ea4-ab269700f5de)   
 [Instrução reDim](../../visual-basic/language-reference/statements/redim-statement.md)   
 [Instrução Dim](../../visual-basic/language-reference/statements/dim-statement.md)
