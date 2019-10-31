---
title: Interface IHostIoCompletionManager
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c28d1983-83f7-46e2-990f-dbb9dc07c818
topic_type:
- apiref
ms.openlocfilehash: 51d79c398c94ec355528140325da2c25422cbad9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133854"
---
# <a name="ihostiocompletionmanager-interface"></a>Interface IHostIoCompletionManager
Fornece métodos que permitem que o Common Language Runtime (CLR) interaja com portas de conclusão de e/s fornecidas pelo host.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)|Associa um identificador a uma porta de conclusão de e/s.|  
|[Método CloseIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-closeiocompletionport-method.md)|Fecha uma porta que foi criada por meio de uma chamada anterior para `CreateIoCompletionPort`.|  
|[Método CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)|Solicita que o host crie uma nova porta de conclusão de e/s.|  
|[Método GetAvailableThreads](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getavailablethreads-method.md)|Obtém o número de threads de conclusão de e/s que não estão processando solicitações no momento.|  
|[Método GetHostOverlappedSize](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)|Obtém o tamanho de qualquer dado personalizado que o host pretende acrescentar às solicitações de e/s.|  
|[Método GetMaxThreads](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getmaxthreads-method.md)|Obtém o número máximo de threads que o host pode alocar para solicitações de e/s de serviço.|  
|[Método GetMinThreads](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getminthreads-method.md)|Obtém o número mínimo de threads que o host fornece para atender solicitações de e/s.|  
|[Método InitializeHostOverlapped](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md)|Fornece ao host uma oportunidade de inicializar quaisquer dados personalizados sobre uma solicitação de e/s.|  
|[Método SetCLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setclriocompletionmanager-method.md)|Fornece ao host um ponteiro de interface para uma instância [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) implementada pelo CLR.|  
|[Método SetMaxThreads](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)|Define o número máximo de threads que o host aloca para atender às solicitações de e/s.|  
|[Método SetMinThreads](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setminthreads-method.md)|Define o número mínimo de threads que o host deve alocar para a conclusão de e/s.|  
  
## <a name="remarks"></a>Comentários  
 `IHostIoCompletionManager` corresponde à interface `ICLRIoCompletionManager` implementada pelo CLR. O CLR chama os métodos de `IHostIoCompletionManager` para associar identificadores às portas que o host fornece, e o host chama os métodos de `ICLRIoCompletionManager` para relatar a conclusão de solicitações de e/s.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE. h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
