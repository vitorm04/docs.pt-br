---
title: Interface IDefinitionAppId
ms.date: 03/30/2017
api_name:
- IDefinitionAppId
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDefinitionAppId
helpviewer_keywords:
- IDefinitionAppId interface [.NET Framework fusion]
ms.assetid: e72f2550-bdec-4a20-a2f4-2e14847266c1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2735355097a1f3f581b3a4bc74f08d8f2ebf3bd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430374"
---
# <a name="idefinitionappid-interface"></a>Interface IDefinitionAppId
Representa um identificador exclusivo para o código que define o aplicativo no escopo atual.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|Obtém uma cadeia de caracteres formatada que representa o código neste `IDefinitionAppId` objeto.|  
|`IDefinitionAppId::put_Codebase`|Define o código deste `IDefinitionAppId` objeto especificado formatado valor de cadeia de caracteres.|  
|`IDefinitionAppId::EnumAppPath`|Obtém um ponteiro de interface para um [IEnumDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md) objeto que contém os assemblies no caminho do aplicativo atual.|  
|`IDefinitionAppId::SetAppPath`|Define o caminho do aplicativo para o assembly no escopo atual com o valor referenciado por especificado [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) objeto.|  
|`IDefinitionAppId::get_SubscriptionId`|Obtém um ponteiro para uma representação de cadeia de caracteres do identificador de token para uma assinatura `IDefinitionAppId` objeto.|  
|`IDefinitionAppId::put_SubscriptionId`|Define o identificador para uma assinatura de token para este `IDefinitionAppId` objeto para o valor de cadeia de caracteres especificada.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Isolation.h  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de fusão](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
