---
title: Método ICLRDomainManager::SetPropertiesForDefaultAppDomain
ms.date: 03/30/2017
api_name:
- ICLRDomainManager.SetPropertiesForDefaultAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain
helpviewer_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
- SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 43e61c4b-c435-45ec-9ef6-c68403aa4200
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4c42297e848844617ffdc6c85c81846b5805eb4b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181318"
---
# <a name="iclrdomainmanagersetpropertiesfordefaultappdomain-method"></a>Método ICLRDomainManager::SetPropertiesForDefaultAppDomain
Define as propriedades que serão usadas para inicializar o domínio de aplicativo padrão.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetPropertiesForDefaultAppDomain(  
    [in] DWORD nProperties,  
    [in] LPCWSTR *pwszPropertyNames,  
    [in] LPCWSTR *pwszPropertyValues  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `nProperties`  
 [in] O número de entradas no `pwszPropertyNames` e `pwszPropertyValues`.  
  
 `pwszPropertyNames`  
 [in] Uma matriz de nomes de propriedade, ou nulo se não houver nenhuma propriedade. Atualmente, o nome da propriedade única que é reconhecido por esse método é "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".  
  
 `pwszPropertyValues`  
 [in] Uma matriz de valores de propriedade, ou nulo se não houver nenhuma propriedade.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)|`pwszPropertyNames` inclui um nome de propriedade que não é reconhecido por esse método.|  
  
## <a name="remarks"></a>Comentários  
 O valor da propriedade para "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" é uma lista de assemblies que têm a condicional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributo (APTCA) com o <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> sinalizador, que se tornarão visíveis para chamadores parcialmente confiáveis no aplicativo padrão domínio.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [Interface ICLRDomainManager](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
