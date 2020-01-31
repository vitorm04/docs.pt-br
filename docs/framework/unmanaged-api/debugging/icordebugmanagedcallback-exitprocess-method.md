---
title: Método ICorDebugManagedCallback::ExitProcess
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitProcess
helpviewer_keywords:
- ExitProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::ExitProcess method [.NET Framework debugging]
ms.assetid: 63a7d47a-0d54-4e29-9767-9f09feaa38b7
topic_type:
- apiref
ms.openlocfilehash: 4380b8a3803e164aab7318821a9dbde32ecc3a0b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781747"
---
# <a name="icordebugmanagedcallbackexitprocess-method"></a>Método ICorDebugManagedCallback::ExitProcess
Notifica o depurador de que um processo foi encerrado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ExitProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pProcess`  
 no Um ponteiro para um objeto ICorDebugProcess que representa o processo.  
  
## <a name="remarks"></a>Comentários  
 Não é possível continuar a partir de um evento `ExitProcess`. Esse evento pode ser acionado de forma assíncrona a outros eventos enquanto o processo parece estar parado. Isso pode ocorrer se o processo for encerrado enquanto é interrompido, geralmente devido a alguma força externa.  
  
 Se o Common Language Runtime (CLR) já estiver expedindo um retorno de chamada gerenciado, esse evento será atrasado até que o retorno de chamada seja retornado.  
  
 O evento `ExitProcess` é o único evento Exit/Unload que é garantido para ser chamado no desligamento.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugManagedCallback](icordebugmanagedcallback-interface.md)
