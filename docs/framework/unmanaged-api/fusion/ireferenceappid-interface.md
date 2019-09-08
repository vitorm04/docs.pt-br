---
title: Interface IReferenceAppId
ms.date: 03/30/2017
api_name:
- IReferenceAppId
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceAppId
helpviewer_keywords:
- IReferenceAppId interface [.NET Framework fusion]
ms.assetid: 8eb9e565-f358-43ce-900e-a8f8a5aa6cfb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 522ed80f161f114af25e1fa7ad041c8238073d6f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796373"
---
# <a name="ireferenceappid-interface"></a>Interface IReferenceAppId
Representa uma referência ao identificador exclusivo para o aplicativo no escopo atual.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|Obtém um ponteiro para uma representação de cadeia de caracteres do identificador de código para o aplicativo `IReferenceAppId`referenciado por isso.|  
|`IReferenceAppId::put_CodeBase`|Define o identificador de código para o aplicativo referenciado `IReferenceAppId`por isso.|  
|`IReferenceAppId::EnumAppPath`|Obtém um ponteiro de interface para `IEnumReferenceIdentity` uma instância que `IReferenceIdentity` contém as instâncias `IReferenceAppId`que representam os membros desse.|  
|`IReferenceAppId::get_SubscriptionId`|Obtém um ponteiro para uma representação de cadeia de caracteres do identificador de token para uma `IReferenceAppId`assinatura para isso.|  
|`IReferenceAppId::put_SubscriptionId`|Define o identificador de token para uma assinatura para `IReferenceAppId` o valor da cadeia de caracteres especificada.|  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** Isolamento. h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interfaces de fusão](fusion-interfaces.md)
- [Interface IEnumReferenceIdentity](ienumreferenceidentity-interface.md)
- [Interface IReferenceIdentity](ireferenceidentity-interface.md)
