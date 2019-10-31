---
title: Método ICorDebugModule2::SetJITCompilerFlags
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.SetJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::SetJITCompilerFlags
helpviewer_keywords:
- ICorDebugModule2::SetJITCompilerFlags method [.NET Framework debugging]
- SetJITCompilerFlags method [.NET Framework debugging]
ms.assetid: ea574c84-c622-4589-9a14-b55771af5e06
topic_type:
- apiref
ms.openlocfilehash: 2358cee1b3a9aa50fb1f0e61d558f164a39aa86c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137356"
---
# <a name="icordebugmodule2setjitcompilerflags-method"></a>Método ICorDebugModule2::SetJITCompilerFlags
Define os sinalizadores que controlam a compilação JIT (just-in-time) deste ICorDebugModule2.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `dwFlags`  
 no Uma combinação de bits de bit que contenha valores de enumeração [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) .  
  
## <a name="remarks"></a>Comentários  
 Se o valor de `dwFlags` for inválido, o método `SetJITCompilerFlags` falhará.  
  
 O método `SetJITCompilerFlags` pode ser chamado somente de dentro do retorno de chamada [ICorDebugManagedCallback:: LoadModule](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md) para este módulo. O tentará chamá-lo após a entrega do `ICorDebugManagedCallback::LoadModule` o retorno de chamada será reprovado.  
  
 Não há suporte para editar e continuar em plataformas de 64 bits ou Win9x. Portanto, se você chamar o método `SetJITCompilerFlags` em qualquer uma dessas duas plataformas com o sinalizador CORDEBUG_JIT_ENABLE_ENC definido em `dwFlags`, o método `SetJITCompilerFlags` e todos os métodos específicos para editar e continuar, como [ICorDebugModule2:: ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md), falharão.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
