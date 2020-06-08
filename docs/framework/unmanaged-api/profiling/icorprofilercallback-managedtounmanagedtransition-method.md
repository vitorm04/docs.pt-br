---
title: Método ICorProfilerCallback::ManagedToUnmanagedTransition
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ManagedToUnmanagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ManagedToUnmanagedTransition
helpviewer_keywords:
- ManagedToUnmanagedTransition method [.NET Framework profiling]
- ICorProfilerCallback::ManagedToUnmanagedTransition method [.NET Framework profiling]
ms.assetid: ef3cd619-912d-40c5-a449-03ba02a39ee7
topic_type:
- apiref
ms.openlocfilehash: 9b53030fe860e02b0afd0dce3055ac3cf29e3491
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499994"
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a><span data-ttu-id="dd6b4-102">Método ICorProfilerCallback::ManagedToUnmanagedTransition</span><span class="sxs-lookup"><span data-stu-id="dd6b4-102">ICorProfilerCallback::ManagedToUnmanagedTransition Method</span></span>
<span data-ttu-id="dd6b4-103">Notifica o criador de perfil de que uma transição do código gerenciado para o código não gerenciado ocorreu.</span><span class="sxs-lookup"><span data-stu-id="dd6b4-103">Notifies the profiler that a transition from managed code to unmanaged code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd6b4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dd6b4-104">Syntax</span></span>  
  
```cpp  
HRESULT ManagedToUnmanagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd6b4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dd6b4-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="dd6b4-106">no A ID da função que está sendo chamada.</span><span class="sxs-lookup"><span data-stu-id="dd6b4-106">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="dd6b4-107">no Um valor da enumeração [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) que indica se a transição ocorreu devido a uma chamada em código não gerenciado do código gerenciado ou devido a um retorno de uma função gerenciada chamada por um não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="dd6b4-107">[in] A value of the [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into unmanaged code from managed code, or because of a return from a managed function called by an unmanaged one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd6b4-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="dd6b4-108">Remarks</span></span>  
 <span data-ttu-id="dd6b4-109">Se o valor de `reason` for COR_PRF_TRANSITION_CALL, a ID da função será a da função não gerenciada, que nunca terá sido compilada usando o compilador just-in-time.</span><span class="sxs-lookup"><span data-stu-id="dd6b4-109">If the value of `reason` is COR_PRF_TRANSITION_CALL, the function ID is that of the unmanaged function, which will never have been compiled using the just-in-time compiler.</span></span> <span data-ttu-id="dd6b4-110">As funções não gerenciadas têm informações básicas associadas a elas, como um nome e alguns metadados.</span><span class="sxs-lookup"><span data-stu-id="dd6b4-110">Unmanaged functions have basic information associated with them, such as a name and some metadata.</span></span> <span data-ttu-id="dd6b4-111">Se a função não gerenciada for chamada usando o PInvoke (chamada de plataforma implícita), o tempo de execução não poderá determinar o destino da chamada e o valor de `functionId` será NULL.</span><span class="sxs-lookup"><span data-stu-id="dd6b4-111">If the unmanaged function was called by using implicit platform invoke (PInvoke), the runtime cannot determine the destination of the call and the value of `functionId` will be null.</span></span> <span data-ttu-id="dd6b4-112">Para obter mais informações sobre o PInvoke implícito, consulte [usando a interoperabilidade C++ (PInvoke implícito)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).</span><span class="sxs-lookup"><span data-stu-id="dd6b4-112">For more information on implicit PInvoke, see [Using C++ Interop (Implicit PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd6b4-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dd6b4-113">Requirements</span></span>  
 <span data-ttu-id="dd6b4-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd6b4-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd6b4-115">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="dd6b4-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dd6b4-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dd6b4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd6b4-117">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd6b4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd6b4-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="dd6b4-118">See also</span></span>

- [<span data-ttu-id="dd6b4-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="dd6b4-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="dd6b4-120">Método UnmanagedToManagedTransition</span><span class="sxs-lookup"><span data-stu-id="dd6b4-120">UnmanagedToManagedTransition Method</span></span>](icorprofilercallback-unmanagedtomanagedtransition-method.md)
- [<span data-ttu-id="dd6b4-121">Usando o PInvoke explícito em C++ (atributo DllImport)</span><span class="sxs-lookup"><span data-stu-id="dd6b4-121">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
