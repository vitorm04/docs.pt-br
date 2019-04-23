---
title: Método ICorDebugManagedCallback2::ChangeConnection
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.ChangeConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::ChangeConnection
helpviewer_keywords:
- ICorDebugManagedCallback2::ChangeConnection method [.NET Framework debugging]
- ChangeConnection method [.NET Framework debugging]
ms.assetid: 7263f9a9-4c0b-4d82-a181-288873fb2b18
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b4eeecc22db5786f66b3d484b521989e71817d8e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59185036"
---
# <a name="icordebugmanagedcallback2changeconnection-method"></a>Método ICorDebugManagedCallback2::ChangeConnection
Notifica o depurador que o conjunto de tarefas associadas com a conexão especificada foi alterado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ChangeConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pProcess`  
 [in] Um ponteiro para um objeto de "ICorDebugProcess" que representa o processo que contém a conexão que foi alterada.  
  
 `dwConnectionId`  
 [in] A ID da conexão que foi alterada.  
  
## <a name="remarks"></a>Comentários  
 Um `ChangeConnection` retorno de chamada será acionado em qualquer um dos seguintes casos:  
  
-   Quando um depurador é anexado a um processo que contém as conexões. Nesse caso, o tempo de execução gerará e expedir uma [ICorDebugManagedCallback2::CreateConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md) eventos e um `ChangeConnection` evento para cada conexão no processo. Um `ChangeConnection` evento é gerado para cada conexão existente, independentemente se o conjunto dessa conexão de tarefas foi alterado desde sua criação.  
  
-   Quando um host chama [iclrdebugmanager:: Setconnectiontasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md) na [API de hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md).  
  
 O depurador deve verificar todos os threads do processo para acompanhar as alterações de novo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [Interface ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
