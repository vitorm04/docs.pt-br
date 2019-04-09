---
title: Enumeração EInitializeNewDomainFlags
ms.date: 03/30/2017
api_name:
- EInitializeNewDomainFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EInitializeNewDomainFlags
helpviewer_keywords:
- EInitializeNewDomainFlags enumeration [.NET Framework hosting]
ms.assetid: 3a120ab2-f5ef-4c9b-8595-d3ed7247c342
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 04b0d9989d66888c33de0359e4c93529fcfbf8d1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095354"
---
# <a name="einitializenewdomainflags-enumeration"></a>Enumeração EInitializeNewDomainFlags
Permite que o host fornecer o tempo de execução com informações sobre a inicialização de um domínio de aplicativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|Sem sinalizadores.|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|Informa o common language runtime (CLR) que o host não fará alterações para o estado de segurança do domínio do aplicativo na <xref:System.AppDomainManager.InitializeNewDomain%2A> método.|  
  
## <a name="remarks"></a>Comentários  
 O [iclrdomainmanager:: Setappdomainmanagertype](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) método utiliza um parâmetro de tipo `EInitializeNewDomainFlags`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Hospedando enumerações](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [Método SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)
