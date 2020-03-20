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
ms.openlocfilehash: 680af5afa3ebef5bcaf9e34580e421dcc8093aaf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178459"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a>Método ICorDebugThread3::GetActiveInternalFrames
Retorna uma matriz de quadros internos (objetos[ICorDebugInternalFrame2)](icordebuginternalframe2-interface.md) na pilha.  
  
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
  
## <a name="parameters"></a>parâmetros  
 `cInternalFrames`  
 [em] O número de quadros `ppInternalFrames`internos esperados em .  
  
 `pcInternalFrames`  
 [fora] Um ponteiro `ULONG32` para um que contém o número de quadros internos na pilha.  
  
 `ppInternalFrames`  
 [dentro, fora] Um ponteiro para o endereço de uma matriz de quadros internos na pilha.  
  
## <a name="return-value"></a>Valor retornado  
 Este método retorna os seguintes HRESULTs específicos, bem como erros de HRESULT que indicam falha do método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O objeto [ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) foi criado com sucesso.|  
|E_INVALIDARG|`cInternalFrames`não é `ppInternalFrames` zero `null`e `pcInternalFrames` `null`é, ou é .|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|`ppInternalFrames`é menor do que a contagem de quadros internos.|  
  
## <a name="exceptions"></a>Exceções  
  
## <a name="remarks"></a>Comentários  
 Quadros internos são estruturas de dados empurradas para a pilha pelo tempo de execução para armazenar dados temporários.  
  
 Quando você `GetActiveInternalFrames`chamar pela primeira `cInternalFrames` vez, você deve definir `ppInternalFrames` o parâmetro como 0 (zero) e o parâmetro para nulo. Quando `GetActiveInternalFrames` retorna `pcInternalFrames` pela primeira vez, contém a contagem dos quadros internos na pilha.  
  
 `GetActiveInternalFrames`então deve ser chamado uma segunda vez. Você deve passar a`pcInternalFrames`contagem `cInternalFrames` adequada ( ) no parâmetro, e `ppInternalFrames`especificar um ponteiro para uma matriz de tamanho apropriado em .  
  
 Use o método [ICorDebugStackWalk::GetFrame](icordebugthread3-getactiveinternalframes-method.md) para retornar quadros reais de pilha.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
