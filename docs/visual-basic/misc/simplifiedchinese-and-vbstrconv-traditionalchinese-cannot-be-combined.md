---
title: "Chinês simplificado e TraditionalChinese não podem ser combinados | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrArgument_StrConvSCandTC
ms.assetid: d8e6a11b-f549-43b5-8337-0594340e1325
caps.latest.revision: 10
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 57ab14cdcb3e4b27e821097dcfca4d97e1633035
ms.lasthandoff: 03/13/2017

---
# <a name="simplifiedchinese-and-vbstrconvtraditionalchinese-cannot-be-combined"></a>Chinês simplificado e TraditionalChinese não podem ser combinados
Seu aplicativo está tentando combinar o `VbStrConv` membros de enumeração `SimplifiedChinese` e `TraditionalChinese`, que são mutuamente exclusivos.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Remova `VbStrConv.SimplifiedChinese` ou `VbStrConv.TraditionalChinese`.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Globalization>   
 [NOTINBUILD VbStrConv Enumeration](http://msdn.microsoft.com/en-us/59f83dd9-6361-47df-a836-02ba9d4cb936)   
 [Introdução a aplicativos internacionais com base no .NET Framework](https://docs.microsoft.com/visualstudio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)
