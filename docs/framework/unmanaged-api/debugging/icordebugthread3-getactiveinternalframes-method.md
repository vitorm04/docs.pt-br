---
title: "Método ICorDebugThread3::GetActiveInternalFrames"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread3.GetActiveInternalFrames Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread3::GetActiveInternalFrames
helpviewer_keywords:
- ICorDebugThread3::GetActiveInternalFrames method [.NET Framework debugging]
- GetActiveInternalFrames method [.NET Framework debugging]
ms.assetid: d69796b4-5b6d-457c-85f6-2cf42e8a8773
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b9b94827ac49c69c5e72c2e300a80914774cc498
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugthread3getactiveinternalframes-method"></a>Método ICorDebugThread3::GetActiveInternalFrames
Retorna uma matriz de quadros internos ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objetos) na pilha.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetActiveInternalFrames  
      (  
      [in] ULONG32 cInternalFrames,  
      [out] ULONG32 *pcInternalFrames,  
      [in, out,size_is(cInternalFrames), length_is(*pcInternalFrames)]  
            ICorDebugInternalFrame2 * ppInternalFrames[]  
      );  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cInternalFrames`  
 [in] O número de quadros internos esperado em `ppInternalFrames`.  
  
 `pcInternalFrames`  
 [out] Um ponteiro para um `ULONG32` que contém o número de quadros internos na pilha.  
  
 `ppInternalFrames`  
 [out no] Um ponteiro para o endereço de uma matriz de quadros internos na pilha.  
  
## <a name="return-value"></a>Valor de retorno  
 Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O [ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objeto foi criado com êxito.|  
|E_INVALIDARG|`cInternalFrames`não é zero e `ppInternalFrames` é `null`, ou `pcInternalFrames` é `null`.|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|`ppInternalFrames`é menor do que a contagem de quadros internos.|  
  
## <a name="exceptions"></a>Exceções  
  
## <a name="remarks"></a>Comentários  
 Quadros internos são estruturas de dados inseridas na pilha pelo tempo de execução para armazenar dados temporários.  
  
 Quando você chama primeiro `GetActiveInternalFrames`, você deve definir o `cInternalFrames` parâmetro como 0 (zero) e o `ppInternalFrames` parâmetro como null. Quando `GetActiveInternalFrames` retorna primeiro, `pcInternalFrames` contém a contagem de quadros na pilha internas.  
  
 `GetActiveInternalFrames`deve ser chamado pela segunda vez. Você deve passar a contagem adequada (`pcInternalFrames`) no `cInternalFrames` parâmetro, e especifique um ponteiro para uma matriz de tamanho apropriado no `ppInternalFrames`.  
  
 Use o [Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) quadros de pilha do método de retorno real.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
