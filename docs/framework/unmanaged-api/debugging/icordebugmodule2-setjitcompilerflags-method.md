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
# <a name="icordebugmodule2setjitcompilerflags-method"></a><span data-ttu-id="c1f44-102">Método ICorDebugModule2::SetJITCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="c1f44-102">ICorDebugModule2::SetJITCompilerFlags Method</span></span>
<span data-ttu-id="c1f44-103">Define os sinalizadores que controlam a compilação JIT (just-in-time) deste ICorDebugModule2.</span><span class="sxs-lookup"><span data-stu-id="c1f44-103">Sets the flags that control the just-in-time (JIT) compilation of this ICorDebugModule2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1f44-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c1f44-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1f44-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c1f44-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="c1f44-106">no Uma combinação de bits de bit que contenha valores de enumeração [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="c1f44-106">[in] A bitwise combination of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1f44-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="c1f44-107">Remarks</span></span>  
 <span data-ttu-id="c1f44-108">Se o valor de `dwFlags` for inválido, o método `SetJITCompilerFlags` falhará.</span><span class="sxs-lookup"><span data-stu-id="c1f44-108">If the `dwFlags` value is invalid, the `SetJITCompilerFlags` method will fail.</span></span>  
  
 <span data-ttu-id="c1f44-109">O método `SetJITCompilerFlags` pode ser chamado somente de dentro do retorno de chamada [ICorDebugManagedCallback:: LoadModule](icordebugmanagedcallback-loadmodule-method.md) para este módulo.</span><span class="sxs-lookup"><span data-stu-id="c1f44-109">The `SetJITCompilerFlags` method can be called only from within the [ICorDebugManagedCallback::LoadModule](icordebugmanagedcallback-loadmodule-method.md) callback for this module.</span></span> <span data-ttu-id="c1f44-110">O tentará chamá-lo após a entrega do `ICorDebugManagedCallback::LoadModule` o retorno de chamada será reprovado.</span><span class="sxs-lookup"><span data-stu-id="c1f44-110">Attempts to call it after the `ICorDebugManagedCallback::LoadModule` callback has been delivered will fail.</span></span>  
  
 <span data-ttu-id="c1f44-111">Não há suporte para editar e continuar em plataformas de 64 bits ou Win9x.</span><span class="sxs-lookup"><span data-stu-id="c1f44-111">Edit and Continue is not supported on 64-bit or Win9x platforms.</span></span> <span data-ttu-id="c1f44-112">Portanto, se você chamar o método `SetJITCompilerFlags` em qualquer uma dessas duas plataformas com o sinalizador CORDEBUG_JIT_ENABLE_ENC definido em `dwFlags`, o método `SetJITCompilerFlags` e todos os métodos específicos para editar e continuar, como [ICorDebugModule2:: ApplyChanges](icordebugmodule2-applychanges-method.md), falharão.</span><span class="sxs-lookup"><span data-stu-id="c1f44-112">Therefore, if you call the `SetJITCompilerFlags` method on either of these two platforms with the CORDEBUG_JIT_ENABLE_ENC flag set in `dwFlags`, the `SetJITCompilerFlags` method and all methods specific to Edit and Continue, such as [ICorDebugModule2::ApplyChanges](icordebugmodule2-applychanges-method.md), will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1f44-113">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="c1f44-113">Requirements</span></span>  
 <span data-ttu-id="c1f44-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1f44-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1f44-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c1f44-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c1f44-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c1f44-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1f44-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1f44-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
