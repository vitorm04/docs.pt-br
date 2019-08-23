---
title: Método ICLRDomainManager::SetAppDomainManagerType
ms.date: 03/30/2017
api_name:
- ICLRDomainManager.SetAppDomainManagerType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRDomainManager interface [.NET Framework hosting]
- ICLRDomainManager::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ee91abb0-cb74-41dd-927b-e117fb8ffdf4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9b142f1a05036eddf44c69d8b7da95091dc8f445
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963089"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a>Método ICLRDomainManager::SetAppDomainManagerType
Especifica o tipo, derivado da <xref:System.AppDomainManager?displayProperty=nameWithType> classe, do Gerenciador de domínio de aplicativo que será usado para inicializar o domínio de aplicativo padrão.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `wszAppDomainManagerAssembly`  
 no O nome de exibição do assembly que contém o tipo de Gerenciador de domínio do aplicativo; por exemplo: "AdMgrExample, Version = 1.0.0.0, Culture = neutral, PublicKeyToken = 6856bccf150f00b3".  
  
 `wszAppDomainManagerType`  
 no O nome do tipo do Gerenciador de domínio do aplicativo, incluindo o namespace.  
  
 `dwInitializeDomainFlags`  
 no Uma combinação de valores de enumeração [EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) que fornecem informações sobre o Gerenciador de domínio do aplicativo.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.|  
  
## <a name="remarks"></a>Comentários  
 Atualmente, o único valor definido para `dwInitializeDomainFlags` é `eInitializeNewDomainFlags_NoSecurityChanges`, que informa ao Common Language Runtime (CLR) que o Gerenciador de domínio do aplicativo não modificará as configurações de segurança <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> durante a execução do método. Isso permite que o CLR Otimize o carregamento de assemblies que têm o atributo <xref:System.Security.AllowPartiallyTrustedCallersAttribute> condicional (APTCA). Isso pode resultar em uma melhoria significativa no tempo de inicialização se o fechamento transitivo desse conjunto de assemblies for grande.  
  
> [!IMPORTANT]
> Se o host especificar `eInitializeNewDomainFlags_NoSecurityChanges` o Gerenciador de domínio do aplicativo, <xref:System.InvalidOperationException> um será gerado se qualquer tentativa for feita para modificar a segurança do domínio do aplicativo.  
  
 Chamar o método [ICLRControl:: SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)é equivalente a chamar `ICLRDomainManager::SetAppDomainManagerType` with `eInitializeNewDomainFlags_None`.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost.h  
  
 **Biblioteca** Incluído como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [Interface ICLRDomainManager](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
- [Enumeração EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
