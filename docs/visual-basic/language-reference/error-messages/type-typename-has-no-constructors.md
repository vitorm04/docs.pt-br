---
title: "Tipo de &quot;&lt;typename&gt;&quot; não tem construtores | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30251
- vbc30251
dev_langs:
- VB
helpviewer_keywords:
- BC30251
ms.assetid: aff3e1df-abe6-4bc0-9abc-a1e70514c561
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 505e3bbdfa830394efcea7226897ec0d3e6d2b02
ms.lasthandoff: 03/13/2017

---
# <a name="type-39lttypenamegt39-has-no-constructors"></a>Tipo de '&lt;typename&gt;' não tem construtores
Um tipo não suporta uma chamada para `Sub New()`. Uma possível causa é um compilador corrompido ou arquivo binário.  
  
 **ID do erro:** BC30251  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Se o tipo estiver em um projeto diferente ou em um arquivo referenciado, reinstale o projeto ou arquivo.  
  
2.  Se o tipo estiver no mesmo projeto, recompile o assembly que contém o tipo.  
  
3.  Se o erro persistir, reinstale o compilador [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
4.  Se o erro persistir, reúna informações sobre as circunstâncias e notifique o Microsoft Product Support Services.  
  
## <a name="see-also"></a>Consulte também  
 [Objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [Fale conosco](https://docs.microsoft.com/visualstudio/ide/talk-to-us)
