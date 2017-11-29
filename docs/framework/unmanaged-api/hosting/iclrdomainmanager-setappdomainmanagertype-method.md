---
title: "Método ICLRDomainManager::SetAppDomainManagerType"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDomainManager.SetAppDomainManagerType
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDomainManager::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRDomainManager interface [.NET Framework hosting]
- ICLRDomainManager::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ee91abb0-cb74-41dd-927b-e117fb8ffdf4
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 17c99d21155d8f985ea455e171067855edcafedc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a>Método ICLRDomainManager::SetAppDomainManagerType
Especifica o tipo derivado de <xref:System.AppDomainManager?displayProperty=nameWithType> classe do Gerenciador de domínio de aplicativo que será usado para inicializar o domínio de aplicativo padrão.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `wszAppDomainManagerAssembly`  
 [in] O nome para exibição do assembly que contém o tipo de Gerenciador de domínio de aplicativo; Por exemplo: "AdMgrExample, Version = 1.0.0.0, Culture = neutral, PublicKeyToken = 6856bccf150f00b3".  
  
 `wszAppDomainManagerType`  
 [in] O nome do tipo de Gerenciador de domínio de aplicativo, incluindo o namespace.  
  
 `dwInitializeDomainFlags`  
 [in] Uma combinação de [EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) valores de enumeração que fornecem informações sobre o Gerenciador de domínio de aplicativo.  
  
## <a name="return-value"></a>Valor de retorno  
 Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.|  
  
## <a name="remarks"></a>Comentários  
 No momento, o único valor definido para `dwInitializeDomainFlags` é `eInitializeNewDomainFlags_NoSecurityChanges`, que informa o common language runtime (CLR) que o Gerenciador de domínio de aplicativo não modificará as configurações de segurança durante a execução de <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> método. Isso permite que o CLR otimizar o carregamento de assemblies que têm a condicional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributo (APTCA). Se o fechamento transitivo deste conjunto de módulos (assemblies) for grande, isso pode resultar em um aprimoramento significativo no tempo de inicialização.  
  
> [!IMPORTANT]
>  Se o host especifica `eInitializeNewDomainFlags_NoSecurityChanges` para o Gerenciador de domínio de aplicativo, um <xref:System.InvalidOperationException> será lançada se qualquer tentativa de modificar a segurança do domínio do aplicativo.  
  
 Chamando o [: Setappdomainmanagertype](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)método é equivalente a chamar `ICLRDomainManager::SetAppDomainManagerType` com `eInitializeNewDomainFlags_None`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [Interface ICLRDomainManager](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 [Enumeração EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
