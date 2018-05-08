---
title: Arquivo já aberto
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: 75a08b411a4afd7ea8e11953f1d465b082faa712
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="file-already-open"></a>Arquivo já aberto
Às vezes, um arquivo deve ser fechado antes de outro `FileOpen` ou outra operação pode ocorrer. Entre as causas possíveis desse erro são:  
  
-   Um modo de saída sequencial `FileOpen` operação foi executada para um arquivo que já está aberto  
  
-   Uma instrução faz referência a um arquivo aberto.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Feche o arquivo antes de executar a instrução.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
