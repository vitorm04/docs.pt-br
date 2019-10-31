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
ms.openlocfilehash: 5c61e2e1208cec0bda1492964a8d02bd71f5a1c6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129327"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a>Método ICLRDomainManager::SetAppDomainManagerType
Especifica o tipo, derivado da classe <xref:System.AppDomainManager?displayProperty=nameWithType>, do Gerenciador de domínio do aplicativo que será usado para inicializar o domínio do aplicativo padrão.  
  
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
  
## <a name="return-value"></a>Valor retornado  
 Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.|  
  
## <a name="remarks"></a>Comentários  
 Atualmente, o único valor definido para `dwInitializeDomainFlags` é `eInitializeNewDomainFlags_NoSecurityChanges`, que informa ao Common Language Runtime (CLR) que o Gerenciador de domínio do aplicativo não modificará as configurações de segurança durante a execução do método <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType>. Isso permite que o CLR Otimize o carregamento de assemblies que têm o atributo APTCA (<xref:System.Security.AllowPartiallyTrustedCallersAttribute> condicional). Isso pode resultar em uma melhoria significativa no tempo de inicialização se o fechamento transitivo desse conjunto de assemblies for grande.  
  
> [!IMPORTANT]
> Se o host especificar `eInitializeNewDomainFlags_NoSecurityChanges` para o Gerenciador de domínio do aplicativo, um <xref:System.InvalidOperationException> será gerado se qualquer tentativa for feita para modificar a segurança do domínio do aplicativo.  
  
 Chamar o método [ICLRControl:: SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)é equivalente a chamar `ICLRDomainManager::SetAppDomainManagerType` com `eInitializeNewDomainFlags_None`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost. h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [Interface ICLRDomainManager](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
- [Enumeração EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
