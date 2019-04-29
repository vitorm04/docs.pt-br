---
title: Método ICorConfiguration::SetGCThreadControl
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetGCThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCThreadControl
helpviewer_keywords:
- ICorConfiguration::SetGCThreadControl method [.NET Framework hosting]
- SetGCThreadControl method [.NET Framework hosting]
ms.assetid: 72e38e61-3d56-4ae3-b8f6-0ab7922aaf11
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b50c87efeb8ad2311a75886da677a9dc901bca1b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763224"
---
# <a name="icorconfigurationsetgcthreadcontrol-method"></a>Método ICorConfiguration::SetGCThreadControl
Define a interface de retorno de chamada para o agendamento de threads para tarefas de tempo de execução não caso contrário, seriam bloqueadas para uma coleta de lixo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetGCThreadControl (  
    [in] IGCThreadControl* pGCThreadControl  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pGCThreadControl`  
 [in] Um ponteiro para um [IGCThreadControl](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md) objeto que notifica o host sobre a suspensão de threads para tarefas sem tempo de execução.  
  
## <a name="remarks"></a>Comentários  
 O host pode escolher dentro de [igcthreadcontrol:: Threadisblockingforsuspension](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md) retorno de chamada se reagendar um thread.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
