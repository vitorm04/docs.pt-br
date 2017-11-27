---
title: "Método ICorDebugProcess2::SetDesiredNGENCompilerFlags"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess2.SetDesiredNGENCompilerFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess2::SetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags method [.NET Framework debugging]
- SetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: 98320175-7c5e-4dbb-8683-86fa82e2641f
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 278f1f79fd929aa8a0c3233e68b30b1154e913ef
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a><span data-ttu-id="1f98e-102">Método ICorDebugProcess2::SetDesiredNGENCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="1f98e-102">ICorDebugProcess2::SetDesiredNGENCompilerFlags Method</span></span>
<span data-ttu-id="1f98e-103">Define os sinalizadores que devem ser inseridos em uma imagem pré-compilado em ordem para o tempo de execução carregar a imagem no processo atual.</span><span class="sxs-lookup"><span data-stu-id="1f98e-103">Sets the flags that must be embedded in a precompiled image in order for the runtime to load that image into the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f98e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1f98e-104">Syntax</span></span>  
  
```  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1f98e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1f98e-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="1f98e-106">[in] Um valor de [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeração que especifica os sinalizadores de compilador usada para selecionar a imagem correta de pré-compilada.</span><span class="sxs-lookup"><span data-stu-id="1f98e-106">[in] A value of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration that specifies the compiler flags used to select the correct pre-compiled image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f98e-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="1f98e-107">Remarks</span></span>  
 <span data-ttu-id="1f98e-108">O `SetDesiredNGENCompilerFlags` método Especifica os sinalizadores que devem ser inseridos em uma imagem pré-compilado, para que o tempo de execução será carregado se a imagem nesse processo.</span><span class="sxs-lookup"><span data-stu-id="1f98e-108">The `SetDesiredNGENCompilerFlags` method specifies the flags that must be embedded in a precompiled image so that the runtime will load that image into this process.</span></span> <span data-ttu-id="1f98e-109">Os sinalizadores definidos por esse método são usados apenas para selecionar a imagem pré-compilado correta.</span><span class="sxs-lookup"><span data-stu-id="1f98e-109">The flags set by this method are used only to select the correct precompiled image.</span></span> <span data-ttu-id="1f98e-110">Se essa imagem não existir, o tempo de execução carregará a imagem do Microsoft intermediate language (MSIL) e o compilador just-in-time (JIT) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="1f98e-110">If no such image exists, the runtime will load the Microsoft intermediate language (MSIL) image and the just-in-time (JIT) compiler instead.</span></span> <span data-ttu-id="1f98e-111">Nesse caso, o depurador ainda deve usar o [Icordebugmodule2](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md) método para definir os sinalizadores conforme desejado para a compilação JIT.</span><span class="sxs-lookup"><span data-stu-id="1f98e-111">In that case, the debugger must still use the [ICorDebugModule2::SetJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md) method to set the flags as desired for the JIT compilation.</span></span>  
  
 <span data-ttu-id="1f98e-112">Se uma imagem é carregada, mas alguns compilação JIT deve ser realizadas para essa imagem (que será o caso se a imagem contém genéricos), os sinalizadores de compilador especificados pelo `SetDesiredNGENCompilerFlags` método aplicará a compilação JIT extra.</span><span class="sxs-lookup"><span data-stu-id="1f98e-112">If an image is loaded, but some JIT compiling must take place for that image (which will be the case if the image contains generics), the compiler flags specified by the `SetDesiredNGENCompilerFlags` method will apply to the extra JIT compilation.</span></span>  
  
 <span data-ttu-id="1f98e-113">O `SetDesiredNGENCompilerFlags` método deve ser chamado durante a [Icordebugmanagedcallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="1f98e-113">The `SetDesiredNGENCompilerFlags` method must be called during the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="1f98e-114">Tentativas de chamar o `SetDesiredNGENCompilerFlags` método posteriormente falhará.</span><span class="sxs-lookup"><span data-stu-id="1f98e-114">Attempts to call the `SetDesiredNGENCompilerFlags` method afterwards will fail.</span></span> <span data-ttu-id="1f98e-115">Além disso, as tentativas de definir os sinalizadores que não estão definidos no `CorDebugJITCompilerFlags` enumeração ou são ilegal para determinado processo falhará.</span><span class="sxs-lookup"><span data-stu-id="1f98e-115">Also, attempts to set flags that are either not defined in the `CorDebugJITCompilerFlags` enumeration or are not legal for the given process will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f98e-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1f98e-116">Requirements</span></span>  
 <span data-ttu-id="1f98e-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f98e-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f98e-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1f98e-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f98e-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f98e-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f98e-120">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f98e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f98e-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1f98e-121">See Also</span></span>  
 [<span data-ttu-id="1f98e-122">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="1f98e-122">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [<span data-ttu-id="1f98e-123">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="1f98e-123">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
