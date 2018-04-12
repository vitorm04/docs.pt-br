---
title: Entrada passou do final do arquivo
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID62
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 27de462d5d28ee09107d75afe8269e7401c4dc39
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="input-past-end-of-file"></a>Entrada passou do final do arquivo
Qualquer um `Input` instrução está lendo de um arquivo que está vazio ou um no qual todos os dados é usado, ou você usou o `EOF` função com um arquivo aberto para acesso binário.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Use o `EOF` função imediatamente antes do `Input` instrução para detectar o final do arquivo.  
  
2.  Se o arquivo é aberto para acesso binário, use `Seek` e `Loc`.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.FileSystem.Input%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.EOF%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.Seek%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.Loc%2A>
