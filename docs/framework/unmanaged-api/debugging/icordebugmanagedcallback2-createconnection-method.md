---
title: "Método ICorDebugManagedCallback2::CreateConnection"
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
- ICorDebugManagedCallback2.CreateConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::CreateConnection
helpviewer_keywords:
- CreateConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::CreateConnection method [.NET Framework debugging]
ms.assetid: 49e647be-9d63-4250-9d11-704e2a400d1b
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5e0037f72e51683e5b1d62ad7ecb9aa185f53370
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2createconnection-method"></a>Método ICorDebugManagedCallback2::CreateConnection
Notifica o depurador que foi criada uma nova conexão.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CreateConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId,  
    [in] WCHAR                *pConnName  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pProcess`  
 [in] Um ponteiro para um objeto de "ICorDebugProcess" que representa o processo no qual a conexão foi criada  
  
 `dwConnectionId`  
 [in] A ID da conexão de novo.  
  
 `pConnName`  
 [in] Um ponteiro para o nome da conexão de novo.  
  
## <a name="remarks"></a>Comentários  
 Um `CreateConnection` retorno de chamada será acionado em qualquer um dos seguintes casos:  
  
-   Quando um depurador é anexado a um processo que contém as conexões. Nesse caso, o tempo de execução será gerar e enviar uma `CreateConnection` eventos e uma [Icordebugmanagedcallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md) evento para cada conexão no processo.  
  
-   Quando um host chama [Iclrdebugmanager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) no [API de hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [Interface ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
