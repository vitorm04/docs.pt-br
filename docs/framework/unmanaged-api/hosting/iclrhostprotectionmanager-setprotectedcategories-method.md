---
title: Método ICLRHostProtectionManager::SetProtectedCategories
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager.SetProtectedCategories
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager::SetProtectedCategories
helpviewer_keywords:
- SetProtectedCategories method [.NET Framework hosting]
- ICLRHostProtectionManager::SetProtectedCategories method [.NET Framework hosting]
ms.assetid: fa21dc7b-5da7-440b-b59e-9180e5181f9d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e34c14ce9f063653c9d0018733f93e398641355
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569843"
---
# <a name="iclrhostprotectionmanagersetprotectedcategories-method"></a>Método ICLRHostProtectionManager::SetProtectedCategories
Especifica quais categorias de tipos gerenciados e membros devem ser impedidas de executar código parcialmente confiável.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetProtectedCategories (  
    [in] EApiCategories  categories  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `categories`  
 [in] Uma combinação de [EApiCategories](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md) valores, que indica quais categorias de tipos gerenciados e membros devem ser impedidas de executar código parcialmente confiável.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`SetProtectedCategories` retornado com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada atingiu o tempo limite.|  
|HOST_E_NOT_OWNER|O chamador não é proprietário do bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Depois que um método retorna E_FAIL, o CLR não é mais utilizável dentro do processo. As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Comentários  
 Cada `EApiCategories` valor refere-se a uma lista de membros e tipos gerenciados. O `EApiCategories` enumeração e a `SetProtectedCategories` método estão diretamente relacionados para o gerenciado <xref:System.Security.Permissions.HostProtectionAttribute> classe, que é usado para marcar tipos gerenciados e membros que expõem funcionalidades correspondentes às categorias descritas pelo `EApiCategories`. Para obter mais informações, consulte <xref:System.Security.Permissions.HostProtectionAttribute> e o <xref:System.Security.Permissions.HostProtectionResource> enumeração, que corresponde diretamente à `EApiCategories`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Security.Permissions.HostProtectionAttribute>
- <xref:System.Security.Permissions.HostProtectionResource>
- [Enumeração EApiCategories](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)
- [Interface ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [Interface ICLRHostProtectionManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
