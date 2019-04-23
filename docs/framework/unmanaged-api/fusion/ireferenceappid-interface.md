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
ms.openlocfilehash: 25733e459423500352595d6be0eee26ef75ca7e2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59157190"
---
# <a name="ireferenceappid-interface"></a>Interface IReferenceAppId
Representa uma referência para o identificador exclusivo para o aplicativo no escopo atual.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|Obtém um ponteiro para uma representação de cadeia de caracteres do identificador de código para o aplicativo referenciado por este `IReferenceAppId`.|  
|`IReferenceAppId::put_CodeBase`|Define o identificador de código para o aplicativo referenciado por este `IReferenceAppId`.|  
|`IReferenceAppId::EnumAppPath`|Obtém um ponteiro de interface para um `IEnumReferenceIdentity` instância que contém o `IReferenceIdentity` instâncias que representam os membros deste `IReferenceAppId`.|  
|`IReferenceAppId::get_SubscriptionId`|Obtém um ponteiro para uma representação de cadeia de caracteres do identificador de token para uma assinatura a este `IReferenceAppId`.|  
|`IReferenceAppId::put_SubscriptionId`|Define o identificador de token para uma assinatura para essa `IReferenceAppId` para o valor de cadeia de caracteres especificada.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Isolation.h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interfaces de fusão](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [Interface IEnumReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)
- [Interface IReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
