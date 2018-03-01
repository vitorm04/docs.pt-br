---
title: "Método ICorDebugProcess::GetHelperThreadID"
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
- ICorDebugProcess.GetHelperThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHelperThreadID
helpviewer_keywords:
- GetHelperThreadID method [.NET Framework debugging]
- ICorDebugProcess::GetHelperThreadID method [.NET Framework debugging]
ms.assetid: 84e1e605-37c1-49a5-8e12-35db85654622
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 03e801cb58b8f5c3f658085fcee4288278e545c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessgethelperthreadid-method"></a>Método ICorDebugProcess::GetHelperThreadID
Obtém a ID do thread do sistema operacional (SO) do thread de auxiliar interno do depurador.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pThreadID`  
 [out] ID do thread de auxiliar interno do depurador do thread de um ponteiro para o sistema operacional.  
  
## <a name="remarks"></a>Comentários  
 Durante a depuração gerenciado e não gerenciado, é responsabilidade do depurador para garantir que o thread com a ID especificada permanece em execução, se ele atinja um ponto de interrupção colocado pelo depurador. Um depurador também pode querer ocultar esse thread do usuário. Se nenhum thread auxiliar ainda não existe no processo, o `GetHelperThreadID` método retorna zero em *`pThreadID`.  
  
 Você não pode armazenar em cache a ID do thread do thread auxiliar, pois ele pode ser alterado ao longo do tempo. Você deve consultar novamente a ID do thread em todos os eventos de interrupção.  
  
 A ID do thread de thread do auxiliar do depurador estará correta em todos os não gerenciados [Icordebugmanagedcallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) eventos, permitindo que um depurador determinar a ID do thread de seu thread auxiliar e ocultá-lo do usuário. Um thread que é identificado como um thread auxiliar durante um não gerenciado `ICorDebugManagedCallback::CreateThread` evento nunca será executado o código de usuário gerenciado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl. CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
