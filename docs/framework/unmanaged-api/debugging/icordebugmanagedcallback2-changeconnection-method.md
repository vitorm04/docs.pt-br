---
title: "Método ICorDebugManagedCallback2::ChangeConnection"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.ChangeConnection
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::ChangeConnection
helpviewer_keywords:
- ICorDebugManagedCallback2::ChangeConnection method [.NET Framework debugging]
- ChangeConnection method [.NET Framework debugging]
ms.assetid: 7263f9a9-4c0b-4d82-a181-288873fb2b18
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7c62859cb6a3e61af9670834db169410cecb6787
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallback2changeconnection-method"></a>Método ICorDebugManagedCallback2::ChangeConnection
Notifica o depurador que o conjunto de tarefas associadas a conexão especificada foi alterado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ChangeConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pProcess`  
 [in] Um ponteiro para um objeto de "ICorDebugProcess" que representa o processo que contém a conexão que foram alteradas.  
  
 `dwConnectionId`  
 [in] A ID da conexão alterada.  
  
## <a name="remarks"></a>Comentários  
 Um `ChangeConnection` retorno de chamada será acionado em qualquer um dos seguintes casos:  
  
-   Quando um depurador é anexado a um processo que contém as conexões. Nesse caso, o tempo de execução será gerar e enviar uma [Icordebugmanagedcallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md) eventos e um `ChangeConnection` evento para cada conexão no processo. Um `ChangeConnection` evento é gerado para cada conexão existente, independentemente se o conjunto dessa conexão de tarefas foi alterado desde sua criação.  
  
-   Quando um host chama [: Setconnectiontasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md) no [API de hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md).  
  
 O depurador deve verificar todos os threads do processo para acompanhar as alterações de novo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [Interface ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
