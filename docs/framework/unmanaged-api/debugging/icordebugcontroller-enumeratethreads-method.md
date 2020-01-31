---
title: Método ICorDebugController::EnumerateThreads
ms.date: 03/30/2017
api_name:
- ICorDebugController.EnumerateThreads
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::EnumerateThreads
helpviewer_keywords:
- ICorDebugController::EnumerateThreads method [.NET Framework debugging]
- EnumerateThreads method [.NET Framework debugging]
ms.assetid: 73f536f6-4668-4a4a-b3e4-ac7df862d5be
topic_type:
- apiref
ms.openlocfilehash: 815dc63a2dedecc613506b0f98702f58d6e7bd04
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783786"
---
# <a name="icordebugcontrollerenumeratethreads-method"></a>Método ICorDebugController::EnumerateThreads
Obtém um enumerador para os threads gerenciados ativos no processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ppThreads`  
 fora Um ponteiro para o endereço de um objeto "ICorDebugThreadEnum" que representa um enumerador para todos os threads gerenciados que estão ativos no processo.  
  
## <a name="remarks"></a>Comentários  
 Um thread é considerado ativo após o retorno de chamada [ICorDebugManagedCallback:: CreateThread](icordebugmanagedcallback-createthread-method.md) ter sido expedido e antes de o retorno de chamada [ICorDebugManagedCallback:: ExitThread](icordebugmanagedcallback-exitthread-method.md) ser expedido. Um thread gerenciado pode não ter necessariamente nenhum quadro gerenciado em sua pilha. Os threads podem ser enumerados mesmo antes do retorno de chamada [ICorDebugManagedCallback:: CreateProcess](icordebugmanagedcallback-createprocess-method.md) . A enumeração estará naturalmente vazia.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também
