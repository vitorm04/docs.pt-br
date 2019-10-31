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
ms.openlocfilehash: 6f20fb2e9e026253fb02b47dfcd63cf655acc4ee
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131655"
---
# <a name="ireferenceappid-interface"></a>Interface IReferenceAppId
Representa uma referência ao identificador exclusivo para o aplicativo no escopo atual.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|Obtém um ponteiro para uma representação de cadeia de caracteres do identificador de código para o aplicativo referenciado por este `IReferenceAppId`.|  
|`IReferenceAppId::put_CodeBase`|Define o identificador de código para o aplicativo referenciado por este `IReferenceAppId`.|  
|`IReferenceAppId::EnumAppPath`|Obtém um ponteiro de interface para uma instância de `IEnumReferenceIdentity` que contém as instâncias de `IReferenceIdentity` que representam os membros dessa `IReferenceAppId`.|  
|`IReferenceAppId::get_SubscriptionId`|Obtém um ponteiro para uma representação de cadeia de caracteres do identificador de token para uma assinatura para essa `IReferenceAppId`.|  
|`IReferenceAppId::put_SubscriptionId`|Define o identificador de token para uma assinatura para essa `IReferenceAppId` para o valor da cadeia de caracteres especificada.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** Isolamento. h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interfaces de fusão](fusion-interfaces.md)
- [Interface IEnumReferenceIdentity](ienumreferenceidentity-interface.md)
- [Interface IReferenceIdentity](ireferenceidentity-interface.md)
