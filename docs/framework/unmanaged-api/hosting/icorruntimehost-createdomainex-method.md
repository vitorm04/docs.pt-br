---
title: Método ICorRuntimeHost::CreateDomainEx
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomainEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomainEx
helpviewer_keywords:
- ICorRuntimeHost::CreateDomainEx method [.NET Framework hosting]
- CreateDomainEx method [.NET Framework hosting]
ms.assetid: 1bdde382-f8ba-4cc8-94b2-d1ac919c585e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e851cf16e4b23b1f8510c4d96b23c01eb726a77
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorruntimehostcreatedomainex-method"></a>Método ICorRuntimeHost::CreateDomainEx
Cria um domínio de aplicativo. O chamador recebe um ponteiro de interface do tipo <xref:System._AppDomain>, para uma instância do tipo <xref:System.AppDomain?displayProperty=nameWithType>. Esse método permite que o chamador passar uma instância de IAppDomainSetup para configurar recursos adicionais do retornado <xref:System._AppDomain> instância.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CreateDomainEx (  
    [in] LPCWSTR     pwzFriendlyName,  
    [in] IUnknown*   pSetup,  
    [in] IUnknown*   pIdentityArray,  
    [out] IUnknown** pAppDomain  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pwzFriendlyName`  
 [in] Um parâmetro opcional usado para fornecer um nome amigável para o domínio. Esse nome amigável pode ser exibida nas interfaces do usuário, como depuradores para identificar o domínio.  
  
 `pSetup`  
 [in] Um ponteiro de interface opcional do tipo `IAppDomainSetup`, obtido por uma chamada para o [Createdomainsetup](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md) método.  
  
 `pIdentityArray`  
 [in] Uma matriz opcional de ponteiros para `IIdentity` instâncias que representam a evidência mapeada por meio da política de segurança para estabelecer um conjunto de permissões. Um `IIdentity` objeto pode ser obtido chamando o [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) método.  
  
 `pAppDomain`  
 [out] Um ponteiro de interface do tipo <xref:System._AppDomain> para uma instância de <xref:System.AppDomain?displayProperty=nameWithType> que pode ser usado para controlar ainda mais o domínio.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|A operação foi bem-sucedida.|  
|S_FALSE|Falha ao concluir a operação.|  
|E_FAIL|Ocorreu uma falha catastrófica, desconhecida. Se um método retornará E_FAIL, o common language runtime (CLR) não será mais utilizável no processo. As chamadas subsequentes para hospedagem de APIs retornam HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_CLRNOTAVAILABLE|O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.|  
  
## <a name="remarks"></a>Comentários  
 `CreateDomainEx` estende os recursos do [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) , permitindo que o chamador passar um `IAppDomainSetup` instância com valores de propriedade para configurar o domínio de aplicativo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versão do .NET framework:** 1.0, 1.1  
  
## <a name="see-also"></a>Consulte também  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 <xref:System.IAppDomainSetup?displayProperty=nameWithType>  
 [Método CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)  
 [Interface ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
