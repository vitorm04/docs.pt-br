---
title: Arquivo já aberto
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: e565dbd6352a8f76290f3f58d62e2e14a18ef45f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58823500"
---
# <a name="file-already-open"></a>Arquivo já aberto
Às vezes, um arquivo deve ser fechado antes da outra `FileOpen` ou outra operação pode ocorrer. Entre as causas possíveis desse erro são:  
  
-   Um modo de saída sequencial `FileOpen` operação foi executada para um arquivo que já está aberto  
  
-   Uma declaração se refere a um arquivo aberto.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Feche o arquivo antes de executar a instrução.  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
