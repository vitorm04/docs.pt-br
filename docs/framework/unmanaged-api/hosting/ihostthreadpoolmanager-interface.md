---
title: Interface IHostThreadPoolManager
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager
helpviewer_keywords:
- IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: c3a2cd90-7c4e-4374-bb87-b41befb8344f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e7976740a79efda8e5ab569f2efb55444012c5d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59220364"
---
# <a name="ihostthreadpoolmanager-interface"></a>Interface IHostThreadPoolManager
Fornece métodos que permitem que o common language runtime (CLR) para configurar o pool de threads e para enfileirar itens de trabalho para o pool de threads.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetAvailableThreads](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md)|Obtém o número de threads no pool de threads que não estão processando no momento, os itens de trabalho.|  
|[Método GetMaxThreads](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)|Obtém o número máximo de threads que o host mantém simultaneamente no pool de threads.|  
|[Método GetMinThreads](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)|Obtém o número mínimo de threads ociosos do que o host mantém em antecipação de solicitações.|  
|[Método QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)|Enfileira uma função para a execução e fornece um objeto que contém dados a serem usados pela função.|  
|[Método SetMaxThreads](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)|Define o número máximo de threads que o host pode manter no pool de threads.|  
|[Método SetMinThreads](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)|Define o número mínimo de threads ociosos do que o host deve manter em antecipação de solicitações.|  
  
## <a name="remarks"></a>Comentários  
 O host não é necessário para configurar o pool de threads usando os valores especificados em chamadas para o `SetMaxThreads` e `SetMinThreads` métodos. Nesse caso, o host deve retornar um valor HRESULT de E_NOTIMPL desses métodos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Threading>
- <xref:System.Threading.ThreadPool>
- [Interfaces de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
