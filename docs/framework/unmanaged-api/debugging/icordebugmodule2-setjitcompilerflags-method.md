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
ms.openlocfilehash: f73919634ba15dfd16694676d1389875fc2d79bc
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210183"
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
 Se o `dwFlags` valor for inválido, o `SetJITCompilerFlags` método falhará.  
  
 O `SetJITCompilerFlags` método pode ser chamado somente de dentro do retorno de chamada [ICorDebugManagedCallback:: LoadModule](icordebugmanagedcallback-loadmodule-method.md) para este módulo. As tentativas de chamá-lo após a entrega do retorno de chamada `ICorDebugManagedCallback::LoadModule` falharão.  
  
 Não há suporte para editar e continuar em plataformas de 64 bits ou Win9x. Portanto, se você chamar o `SetJITCompilerFlags` método em qualquer uma dessas duas plataformas com o sinalizador CORDEBUG_JIT_ENABLE_ENC definido em `dwFlags` , o `SetJITCompilerFlags` método e todos os métodos específicos para editar e continuar, como [ICorDebugModule2:: ApplyChanges](icordebugmodule2-applychanges-method.md), falharão.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
