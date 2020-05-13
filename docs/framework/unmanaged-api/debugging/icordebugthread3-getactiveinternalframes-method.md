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
ms.openlocfilehash: 953b7c1cb5e471072776fe03e53a46d3ff19c0ac
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379858"
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
 no O número de quadros internos esperados em `ppInternalFrames` .  
  
 `pcInternalFrames`  
 fora Um ponteiro para um `ULONG32` que contém o número de quadros internos na pilha.  
  
 `ppInternalFrames`  
 [entrada, saída] Um ponteiro para o endereço de uma matriz de quadros internos na pilha.  
  
## <a name="return-value"></a>Valor retornado  
 Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O objeto [ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) foi criado com êxito.|  
|E_INVALIDARG|`cInternalFrames`Não é zero e `ppInternalFrames` é `null` `pcInternalFrames` `null` .|  
|HRESULT_FROM_WIN32 (ERROR_INSUFFICIENT_BUFFER)|`ppInternalFrames`é menor do que a contagem de quadros internos.|  
  
## <a name="exceptions"></a>Exceções  
  
## <a name="remarks"></a>Comentários  
 Os quadros internos são estruturas de dados enviadas por push para a pilha pelo tempo de execução para armazenar dados temporários.  
  
 Ao chamar pela primeira vez `GetActiveInternalFrames` , você deve definir o `cInternalFrames` parâmetro como 0 (zero) e o `ppInternalFrames` parâmetro como NULL. Quando `GetActiveInternalFrames` o primeiro retorna, `pcInternalFrames` contém a contagem dos quadros internos na pilha.  
  
 `GetActiveInternalFrames`deve ser chamado uma segunda vez. Você deve passar a contagem apropriada ( `pcInternalFrames` ) no `cInternalFrames` parâmetro e especificar um ponteiro para uma matriz de tamanho apropriado no `ppInternalFrames` .  
  
 Use o método [ICorDebugStackWalk:: GetFrame](icordebugthread3-getactiveinternalframes-method.md) para retornar os quadros de pilhas reais.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
