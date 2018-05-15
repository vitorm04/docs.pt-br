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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e605859a3049abc0c17d9d6792ade78f4ad2bd78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmodule2setjitcompilerflags-method"></a><span data-ttu-id="b1e2d-102">Método ICorDebugModule2::SetJITCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="b1e2d-102">ICorDebugModule2::SetJITCompilerFlags Method</span></span>
<span data-ttu-id="b1e2d-103">Define os sinalizadores que controlam a compilação just-in-time (JIT) deste ICorDebugModule2.</span><span class="sxs-lookup"><span data-stu-id="b1e2d-103">Sets the flags that control the just-in-time (JIT) compilation of this ICorDebugModule2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1e2d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b1e2d-104">Syntax</span></span>  
  
```  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b1e2d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b1e2d-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="b1e2d-106">[in] Uma combinação bit a bit do [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) valores de enumeração.</span><span class="sxs-lookup"><span data-stu-id="b1e2d-106">[in] A bitwise combination of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1e2d-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="b1e2d-107">Remarks</span></span>  
 <span data-ttu-id="b1e2d-108">Se o `dwFlags` o valor é inválido, o `SetJITCompilerFlags` método irá falhar.</span><span class="sxs-lookup"><span data-stu-id="b1e2d-108">If the `dwFlags` value is invalid, the `SetJITCompilerFlags` method will fail.</span></span>  
  
 <span data-ttu-id="b1e2d-109">O `SetJITCompilerFlags` método pode ser chamado apenas de dentro do [: LoadModule](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md) retorno de chamada para este módulo.</span><span class="sxs-lookup"><span data-stu-id="b1e2d-109">The `SetJITCompilerFlags` method can be called only from within the [ICorDebugManagedCallback::LoadModule](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md) callback for this module.</span></span> <span data-ttu-id="b1e2d-110">Tenta chamá-lo após o `ICorDebugManagedCallback::LoadModule` retorno de chamada foi entregue irá falhar.</span><span class="sxs-lookup"><span data-stu-id="b1e2d-110">Attempts to call it after the `ICorDebugManagedCallback::LoadModule` callback has been delivered will fail.</span></span>  
  
 <span data-ttu-id="b1e2d-111">Não há suporte para editar e continuar em 64 bits ou plataformas Win9x.</span><span class="sxs-lookup"><span data-stu-id="b1e2d-111">Edit and Continue is not supported on 64-bit or Win9x platforms.</span></span> <span data-ttu-id="b1e2d-112">Portanto, se você chamar o `SetJITCompilerFlags` método em qualquer uma dessas duas plataformas com o sinalizador CORDEBUG_JIT_ENABLE_ENC definido `dwFlags`, o `SetJITCompilerFlags` método e todos os métodos específicos para editar e continuar, como [ICorDebugModule2:: ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md), falharão.</span><span class="sxs-lookup"><span data-stu-id="b1e2d-112">Therefore, if you call the `SetJITCompilerFlags` method on either of these two platforms with the CORDEBUG_JIT_ENABLE_ENC flag set in `dwFlags`, the `SetJITCompilerFlags` method and all methods specific to Edit and Continue, such as [ICorDebugModule2::ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md), will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1e2d-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b1e2d-113">Requirements</span></span>  
 <span data-ttu-id="b1e2d-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1e2d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1e2d-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b1e2d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1e2d-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1e2d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1e2d-117">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1e2d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
