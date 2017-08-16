---
title: "Instruções &quot;Module&quot; só podem ocorrer no nível de namespace ou arquivo | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30617
- vbc30617
dev_langs:
- VB
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
caps.latest.revision: 8
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
ms.openlocfilehash: cefce3ea6222232d830d74a3836fcc43ea1e6604
ms.lasthandoff: 03/13/2017

---
# <a name="39module39-statements-can-occur-only-at-file-or-namespace-level"></a>Instruções 'Module' só podem ocorrer no nível de namespace ou arquivo
`Module`instruções devem aparecer na parte superior do seu arquivo de origem imediatamente após `Option` e `Imports` instruções, atributos globais e declarações de namespace, mas antes de todas as outras declarações.  
  
 **ID do erro:** BC30617  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Mova o `Module` instrução na parte superior do seu arquivo de origem ou de declaração namespace.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Module](../../../visual-basic/language-reference/statements/module-statement.md)
