---
title: "Arquivo já aberto | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID55
dev_langs:
- VB
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
caps.latest.revision: 7
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
ms.openlocfilehash: ef8fa5ded0732193ef520b69260ac362ba335753
ms.lasthandoff: 03/13/2017

---
# <a name="file-already-open"></a>Arquivo já aberto
Às vezes, um arquivo deve ser fechado antes de outro `FileOpen` ou outra operação pode ocorrer. Entre as causas possíveis desse erro são:  
  
-   Um modo de saída sequencial `FileOpen` operação foi executada para um arquivo que já está aberto  
  
-   Uma instrução refere-se a um arquivo aberto.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Feche o arquivo antes de executar a instrução.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A></xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
