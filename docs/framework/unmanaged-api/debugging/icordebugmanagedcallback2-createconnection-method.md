---
title: Método ICorDebugManagedCallback2::CreateConnection
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 300baeb4184bbb73704563671ab907fafbdb5284
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57472623"
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
  
## <a name="parameters"></a>Parâmetros  
 `pProcess`  
 [in] Um ponteiro para um objeto de "ICorDebugProcess" que representa o processo no qual a conexão foi criada  
  
 `dwConnectionId`  
 [in] A ID da nova conexão.  
  
 `pConnName`  
 [in] Um ponteiro para o nome da nova conexão.  
  
## <a name="remarks"></a>Comentários  
 Um `CreateConnection` retorno de chamada será acionado em qualquer um dos seguintes casos:  
  
-   Quando um depurador é anexado a um processo que contém as conexões. Nesse caso, o tempo de execução gerará e expedir uma `CreateConnection` evento e uma [ICorDebugManagedCallback2::ChangeConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md) evento para cada conexão no processo.  
  
-   Quando um host chama [iclrdebugmanager:: Beginconnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) na [API de hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [Interface ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
