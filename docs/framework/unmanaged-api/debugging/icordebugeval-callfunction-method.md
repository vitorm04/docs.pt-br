---
title: Método ICorDebugEval::CallFunction
ms.date: 03/30/2017
api_name:
- ICorDebugEval.CallFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::CallFunction
helpviewer_keywords:
- ICorDebugEval::CallFunction method [.NET Framework debugging]
- CallFunction method [.NET Framework debugging]
ms.assetid: 7f470c5c-e1c0-4d8d-aad8-830f113ae751
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 493b4850436b3724287210878992d1d8ce8fe168
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589393"
---
# <a name="icordebugevalcallfunction-method"></a>Método ICorDebugEval::CallFunction
Define uma chamada para a função especificada.  
  
 Este método é obsoleto no .NET Framework versão 2.0. Use [ICorDebugEval2::CallParameterizedFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md) em vez disso.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CallFunction (  
    [in] ICorDebugFunction  *pFunction,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pFunction`  
 [in] Ponteiro para um objeto de ICorDebugFunction que especifica a função a ser chamado.  
  
 `nArgs`  
 [in] O número de argumentos da função.  
  
 `ppArgs`  
 [in] Uma matriz de ponteiros, cada um deles aponta para um objeto de ICorDebugValue que especifica um argumento a ser passado para a função.  
  
## <a name="remarks"></a>Comentários  
 Se a função é virtual, `CallFunction` executará a expedição virtual. Se a função está em um domínio de aplicativo diferente, uma transição ocorrerá desde que todos os argumentos também estão no domínio do aplicativo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** WindowSee [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** 1.1, 1.0  
  
## <a name="see-also"></a>Consulte também
- [Método CallParameterizedFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)
