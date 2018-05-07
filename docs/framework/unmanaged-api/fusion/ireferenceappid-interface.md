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
ms.openlocfilehash: 2484fa61c03b95e7cbdb452b92a68a2049701374
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="ireferenceappid-interface"></a>Interface IReferenceAppId
Representa uma referência para o identificador exclusivo para o aplicativo no escopo atual.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|Obtém um ponteiro para uma representação de cadeia de caracteres do identificador de código para o aplicativo referenciado por este `IReferenceAppId`.|  
|`IReferenceAppId::put_CodeBase`|Define o identificador de código para o aplicativo referenciado por este `IReferenceAppId`.|  
|`IReferenceAppId::EnumAppPath`|Obtém um ponteiro de interface para um `IEnumReferenceIdentity` instância que contém o `IReferenceIdentity` instâncias que representam os membros deste `IReferenceAppId`.|  
|`IReferenceAppId::get_SubscriptionId`|Obtém um ponteiro para uma representação de cadeia de caracteres do identificador de token para uma assinatura para este `IReferenceAppId`.|  
|`IReferenceAppId::put_SubscriptionId`|Define o identificador para uma assinatura de token para este `IReferenceAppId` para o valor de cadeia de caracteres especificada.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Isolation.h  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de fusão](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [Interface IEnumReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)  
 [Interface IReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
