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
ms.openlocfilehash: 4d954057c519263da49f8aaeeeef6ab9402b6956
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378369"
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
  
## <a name="return-value"></a>Valor retornado  
 Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O thread teve uma exceção sem tratamento desde sua criação.|  
|S_FALSE|O thread nunca teve uma exceção sem tratamento.|  
  
## <a name="remarks"></a>Comentários  
 Esse método indica se o thread já teve uma exceção sem tratamento. No momento em que o retorno de chamada de exceção sem tratamento é acionado ou a anexação JIT nativa é iniciada, esse método é garantido para retornar S_OK. Não há nenhuma garantia de que o método [ICorDebugThread. GetCurrentException](icordebugthread-getcurrentexception-method.md) retornará a exceção sem tratamento; no entanto, ele será se o processo ainda não tiver sido continuado depois de obter o retorno de chamada de exceção sem tratamento ou após a anexação JIT nativa. Além disso, é possível (embora improvável) ter mais de um thread com uma exceção sem tratamento no momento em que a anexação JIT nativa é disparada. Nesse caso, não há como determinar qual exceção disparou a anexação JIT.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorDebugThread4](icordebugthread4-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
