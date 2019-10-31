---
title: Método ICorDebugProcess2::SetDesiredNGENCompilerFlags
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.SetDesiredNGENCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags method [.NET Framework debugging]
- SetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: 98320175-7c5e-4dbb-8683-86fa82e2641f
topic_type:
- apiref
ms.openlocfilehash: 9313fc58dec8099f42dbff07685ca14791fa324f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137169"
---
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a><span data-ttu-id="b7b58-102">Método ICorDebugProcess2::SetDesiredNGENCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="b7b58-102">ICorDebugProcess2::SetDesiredNGENCompilerFlags Method</span></span>
<span data-ttu-id="b7b58-103">Define os sinalizadores que devem ser inseridos em uma imagem pré-compilada para que o tempo de execução carregue essa imagem no processo atual.</span><span class="sxs-lookup"><span data-stu-id="b7b58-103">Sets the flags that must be embedded in a precompiled image in order for the runtime to load that image into the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7b58-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7b58-104">Syntax</span></span>  
  
```cpp  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7b58-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b7b58-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="b7b58-106">no Um valor da enumeração [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) que especifica os sinalizadores de compilador usados para selecionar a imagem previamente compilada correta.</span><span class="sxs-lookup"><span data-stu-id="b7b58-106">[in] A value of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration that specifies the compiler flags used to select the correct pre-compiled image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7b58-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="b7b58-107">Remarks</span></span>  
 <span data-ttu-id="b7b58-108">O método `SetDesiredNGENCompilerFlags` especifica os sinalizadores que devem ser inseridos em uma imagem pré-compilada para que o tempo de execução carregue essa imagem nesse processo.</span><span class="sxs-lookup"><span data-stu-id="b7b58-108">The `SetDesiredNGENCompilerFlags` method specifies the flags that must be embedded in a precompiled image so that the runtime will load that image into this process.</span></span> <span data-ttu-id="b7b58-109">Os sinalizadores definidos por esse método são usados apenas para selecionar a imagem pré-compilada correta.</span><span class="sxs-lookup"><span data-stu-id="b7b58-109">The flags set by this method are used only to select the correct precompiled image.</span></span> <span data-ttu-id="b7b58-110">Se essa imagem não existir, o tempo de execução carregará a imagem do Microsoft Intermediate Language (MSIL) e o compilador JIT (just-in-time).</span><span class="sxs-lookup"><span data-stu-id="b7b58-110">If no such image exists, the runtime will load the Microsoft intermediate language (MSIL) image and the just-in-time (JIT) compiler instead.</span></span> <span data-ttu-id="b7b58-111">Nesse caso, o depurador ainda deve usar o método [ICorDebugModule2:: SetJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md) para definir os sinalizadores conforme desejado para a compilação JIT.</span><span class="sxs-lookup"><span data-stu-id="b7b58-111">In that case, the debugger must still use the [ICorDebugModule2::SetJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md) method to set the flags as desired for the JIT compilation.</span></span>  
  
 <span data-ttu-id="b7b58-112">Se uma imagem for carregada, mas alguma compilação JIT precisar ocorrer para essa imagem (que será o caso se a imagem contiver genéricos), os sinalizadores do compilador especificados pelo método `SetDesiredNGENCompilerFlags` serão aplicados à compilação adicional do JIT.</span><span class="sxs-lookup"><span data-stu-id="b7b58-112">If an image is loaded, but some JIT compiling must take place for that image (which will be the case if the image contains generics), the compiler flags specified by the `SetDesiredNGENCompilerFlags` method will apply to the extra JIT compilation.</span></span>  
  
 <span data-ttu-id="b7b58-113">O método `SetDesiredNGENCompilerFlags` deve ser chamado durante o retorno de chamada [ICorDebugManagedCallback:: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b7b58-113">The `SetDesiredNGENCompilerFlags` method must be called during the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="b7b58-114">As tentativas de chamar o método `SetDesiredNGENCompilerFlags` depois falharão.</span><span class="sxs-lookup"><span data-stu-id="b7b58-114">Attempts to call the `SetDesiredNGENCompilerFlags` method afterwards will fail.</span></span> <span data-ttu-id="b7b58-115">Além disso, as tentativas de definir sinalizadores que não estão definidos na enumeração `CorDebugJITCompilerFlags` ou não são legais para o processo especificado falharão.</span><span class="sxs-lookup"><span data-stu-id="b7b58-115">Also, attempts to set flags that are either not defined in the `CorDebugJITCompilerFlags` enumeration or are not legal for the given process will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7b58-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b7b58-116">Requirements</span></span>  
 <span data-ttu-id="b7b58-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7b58-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7b58-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b7b58-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7b58-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7b58-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7b58-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7b58-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7b58-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7b58-121">See also</span></span>

- [<span data-ttu-id="b7b58-122">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="b7b58-122">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="b7b58-123">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="b7b58-123">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
