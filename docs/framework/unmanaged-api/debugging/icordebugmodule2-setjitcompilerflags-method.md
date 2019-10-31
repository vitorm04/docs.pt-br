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
# <a name="icordebugmodule2setjitcompilerflags-method"></a><span data-ttu-id="d80d2-102">Método ICorDebugModule2::SetJITCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="d80d2-102">ICorDebugModule2::SetJITCompilerFlags Method</span></span>
<span data-ttu-id="d80d2-103">Define os sinalizadores que controlam a compilação JIT (just-in-time) deste ICorDebugModule2.</span><span class="sxs-lookup"><span data-stu-id="d80d2-103">Sets the flags that control the just-in-time (JIT) compilation of this ICorDebugModule2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d80d2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d80d2-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d80d2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d80d2-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="d80d2-106">no Uma combinação de bits de bit que contenha valores de enumeração [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="d80d2-106">[in] A bitwise combination of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d80d2-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="d80d2-107">Remarks</span></span>  
 <span data-ttu-id="d80d2-108">Se o valor de `dwFlags` for inválido, o método `SetJITCompilerFlags` falhará.</span><span class="sxs-lookup"><span data-stu-id="d80d2-108">If the `dwFlags` value is invalid, the `SetJITCompilerFlags` method will fail.</span></span>  
  
 <span data-ttu-id="d80d2-109">O método `SetJITCompilerFlags` pode ser chamado somente de dentro do retorno de chamada [ICorDebugManagedCallback:: LoadModule](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md) para este módulo.</span><span class="sxs-lookup"><span data-stu-id="d80d2-109">The `SetJITCompilerFlags` method can be called only from within the [ICorDebugManagedCallback::LoadModule](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md) callback for this module.</span></span> <span data-ttu-id="d80d2-110">O tentará chamá-lo após a entrega do `ICorDebugManagedCallback::LoadModule` o retorno de chamada será reprovado.</span><span class="sxs-lookup"><span data-stu-id="d80d2-110">Attempts to call it after the `ICorDebugManagedCallback::LoadModule` callback has been delivered will fail.</span></span>  
  
 <span data-ttu-id="d80d2-111">Não há suporte para editar e continuar em plataformas de 64 bits ou Win9x.</span><span class="sxs-lookup"><span data-stu-id="d80d2-111">Edit and Continue is not supported on 64-bit or Win9x platforms.</span></span> <span data-ttu-id="d80d2-112">Portanto, se você chamar o método `SetJITCompilerFlags` em qualquer uma dessas duas plataformas com o sinalizador CORDEBUG_JIT_ENABLE_ENC definido em `dwFlags`, o método `SetJITCompilerFlags` e todos os métodos específicos para editar e continuar, como [ICorDebugModule2:: ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md), falharão.</span><span class="sxs-lookup"><span data-stu-id="d80d2-112">Therefore, if you call the `SetJITCompilerFlags` method on either of these two platforms with the CORDEBUG_JIT_ENABLE_ENC flag set in `dwFlags`, the `SetJITCompilerFlags` method and all methods specific to Edit and Continue, such as [ICorDebugModule2::ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md), will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d80d2-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d80d2-113">Requirements</span></span>  
 <span data-ttu-id="d80d2-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d80d2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d80d2-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d80d2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d80d2-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d80d2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d80d2-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d80d2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
