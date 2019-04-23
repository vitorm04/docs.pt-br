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
ms.openlocfilehash: 118e75cb28a4e474427f35f4516ec41850ebe99f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59150859"
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
  
## <a name="parameters"></a>Parâmetros  
 `dwAppDomainID`  
 [in] O identificador numérico do selecionado <xref:System.AppDomain>.  
  
 `pUnkAppDomainManager`  
 [in] Um ponteiro para o <xref:System.AppDomainManager> objeto que o host implementa como `IUnknown`.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`SetAppDomainManager` retornado com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada atingiu o tempo limite.|  
|HOST_E_NOT_OWNER|O chamador não é proprietário do bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo. As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Comentários  
 O <xref:System.AppDomainManager> fornece o host com um mecanismo para inicializar em código gerenciado e controlar a criação e as configurações de cada <xref:System.AppDomain>. O <xref:System.AppDomainManager> é carregado em cada <xref:System.AppDomain> quando que <xref:System.AppDomain> é criado. Se optar por, o CLR notifica o host que o domínio do aplicativo foi criado, definindo o valor da `pUnkAppDomainManager` parâmetro.  
  
 Em sua implementação do `SetAppDomainManager` método, o host pode definir o nome do assembly e o tipo para o Gerenciador de domínio do aplicativo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [Interface IHostControl](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
