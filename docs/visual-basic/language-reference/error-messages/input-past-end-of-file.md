---
title: Entrada passou do final do arquivo
ms.date: 07/20/2015
f1_keywords:
- vbrID62
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
ms.openlocfilehash: 5da14c7a28ecdcd023fc6439cb6ed64444c1183b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013784"
---
# <a name="input-past-end-of-file"></a>Entrada passou do final do arquivo
Qualquer um `Input` instrução está lendo de um arquivo que está vazio ou um em que todos os dados é usado, ou você tiver usado o `EOF` função com um arquivo aberto para acesso binário.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Use o `EOF` funcionar imediatamente antes do `Input` instrução para detectar o final do arquivo.  
  
2. Se o arquivo é aberto para acesso binário, use `Seek` e `Loc`.  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.FileSystem.Input%2A>
- <xref:Microsoft.VisualBasic.FileSystem.EOF%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Seek%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Loc%2A>
