---
title: Método IHostThreadPoolManager::QueueUserWorkItem
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.QueueUserWorkItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::QueueUserWorkItem
helpviewer_keywords:
- IHostThreadPoolManager::QueueUserWorkItem method [.NET Framework hosting]
- QueueUserWorkItem method [.NET Framework hosting]
ms.assetid: 41602053-8670-4827-9d61-cbfcba509b9c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c548ae7f8d605ff84da2046d057e436c8e95721
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796557"
---
# <a name="ihostthreadpoolmanagerqueueuserworkitem-method"></a>Método IHostThreadPoolManager::QueueUserWorkItem
Enfileira uma função para a execução e especifica um objeto que contém dados a serem usados por essa função. A função é executada quando um thread fique disponível.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT QueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID Context,  
    [in] ULONG Flags  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `Function`  
 [in] Um ponteiro de função que representa a função a ser executada.  
  
 `Context`  
 [in] Um objeto que contém dados a serem usados pelo `Function`.  
  
 `Flags`  
 [in] Um dos sinalizadores de valores, conforme definido para o Win32 `QueueUserWorkItem` método, que controlam a execução.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`QueueUserWorkItem` retornado com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada atingiu o tempo limite.|  
|HOST_E_NOT_OWNER|O chamador não é proprietário do bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo. As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Comentários  
 `QueueUserWorkItem` Enfileira um item de trabalho para um thread de trabalho no pool de threads. Seus tipos de assinatura e de parâmetro são idênticos da função do Win32 correspondente, que tem o mesmo nome. Para obter mais informações, consulte a documentação da plataforma Windows.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>
- <xref:System.Threading.ThreadPool>
- [Interface IHostThreadPoolManager](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
