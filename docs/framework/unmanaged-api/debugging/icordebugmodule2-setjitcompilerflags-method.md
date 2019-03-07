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
ms.openlocfilehash: c71ccbc62ea026a55a7e84f6925a78850594a813
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57473781"
---
# <a name="icordebugmodule2setjitcompilerflags-method"></a><span data-ttu-id="a9797-102">Método ICorDebugModule2::SetJITCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="a9797-102">ICorDebugModule2::SetJITCompilerFlags Method</span></span>
<span data-ttu-id="a9797-103">Define os sinalizadores que controlam a compilação just-in-time (JIT) deste ICorDebugModule2.</span><span class="sxs-lookup"><span data-stu-id="a9797-103">Sets the flags that control the just-in-time (JIT) compilation of this ICorDebugModule2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9797-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a9797-104">Syntax</span></span>  
  
```  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9797-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a9797-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="a9797-106">[in] Uma combinação bit a bit do [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) valores de enumeração.</span><span class="sxs-lookup"><span data-stu-id="a9797-106">[in] A bitwise combination of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9797-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="a9797-107">Remarks</span></span>  
 <span data-ttu-id="a9797-108">Se o `dwFlags` o valor é inválido, o `SetJITCompilerFlags` método falhará.</span><span class="sxs-lookup"><span data-stu-id="a9797-108">If the `dwFlags` value is invalid, the `SetJITCompilerFlags` method will fail.</span></span>  
  
 <span data-ttu-id="a9797-109">O `SetJITCompilerFlags` método pode ser chamado apenas de dentro de [icordebugmanagedcallback:: LoadModule](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md) retorno de chamada para esse módulo.</span><span class="sxs-lookup"><span data-stu-id="a9797-109">The `SetJITCompilerFlags` method can be called only from within the [ICorDebugManagedCallback::LoadModule](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md) callback for this module.</span></span> <span data-ttu-id="a9797-110">Tentativas de chamá-lo após o `ICorDebugManagedCallback::LoadModule` retorno de chamada tiver sido entregue irá falhar.</span><span class="sxs-lookup"><span data-stu-id="a9797-110">Attempts to call it after the `ICorDebugManagedCallback::LoadModule` callback has been delivered will fail.</span></span>  
  
 <span data-ttu-id="a9797-111">Não há suporte para editar e continuar no Win9x plataformas ou de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="a9797-111">Edit and Continue is not supported on 64-bit or Win9x platforms.</span></span> <span data-ttu-id="a9797-112">Portanto, se você chamar o `SetJITCompilerFlags` método em qualquer uma dessas duas plataformas com o sinalizador CORDEBUG_JIT_ENABLE_ENC definido `dwFlags`, o `SetJITCompilerFlags` método e todos os métodos específicos para editar e continuar, tais como [ICorDebugModule2:: ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md), falhará.</span><span class="sxs-lookup"><span data-stu-id="a9797-112">Therefore, if you call the `SetJITCompilerFlags` method on either of these two platforms with the CORDEBUG_JIT_ENABLE_ENC flag set in `dwFlags`, the `SetJITCompilerFlags` method and all methods specific to Edit and Continue, such as [ICorDebugModule2::ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md), will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9797-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a9797-113">Requirements</span></span>  
 <span data-ttu-id="a9797-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9797-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9797-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a9797-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a9797-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a9797-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9797-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9797-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
