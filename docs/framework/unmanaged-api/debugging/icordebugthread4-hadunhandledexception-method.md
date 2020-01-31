---
title: Método ICorDebugThread4::HadUnhandledException
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.HadUnhandledException Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::HadUnhandledException
helpviewer_keywords:
- ICorDebugThread4::HadUnhandledException method [.NET Framework debugging]
- HadUnhandledException method [.NET Framework debugging]
ms.assetid: 05558daa-39e2-4c38-aeaf-e2aec4a09468
topic_type:
- apiref
ms.openlocfilehash: f558a4c94afeb69f58605958ddcb91e4be772c39
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791345"
---
# <a name="icordebugthread4hadunhandledexception-method"></a>Método ICorDebugThread4::HadUnhandledException
Indica se o thread já teve uma exceção sem tratamento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ppBlockingObjectEnum`  
 fora Um ponteiro para o endereço de uma enumeração ordenada de estruturas [CorDebugBlockingObject](cordebugblockingobject-structure.md) .  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O thread teve uma exceção sem tratamento desde sua criação.|  
|S_FALSE|O thread nunca teve uma exceção sem tratamento.|  
  
## <a name="remarks"></a>Comentários  
 Esse método indica se o thread já teve uma exceção sem tratamento. No momento em que o retorno de chamada de exceção sem tratamento é acionado ou a anexação JIT nativa é iniciada, esse método é garantido para retornar S_OK. Não há nenhuma garantia de que o método [ICorDebugThread. GetCurrentException](icordebugthread-getcurrentexception-method.md) retornará a exceção sem tratamento; no entanto, ele será se o processo ainda não tiver sido continuado depois de obter o retorno de chamada de exceção sem tratamento ou após a anexação JIT nativa. Além disso, é possível (embora improvável) ter mais de um thread com uma exceção sem tratamento no momento em que a anexação JIT nativa é disparada. Nesse caso, não há como determinar qual exceção disparou a anexação JIT.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugThread4](icordebugthread4-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
