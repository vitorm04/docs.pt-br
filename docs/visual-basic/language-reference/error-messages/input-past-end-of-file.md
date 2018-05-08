---
title: Entrada passou do final do arquivo
ms.date: 07/20/2015
f1_keywords:
- vbrID62
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
ms.openlocfilehash: abd5f5c6e5df262d1deadd74f0a146a8d436ceb3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
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
