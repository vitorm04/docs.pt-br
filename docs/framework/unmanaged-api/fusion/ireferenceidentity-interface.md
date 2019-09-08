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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2bb151d7c77104d8e24acefaac2e1f109b67f168
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796364"
---
# <a name="ireferenceidentity-interface"></a>Interface IReferenceIdentity
Representa uma referência à assinatura exclusiva de um objeto de código.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|Obtém um ponteiro de interface para uma `IReferenceIdentity` nova instância que é idêntica a `IReferenceIdentity`isso, exceto para as alterações de atributo especificadas.|  
|`IReferenceIdentity::EnumAttributes`|Obtém um ponteiro de interface para `IEnumIDENTITY_ATTRIBUTE` uma instância que contém os atributos associados a `IReferenceIdentity`isso.|  
|`IReferenceIdentity::GetAttribute`|Obtém o valor do atributo no namespace especificado, com o nome especificado.|  
|`IReferenceIdentity::SetAttribute`|Define o atributo que tem o namespace especificado e o nome especificado para o valor especificado.|  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** Isolamento. h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interfaces de fusão](fusion-interfaces.md)
- [Interface IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md)
