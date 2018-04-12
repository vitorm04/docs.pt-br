---
title: Arquivo já aberto
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3305831e840510e3f0b5bcb8bf847e39ea3ee4ba
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="file-already-open"></a>Arquivo já aberto
Às vezes, um arquivo deve ser fechado antes de outro `FileOpen` ou outra operação pode ocorrer. Entre as causas possíveis desse erro são:  
  
-   Um modo de saída sequencial `FileOpen` operação foi executada para um arquivo que já está aberto  
  
-   Uma instrução faz referência a um arquivo aberto.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Feche o arquivo antes de executar a instrução.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
