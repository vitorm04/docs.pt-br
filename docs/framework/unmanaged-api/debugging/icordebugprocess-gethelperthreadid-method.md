---
title: Método ICorDebugProcess::GetHelperThreadID
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad62b267eb0c49ff8fbefeb45b523c21edc705fe
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766046"
---
# <a name="icordebugprocessgethelperthreadid-method"></a>Método ICorDebugProcess::GetHelperThreadID
Obtém a ID do thread do sistema operacional (SO) do thread de auxiliar interno do depurador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pThreadID`  
 [out] ID do thread de auxiliar interno do depurador do thread de um ponteiro para o sistema operacional.  
  
## <a name="remarks"></a>Comentários  
 Durante a depuração de gerenciados e não gerenciados, é responsabilidade do depurador para garantir que o thread com a ID especificada permaneça em execução, se ele atingir um ponto de interrupção colocado pelo depurador. Um depurador também pode desejar ocultar esse thread do usuário. Se nenhum thread auxiliar ainda não existe no processo, o `GetHelperThreadID` método retorna zero em *`pThreadID`.  
  
 Você não pode armazenar em cache a ID do thread do thread auxiliar, pois isso pode mudar ao longo do tempo. Você deve consultar novamente a ID do thread em todos os eventos de interrupção.  
  
 A ID do thread de thread do auxiliar do depurador esteja correta em todos os não gerenciados [icordebugmanagedcallback:: CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) eventos, permitindo assim que um depurador determinar a ID do thread de seu thread auxiliar e ocultá-lo do usuário. Um thread que é identificado como um thread auxiliar durante um não-gerenciado `ICorDebugManagedCallback::CreateThread` evento nunca será executado o código de usuário gerenciado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl. CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
