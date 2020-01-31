---
title: Método ICorDebugRegisterSet::GetThreadContext
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetThreadContext
helpviewer_keywords:
- GetThreadContext method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetThreadContext method [.NET Framework debugging]
ms.assetid: 0f63400b-dc1c-48d6-b51a-75c3f7f28e03
topic_type:
- apiref
ms.openlocfilehash: 8137d5477b75b864e223852cf524ac8c5b6c0f2b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792087"
---
# <a name="icordebugregistersetgetthreadcontext-method"></a>Método ICorDebugRegisterSet::GetThreadContext
Obtém o contexto do thread atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetThreadContext(  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize),  
        size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `contextSize`  
 no O tamanho, em bytes, da matriz de `context`.  
  
 `context`  
 [entrada, saída] Uma matriz de bytes que compõe a estrutura de `CONTEXT` do Win32 para a plataforma atual.  
  
## <a name="remarks"></a>Comentários  
 O depurador deve chamar essa função em vez da função de `GetThreadContext` do Win32, porque o thread pode estar em um estado "seqüestrado" em que seu contexto foi alterado temporariamente. Os dados retornados são uma estrutura de `CONTEXT` do Win32 para a plataforma atual.  
  
 Para quadros não folha, os clientes devem verificar quais registros são válidos usando [ICorDebugRegisterSet:: GetRegistersAvailable](icordebugregisterset-getregistersavailable-method.md).  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugRegisterSet](icordebugregisterset-interface.md)
- [Interface ICorDebugRegisterSet2](icordebugregisterset2-interface.md)
