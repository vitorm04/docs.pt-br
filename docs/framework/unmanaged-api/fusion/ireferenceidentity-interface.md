---
title: Interface IReferenceIdentity
ms.date: 03/30/2017
api_name:
- IReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceIdentity
helpviewer_keywords:
- IReferenceIdentity interface [.NET Framework fusion]
ms.assetid: 9180ac5a-7019-4716-9f83-8a91d157239a
topic_type:
- apiref
ms.openlocfilehash: 8f6a117d1e2fe76c271b0b014e6079370c8b4fe4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127063"
---
# <a name="ireferenceidentity-interface"></a>Interface IReferenceIdentity
Representa uma referência à assinatura exclusiva de um objeto de código.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|Obtém um ponteiro de interface para uma nova instância `IReferenceIdentity` que é idêntica a este `IReferenceIdentity`, exceto para as alterações de atributo especificadas.|  
|`IReferenceIdentity::EnumAttributes`|Obtém um ponteiro de interface para uma instância de `IEnumIDENTITY_ATTRIBUTE` que contém os atributos associados a este `IReferenceIdentity`.|  
|`IReferenceIdentity::GetAttribute`|Obtém o valor do atributo no namespace especificado, com o nome especificado.|  
|`IReferenceIdentity::SetAttribute`|Define o atributo que tem o namespace especificado e o nome especificado para o valor especificado.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** Isolamento. h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interfaces de fusão](fusion-interfaces.md)
- [Interface IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md)
