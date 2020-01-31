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
ms.openlocfilehash: b28e457ea0b51d320581c0fbe36574698081ea36
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792954"
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
 no Uma combinação de bits de bit que contenha valores de enumeração [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) .  
  
## <a name="remarks"></a>Comentários  
 Se o valor de `dwFlags` for inválido, o método `SetJITCompilerFlags` falhará.  
  
 O método `SetJITCompilerFlags` pode ser chamado somente de dentro do retorno de chamada [ICorDebugManagedCallback:: LoadModule](icordebugmanagedcallback-loadmodule-method.md) para este módulo. O tentará chamá-lo após a entrega do `ICorDebugManagedCallback::LoadModule` o retorno de chamada será reprovado.  
  
 Não há suporte para editar e continuar em plataformas de 64 bits ou Win9x. Portanto, se você chamar o método `SetJITCompilerFlags` em qualquer uma dessas duas plataformas com o sinalizador CORDEBUG_JIT_ENABLE_ENC definido em `dwFlags`, o método `SetJITCompilerFlags` e todos os métodos específicos para editar e continuar, como [ICorDebugModule2:: ApplyChanges](icordebugmodule2-applychanges-method.md), falharão.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
