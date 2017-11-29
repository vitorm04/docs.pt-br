---
title: "Método IHostIoCompletionManager::GetHostOverlappedSize"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.GetHostOverlappedSize
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::GetHostOverlappedSize
helpviewer_keywords:
- IHostIoCompletionManager::GetHostOverlappedSize method [.NET Framework hosting]
- GetHostOverlappedSize method [.NET Framework hosting]
ms.assetid: 2902578b-d5e2-4f8d-a103-0c7b6dceda9e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6633e0271f29d44bb1d14495d80ffdf9868485a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostiocompletionmanagergethostoverlappedsize-method"></a>Método IHostIoCompletionManager::GetHostOverlappedSize
Obtém o tamanho de qualquer host pretende anexar a solicitações de e/s de dados personalizados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetHostOverlappedSize (  
    [out] DWORD *pcbSize  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pcbSize`  
 [out] Um ponteiro para o número de bytes que o common language runtime (CLR) deve alocar além do tamanho do Win32 `OVERLAPPED` objeto.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`GetHostOverlappedSize`retornou com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada foi atingido.|  
|HOST_E_NOT_OWNER|O chamador não possui o bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo. As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Comentários  
 Todas as chamadas de e/s assíncronas para APIs da plataforma Windows levar Win32 `OVERLAPPED` objeto, que fornece informações como a posição do ponteiro de arquivo. Para manter o estado, aplicativos que fazem chamadas de e/s assíncronas normalmente adicionam dados personalizados para a estrutura. `GetHostOverlappedSize`e [: Initializehostoverlapped](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md) oferecem uma oportunidade para o host incluir esses dados personalizados.  
  
 O CLR chama o `GetHostOverlappedSize` método para determinar o tamanho dos dados personalizados que o host deve acrescentar ao `OVERLAPPED` objeto.  
  
> [!NOTE]
>  `GetHostOverlappedSize`é chamado apenas uma vez. Dados personalizados do host devem ser do mesmo tamanho para cada solicitação de e/s.  
  
> [!IMPORTANT]
>  O tamanho do `OVERLAPPED` próprio objeto não está incluído no valor de `pcbSize`.  
  
 Para obter mais informações sobre o `OVERLAPPED` estrutura, consulte a documentação da plataforma Windows.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading.NativeOverlapped>  
 [Interface ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [Interface IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
