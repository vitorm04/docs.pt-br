---
title: "A função &quot;Dir&quot; deve ser chamada primeiro com um argumento &quot;PathName&quot; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrDIR_IllegalCall
dev_langs:
- VB
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
caps.latest.revision: 7
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 9df0fbb1fcd3b588c1c256b6f76e336d7968935c
ms.lasthandoff: 03/13/2017

---
# <a name="39dir39-function-must-first-be-called-with-a-39pathname39-argument"></a>A função 'Dir' deve ser chamada primeiro com um argumento 'PathName'
Uma chamada inicial para o `Dir` função não inclui o `PathName` argumento. A primeira chamada para `Dir` deve incluir uma `PathName`, mas subsequentes chamadas para `Dir` não precisa incluir parâmetros para recuperar o próximo item.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Forneça um `PathName` argumento na chamada de função.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.FileSystem.Dir%2A></xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
