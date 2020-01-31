---
title: Método ICorDebugThread3::GetActiveInternalFrames
ms.date: 03/30/2017
api_name:
- ICorDebugThread3.GetActiveInternalFrames Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3::GetActiveInternalFrames
helpviewer_keywords:
- ICorDebugThread3::GetActiveInternalFrames method [.NET Framework debugging]
- GetActiveInternalFrames method [.NET Framework debugging]
ms.assetid: d69796b4-5b6d-457c-85f6-2cf42e8a8773
topic_type:
- apiref
ms.openlocfilehash: 25cd3e05bc80dd39d2ca558bb4dd5fb77d255f5a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791405"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a>Método ICorDebugThread3::GetActiveInternalFrames
Retorna uma matriz de quadros internos (objetos[ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) ) na pilha.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp 
HRESULT GetActiveInternalFrames  
      (  
      [in] ULONG32 cInternalFrames,  
      [out] ULONG32 *pcInternalFrames,  
      [in, out,size_is(cInternalFrames), length_is(*pcInternalFrames)]  
            ICorDebugInternalFrame2 * ppInternalFrames[]  
      );  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cInternalFrames`  
 no O número de quadros internos esperados no `ppInternalFrames`.  
  
 `pcInternalFrames`  
 fora Um ponteiro para um `ULONG32` que contém o número de quadros internos na pilha.  
  
 `ppInternalFrames`  
 [entrada, saída] Um ponteiro para o endereço de uma matriz de quadros internos na pilha.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O objeto [ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) foi criado com êxito.|  
|{1&gt;E_INVALIDARG&lt;1}|`cInternalFrames` não é zero e `ppInternalFrames` é `null`ou `pcInternalFrames` é `null`.|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|`ppInternalFrames` é menor do que a contagem de quadros internos.|  
  
## <a name="exceptions"></a>Exceções  
  
## <a name="remarks"></a>Comentários  
 Os quadros internos são estruturas de dados enviadas por push para a pilha pelo tempo de execução para armazenar dados temporários.  
  
 Quando você chama o `GetActiveInternalFrames`pela primeira vez, deve definir o parâmetro `cInternalFrames` como 0 (zero) e o parâmetro `ppInternalFrames` como NULL. Quando `GetActiveInternalFrames` primeiro retorna, `pcInternalFrames` contém a contagem dos quadros internos na pilha.  
  
 `GetActiveInternalFrames` deve ser chamado uma segunda vez. Você deve passar a contagem correta (`pcInternalFrames`) no parâmetro `cInternalFrames` e especificar um ponteiro para uma matriz de tamanho apropriado em `ppInternalFrames`.  
  
 Use o método [ICorDebugStackWalk:: GetFrame](icordebugthread3-getactiveinternalframes-method.md) para retornar os quadros de pilhas reais.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
