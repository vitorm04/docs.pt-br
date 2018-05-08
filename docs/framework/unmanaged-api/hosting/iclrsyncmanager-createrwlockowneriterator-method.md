---
title: Método ICLRSyncManager::CreateRWLockOwnerIterator
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.CreateRWLockOwnerIterator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator method [.NET Framework hosting]
- CreateRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: b5535b87-9439-424e-b9b3-7d6fafb9819e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eda20543c28a7b97979463928ce307df9b830103
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="iclrsyncmanagercreaterwlockowneriterator-method"></a>Método ICLRSyncManager::CreateRWLockOwnerIterator
Solicita que o common language runtime (CLR) criar um iterador para o host a ser usado para determinar o conjunto de tarefas que esperam por um bloqueio de leitor / gravador.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CreateRWLockOwnerIterator (  
    [in]  SIZE_T    cookie,  
    [out] SIZE_T   *pIterator  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cookie`  
 [in] O cookie associado ao bloqueio de leitor-gravador desejado.  
  
 `pIterator`  
 [out] Um ponteiro para um iterador que pode ser passado para o [GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) e [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) métodos.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`CreateRWLockOwnerIterator` retornou com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada foi atingido.|  
|HOST_E_NOT_OWNER|O chamador não possui o bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo. As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_INVALIDOPERATION|`CreateRWLockOwnerIterator` foi chamado em um thread que está executando o código gerenciado.|  
  
## <a name="remarks"></a>Comentários  
 Hosts normalmente chama o `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, e `GetRWLockOwnerNext` métodos durante a detecção de deadlock. O host é responsável por garantir que o bloqueio de leitor-gravador ainda é válido, porque nenhuma tentativa para manter o bloqueio de leitor-gravador ativa faz com que o CLR. Várias estratégias estão disponíveis para o host garantir a validade do bloqueio:  
  
-   O host pode bloquear chamadas de versão sobre o bloqueio de leitor-gravador (por exemplo, [Ihostsemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)), garantindo que esse bloco não causar deadlock.  
  
-   O host pode bloquear a saída de esperar o objeto de evento associado com o bloqueio de leitor-gravador, novamente, garantindo que esse bloco não causar deadlock.  
  
> [!NOTE]
>  `CreateRWLockOwnerIterator` deve ser chamado apenas em threads que estão executando o código não gerenciado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [Interface IHostSyncManager](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
