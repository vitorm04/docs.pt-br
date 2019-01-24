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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 186f5618cce7a70bc4fab55616a0f8b08025a81f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54542529"
---
# <a name="ihostiocompletionmanager-interface"></a>Interface IHostIoCompletionManager
Fornece métodos que permitem que o common language runtime (CLR) para interagir com as portas de conclusão de e/s fornecidas pelo host.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)|Associa um identificador para uma porta de conclusão de e/s.|  
|[Método CloseIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-closeiocompletionport-method.md)|Fecha uma porta que foi criada por meio de uma chamada anterior para `CreateIoCompletionPort`.|  
|[Método CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)|Solicita que o host, crie uma nova porta de conclusão de e/s.|  
|[Método GetAvailableThreads](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getavailablethreads-method.md)|Obtém o número de threads de conclusão de e/s que atualmente não estão processando solicitações.|  
|[Método GetHostOverlappedSize](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)|Obtém o tamanho de qualquer host pretende anexar às solicitações de e/s de dados personalizados.|  
|[Método GetMaxThreads](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getmaxthreads-method.md)|Obtém o número máximo de threads que o host pode alocar para atender a solicitações de e/s.|  
|[Método GetMinThreads](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getminthreads-method.md)|Obtém o número mínimo de threads que o host fornece para atender a solicitações de e/s.|  
|[Método InitializeHostOverlapped](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md)|Fornece o host com uma oportunidade de inicializar quaisquer dados personalizados sobre uma solicitação de e/s.|  
|[Método SetCLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setclriocompletionmanager-method.md)|Fornece o host com um ponteiro de interface para um [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instância implementada pelo CLR.|  
|[Método SetMaxThreads](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)|Define o número máximo de threads que aloca o host para atender a solicitações de e/s.|  
|[Método SetMinThreads](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setminthreads-method.md)|Define o número mínimo de threads que o host deve alocar até a conclusão de e/s.|  
  
## <a name="remarks"></a>Comentários  
 `IHostIoCompletionManager` corresponde ao `ICLRIoCompletionManager` interface implementada pelo CLR. O CLR chama os métodos de `IHostIoCompletionManager` para associar identificadores para as portas que fornece o host e o host chama os métodos de `ICLRIoCompletionManager` para relatar a conclusão das solicitações de e/s.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
