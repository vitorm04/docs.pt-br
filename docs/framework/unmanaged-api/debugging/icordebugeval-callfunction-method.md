---
title: "Método ICorDebugEval::CallFunction"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3c2d5582c9ac69692546e9a2310c4d0c9cdde83e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugevalcallfunction-method"></a>Método ICorDebugEval::CallFunction
Configura uma chamada para a função especificada.  
  
 Este método está obsoleto no .NET Framework versão 2.0. Use [Icordebugeval2](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md) em vez disso.  
  
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
 [in] O número de argumentos para a função.  
  
 `ppArgs`  
 [in] Uma matriz de ponteiros, cada um deles aponta para um objeto de ICorDebugValue que especifica um argumento a ser passado para a função.  
  
## <a name="remarks"></a>Comentários  
 Se a função é virtual, `CallFunction` executará expedição virtual. Se a função está em um domínio de aplicativo diferente, ocorrerá uma transição desde que todos os argumentos também estão no domínio de aplicativo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** WindowSee [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** 1.1 e 1.0  
  
## <a name="see-also"></a>Consulte também  
 [Método CallParameterizedFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)
