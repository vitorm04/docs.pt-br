---
title: Método ICorProfilerInfo3::GetFunctionTailcall3Info
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionTailcall3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info
helpviewer_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info method [.NET Framework profiling]
- GetFunctionTailcall3Info method [.NET Framework profiling]
ms.assetid: afdb5ac9-5bf5-4b91-b7cb-f81db23d7da3
topic_type:
- apiref
ms.openlocfilehash: add89fe81fccbd5e6f5ad5d27f0ab3ace489963e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868519"
---
# <a name="icorprofilerinfo3getfunctiontailcall3info-method"></a><span data-ttu-id="9bfb8-102">Método ICorProfilerInfo3::GetFunctionTailcall3Info</span><span class="sxs-lookup"><span data-stu-id="9bfb8-102">ICorProfilerInfo3::GetFunctionTailcall3Info Method</span></span>
<span data-ttu-id="9bfb8-103">Fornece o quadro de pilha da função que está sendo reportada para o criador de perfil pela função [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) .</span><span class="sxs-lookup"><span data-stu-id="9bfb8-103">Provides the stack frame of the function that is being reported to the profiler by the [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) function.</span></span> <span data-ttu-id="9bfb8-104">Esse método pode ser chamado somente durante o retorno de chamada `FunctionTailcall3WithInfo`.</span><span class="sxs-lookup"><span data-stu-id="9bfb8-104">This method can be called only during the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bfb8-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9bfb8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionTailcall3Info(   
            [in]  FunctionID functionId,   
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9bfb8-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9bfb8-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="9bfb8-107">no A `FunctionID` da função que está retornando.</span><span class="sxs-lookup"><span data-stu-id="9bfb8-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="9bfb8-108">no Um identificador opaco que representa informações sobre um determinado registro de ativação.</span><span class="sxs-lookup"><span data-stu-id="9bfb8-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="9bfb8-109">O criador de perfil deve fornecer o mesmo `eltInfo` fornecido ao criador de perfil pela função `FunctionTailcall3WithInfo`.</span><span class="sxs-lookup"><span data-stu-id="9bfb8-109">The profiler should provide the same `eltInfo` that was given to the profiler by the `FunctionTailcall3WithInfo` function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="9bfb8-110">fora Um identificador opaco que representa informações genéricas sobre um determinado registro de ativação.</span><span class="sxs-lookup"><span data-stu-id="9bfb8-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="9bfb8-111">Esse identificador é válido somente durante o retorno de chamada `FunctionTailcall3WithInfo` no qual o criador de perfil chamou o método `GetFunctionTailcall3Info`.</span><span class="sxs-lookup"><span data-stu-id="9bfb8-111">This handle is valid only during the `FunctionTailcall3WithInfo` callback in which the profiler called the `GetFunctionTailcall3Info` method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9bfb8-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="9bfb8-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bfb8-113">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="9bfb8-113">Requirements</span></span>  
 <span data-ttu-id="9bfb8-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bfb8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bfb8-115">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9bfb8-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9bfb8-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9bfb8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9bfb8-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bfb8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bfb8-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="9bfb8-118">See also</span></span>

- [<span data-ttu-id="9bfb8-119">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="9bfb8-119">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="9bfb8-120">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="9bfb8-120">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="9bfb8-121">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="9bfb8-121">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="9bfb8-122">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="9bfb8-122">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="9bfb8-123">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="9bfb8-123">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="9bfb8-124">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="9bfb8-124">Profiling</span></span>](index.md)
