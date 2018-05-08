---
title: Método ICorRuntimeHost::CreateDomain
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomain
helpviewer_keywords:
- CreateDomain method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomain method [.NET Framework hosting]
ms.assetid: b96c5ef3-a9df-4c7c-9952-432d3272cb5c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea2353f1375667619db47ac5e1f037ce68dbded5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorruntimehostcreatedomain-method"></a>Método ICorRuntimeHost::CreateDomain
Cria um domínio de aplicativo. O chamador recebe um ponteiro de interface do tipo <xref:System._AppDomain> para uma instância do tipo <xref:System.AppDomain?displayProperty=nameWithType>.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CreateDomain (  
    [in] LPWSTR    pwzFriendlyName,  
    [in] IUnknown* pIdentityArray,  
    [out] void   **pAppDomain  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pwzFriendlyName`  
 [in] Um parâmetro opcional usado para fornecer um nome amigável para o domínio. Esse nome amigável pode ser exibida nas interfaces do usuário, como depuradores para identificar o domínio.  
  
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
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** 1.0, 1.1  
  
## <a name="see-also"></a>Consulte também  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [Interface ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
