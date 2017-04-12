---
title: "Instruções &quot;Line&quot; não são mais compatíveis (erro do compilador Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30830
- vbc30830
dev_langs:
- VB
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
caps.latest.revision: 11
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
ms.openlocfilehash: fca2b3cae88f503f838c2c90554b0ca7ee004ea8
ms.lasthandoff: 03/13/2017

---
# <a name="39line39-statements-are-no-longer-supported-visual-basic-compiler-error"></a>Instruções 'Line' não são mais compatíveis (erro do compilador Visual Basic)
Não há suporte para instruções de linha. A funcionalidade de e/s de arquivo está disponível como `Microsoft.VisualBasic.FileSystem.LineInput` e funcionalidade de elementos gráficos está disponível como `System.Drawing.Graphics.DrawLine`.  
  
 **ID do erro:** BC30830  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Se executar o acesso a arquivos, use `Microsoft.VisualBasic.FileSystem.LineInput`.  
  
2.  Se executar gráficos, use `System.Drawing.Graphics.Drawline`.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IO></xref:System.IO>   
 <xref:System.Drawing></xref:System.Drawing>   
 [Access de arquivo com o Visual Basic](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
