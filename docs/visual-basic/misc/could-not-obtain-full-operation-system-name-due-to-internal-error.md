---
title: "Não foi possível obter o nome do sistema completo de operação devido a erro interno | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
caps.latest.revision: 9
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
ms.openlocfilehash: ed04535343c1c43d61eb47b73c431c99bd76d99d
ms.lasthandoff: 03/13/2017

---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a>Não foi possível obter o nome do sistema completo de operação devido a erro interno
Não foi possível obter o nome do sistema completo de operação devido a erro interno. Isso pode ser causado pelo WMI não existentes no computador atual.  
  
 Uma chamada para o `My.Computer.Info.OSFullName` propriedade falhou. Uma possível causa dessa falha é se o Windows Management Instrumentation (WMI) não está instalado no computador atual.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Adicionar uma `Try...Catch` em torno da chamada para o `My.Computer.Info.OSFullName` propriedade.  
  
2.  Para obter mais informações sobre o WMI e como instalá-lo, vá para e procure "Windows Management Instrumentation Core".  
  
## <a name="see-also"></a>Consulte também  
 [Propriedade My.Computer.Info.OSFullName](http://msdn.microsoft.com/en-us/b3b0fbd1-4dc5-428a-ad04-0d9fc9c2a9be)   
 [Exceção e tratamento de erros no Visual Basic](http://msdn.microsoft.com/en-us/3e351e73-cf23-40ab-8b60-05794160529e)   
 [Instrução Try...Catch...Finally](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
