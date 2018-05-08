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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8215ddfd0f59f835d0b0dcd278b8cae9c12027d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugthread4hadunhandledexception-method"></a>Método ICorDebugThread4::HadUnhandledException
Indica se o thread nunca teve uma exceção sem tratamento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppBlockingObjectEnum`  
 [out] Um ponteiro para o endereço de uma enumeração ordenada de [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) estruturas.  
  
## <a name="return-value"></a>Valor de retorno  
 Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O thread teve uma exceção sem tratamento desde sua criação.|  
|S_FALSE|O thread nunca teve uma exceção sem tratamento.|  
  
## <a name="remarks"></a>Comentários  
 Este método indica se o thread nunca teve uma exceção sem tratamento. No momento do retorno de chamada de exceção sem tratamento é acionado ou anexação JIT nativo é iniciado, esse método é garantido para retornar S_OK. Não há nenhuma garantia de que o [ICorDebugThread.GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md) método retornará a exceção não tratada; no entanto, ele irá se o processo não ainda sido continua depois de obter o retorno de chamada de exceção sem tratamento ou após nativo de anexação JIT. Além disso, é possível (embora improvável) para ter mais de um thread com uma exceção sem tratamento no momento nativo de anexação JIT é disparado. Nesse caso, não há nenhuma maneira de determinar qual exceção acionada a anexação JIT.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugThread4](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
