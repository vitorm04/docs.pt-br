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
ms.openlocfilehash: 366a48e5f6abd92f0c6f796f40bdd263181da4a8
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213472"
---
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a><span data-ttu-id="95e2e-102">Método ICorDebugProcess2::SetDesiredNGENCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="95e2e-102">ICorDebugProcess2::SetDesiredNGENCompilerFlags Method</span></span>
<span data-ttu-id="95e2e-103">Define os sinalizadores que devem ser inseridos em uma imagem pré-compilada para que o tempo de execução carregue essa imagem no processo atual.</span><span class="sxs-lookup"><span data-stu-id="95e2e-103">Sets the flags that must be embedded in a precompiled image in order for the runtime to load that image into the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95e2e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="95e2e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95e2e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="95e2e-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="95e2e-106">no Um valor da enumeração [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) que especifica os sinalizadores de compilador usados para selecionar a imagem previamente compilada correta.</span><span class="sxs-lookup"><span data-stu-id="95e2e-106">[in] A value of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration that specifies the compiler flags used to select the correct pre-compiled image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95e2e-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="95e2e-107">Remarks</span></span>  
 <span data-ttu-id="95e2e-108">O `SetDesiredNGENCompilerFlags` método especifica os sinalizadores que devem ser inseridos em uma imagem pré-compilada para que o tempo de execução carregue essa imagem nesse processo.</span><span class="sxs-lookup"><span data-stu-id="95e2e-108">The `SetDesiredNGENCompilerFlags` method specifies the flags that must be embedded in a precompiled image so that the runtime will load that image into this process.</span></span> <span data-ttu-id="95e2e-109">Os sinalizadores definidos por esse método são usados apenas para selecionar a imagem pré-compilada correta.</span><span class="sxs-lookup"><span data-stu-id="95e2e-109">The flags set by this method are used only to select the correct precompiled image.</span></span> <span data-ttu-id="95e2e-110">Se essa imagem não existir, o tempo de execução carregará a imagem do Microsoft Intermediate Language (MSIL) e o compilador JIT (just-in-time).</span><span class="sxs-lookup"><span data-stu-id="95e2e-110">If no such image exists, the runtime will load the Microsoft intermediate language (MSIL) image and the just-in-time (JIT) compiler instead.</span></span> <span data-ttu-id="95e2e-111">Nesse caso, o depurador ainda deve usar o método [ICorDebugModule2:: SetJITCompilerFlags](icordebugmodule2-setjitcompilerflags-method.md) para definir os sinalizadores conforme desejado para a compilação JIT.</span><span class="sxs-lookup"><span data-stu-id="95e2e-111">In that case, the debugger must still use the [ICorDebugModule2::SetJITCompilerFlags](icordebugmodule2-setjitcompilerflags-method.md) method to set the flags as desired for the JIT compilation.</span></span>  
  
 <span data-ttu-id="95e2e-112">Se uma imagem for carregada, mas alguma compilação JIT precisar ocorrer para essa imagem (que será o caso se a imagem contiver genéricos), os sinalizadores do compilador especificados pelo `SetDesiredNGENCompilerFlags` método serão aplicados à compilação adicional do JIT.</span><span class="sxs-lookup"><span data-stu-id="95e2e-112">If an image is loaded, but some JIT compiling must take place for that image (which will be the case if the image contains generics), the compiler flags specified by the `SetDesiredNGENCompilerFlags` method will apply to the extra JIT compilation.</span></span>  
  
 <span data-ttu-id="95e2e-113">O `SetDesiredNGENCompilerFlags` método deve ser chamado durante o retorno de chamada [ICorDebugManagedCallback:: CreateProcess](icordebugmanagedcallback-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="95e2e-113">The `SetDesiredNGENCompilerFlags` method must be called during the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="95e2e-114">Haverá falha nas tentativas de chamar o `SetDesiredNGENCompilerFlags` método posteriormente.</span><span class="sxs-lookup"><span data-stu-id="95e2e-114">Attempts to call the `SetDesiredNGENCompilerFlags` method afterwards will fail.</span></span> <span data-ttu-id="95e2e-115">Além disso, as tentativas de definir sinalizadores que não estão definidos na `CorDebugJITCompilerFlags` enumeração ou não são legais para o processo especificado falharão.</span><span class="sxs-lookup"><span data-stu-id="95e2e-115">Also, attempts to set flags that are either not defined in the `CorDebugJITCompilerFlags` enumeration or are not legal for the given process will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95e2e-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="95e2e-116">Requirements</span></span>  
 <span data-ttu-id="95e2e-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95e2e-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95e2e-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="95e2e-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="95e2e-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95e2e-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95e2e-120">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95e2e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95e2e-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="95e2e-121">See also</span></span>

- [<span data-ttu-id="95e2e-122">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="95e2e-122">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="95e2e-123">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="95e2e-123">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
