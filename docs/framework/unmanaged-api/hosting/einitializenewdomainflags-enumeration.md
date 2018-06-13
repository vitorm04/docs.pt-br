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
ms.openlocfilehash: 0175ab1d06a8166a5bbfd0c42018085a801740f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431443"
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
|`eInitializeNewDomainFlags_NoSecurityChanges`|Informa o common language runtime (CLR) que o host não fará alterações para o estado de segurança do domínio do aplicativo no <xref:System.AppDomainManager.InitializeNewDomain%2A> método.|  
  
## <a name="remarks"></a>Comentários  
 O [Iclrdomainmanager](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) método usa um parâmetro do tipo `EInitializeNewDomainFlags`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
 [Método SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)
