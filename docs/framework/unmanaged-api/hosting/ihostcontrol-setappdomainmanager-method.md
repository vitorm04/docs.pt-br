---
title: Método IHostControl::SetAppDomainManager
ms.date: 03/30/2017
api_name:
- IHostControl.SetAppDomainManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl::SetAppDomainManager
helpviewer_keywords:
- IHostControl::SetAppDomainManager method [.NET Framework hosting]
- SetAppDomainManager method [.NET Framework hosting]
ms.assetid: 6562bbe7-0d67-4c50-a958-3a18cf680375
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bb63f1e9d2b30ce764521aa68fbafe0407cbe922
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441868"
---
# <a name="ihostcontrolsetappdomainmanager-method"></a>Método IHostControl::SetAppDomainManager
Notifica o host que um domínio de aplicativo foi criado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetAppDomainManager (  
    [in] DWORD     dwAppDomainID,  
    [in] IUnknown* pUnkAppDomainManager  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwAppDomainID`  
 [in] O identificador numérico do selecionado <xref:System.AppDomain>.  
  
 `pUnkAppDomainManager`  
 [in] Um ponteiro para o <xref:System.AppDomainManager> objeto que implementa o host como `IUnknown`.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`SetAppDomainManager` retornou com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada foi atingido.|  
|HOST_E_NOT_OWNER|O chamador não possui o bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo. As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Comentários  
 O <xref:System.AppDomainManager> fornece um mecanismo para inicializar em código gerenciado e controlar a criação e as configurações de cada host <xref:System.AppDomain>. O <xref:System.AppDomainManager> é carregado em cada <xref:System.AppDomain> quando que <xref:System.AppDomain> é criado. Se ele escolhe, o CLR notifica o host que o domínio de aplicativo foi criado, definindo o valor da `pUnkAppDomainManager` parâmetro.  
  
 Em sua implementação do `SetAppDomainManager` método, o host pode definir o nome do assembly e o tipo para o Gerenciador de domínio de aplicativo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.AppDomain>  
 <xref:System.AppDomainManager>  
 [Interface IHostControl](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
