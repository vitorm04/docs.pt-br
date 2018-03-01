---
title: "Método IHostSecurityManager::OpenThreadToken"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostSecurityManager.OpenThreadToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::OpenThreadToken
helpviewer_keywords:
- IHostSecurityManager::OpenThreadToken method [.NET Framework hosting]
- OpenThreadToken method [.NET Framework hosting]
ms.assetid: d5999052-8bf0-4a9e-8621-da6284406b18
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9b5c39632d7628d30149a0a0278f9bf6c865bc29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a>Método IHostSecurityManager::OpenThreadToken
Abre o token de acesso discricionário associado ao thread em execução no momento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,   
    [in]  BOOL     bOpenAsSelf,   
    [out] HANDLE   *phThreadToken  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwDesiredAccess`  
 [in] Uma máscara de valores de acesso que especificam os tipos solicitados de acesso para o token de thread. Esses valores são definidos em Win32 `OpenThreadToken` função. Os tipos de acesso solicitado reconciliadas em relação a lista de controle de acesso discricionário (DACL) para determinar quais tipos de acesso para conceder ou negar do token.  
  
 `bOpenAsSelf`  
 [in] `true` para especificar que a verificação de acesso deve ser feita usando o contexto de segurança do processo para o thread de chamada; `false` para especificar que a verificação de acesso deve ser executada usando o contexto de segurança para o thread de chamada. Se o thread está representando um cliente, o contexto de segurança pode ser de um processo do cliente.  
  
 `phThreadToken`  
 [out] Um ponteiro para o token de acesso aberto recentemente.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`OpenThreadToken`retornou com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada foi atingido.|  
|HOST_E_NOT_OWNER|O chamador não possui o bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo. As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Comentários  
 `IHostSecurityManager::OpenThreadToken`se comporta da mesma forma para a função Win32 correspondente de mesmo nome, exceto que a função Win32 permite que o chamador passar um identificador para um thread arbitrário, enquanto `IHostSecurityManager::OpenThreadToken` abre apenas o token associado com o thread de chamada.  
  
 O `HANDLE` tipo não é compatível com o COM, ou seja, seu tamanho é específico para o sistema operacional e requer empacotamento personalizado. Portanto, esse token é para uso somente dentro do processo, entre o host e o CLR.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [Interface IHostSecurityManager](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
