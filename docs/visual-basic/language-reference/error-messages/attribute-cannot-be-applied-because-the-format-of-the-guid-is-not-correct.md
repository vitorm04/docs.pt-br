---
title: "'<attribute>' não pode ser aplicado porque o formato da GUID '<number>' não está correto"
ms.date: 07/20/2015
f1_keywords:
- vbc32500
- bc32500
helpviewer_keywords:
- BC32500
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
ms.openlocfilehash: 1e92c77e6138bbd546d9b837e095e41d5dfaf30c
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55279858"
---
# <a name="attribute-cannot-be-applied-because-the-format-of-the-guid-number-is-not-correct"></a>'\<atributo >' não pode ser aplicado porque o formato da GUID '\<número >' não está correto
Um `COMClassAttribute` bloco de atributo especifica um identificador global exclusivo (GUID) que não corresponde ao formato adequado para um GUID. `COMClassAttribute` usa GUIDs para identificar exclusivamente a classe, a interface e o evento de criação.  
  
 Um GUID consiste em 16 bytes, dos quais os oito primeiros são numéricos e os oito últimos são binários. Ele é gerado pelo utilitários da Microsoft, como uuidgen.exe e é garantido que seja exclusivo no espaço e tempo.  
  
 **ID do erro:** BC32500  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Determine o GUID correto ou GUIDs necessários para identificar o objeto COM.  
  
2.  Certifique-se de que as cadeias de caracteres GUID apresentadas para o `COMClassAttribute` bloco de atributo são copiados corretamente.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Guid>
- [Visão geral de atributos](../../../visual-basic/programming-guide/concepts/attributes/index.md)

