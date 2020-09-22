---
title: Arquivo já aberto
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: 97f9e13e6802e793f7c7baf1f03ec51205eb6d42
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874170"
---
# <a name="file-already-open"></a>Arquivo já aberto

Às vezes, um arquivo deve ser fechado antes que outra `FileOpen` ou outra operação possa ocorrer. Entre as possíveis causas desse erro estão:  
  
- Uma operação de modo de saída sequencial `FileOpen` foi executada para um arquivo que já está aberto  
  
- Uma instrução refere-se a um arquivo aberto.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Feche o arquivo antes de executar a instrução.  
  
## <a name="see-also"></a>Confira também

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
