---
title: Método ICorProfilerCallback::AssemblyUnloadFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadFinished
helpviewer_keywords:
- AssemblyUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::AssemblyUnloadFinished method [.NET Framework profiling]
ms.assetid: 53fca564-84b1-44d4-9e21-17a492d2aae7
topic_type:
- apiref
ms.openlocfilehash: 734ae1d14d02d47c7d3126f1b4cf55dcb4ad151b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866618"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a><span data-ttu-id="146b4-102">Método ICorProfilerCallback::AssemblyUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="146b4-102">ICorProfilerCallback::AssemblyUnloadFinished Method</span></span>
<span data-ttu-id="146b4-103">Notifica o criador de perfil de que um assembly foi descarregado.</span><span class="sxs-lookup"><span data-stu-id="146b4-103">Notifies the profiler that an assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="146b4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="146b4-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="146b4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="146b4-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="146b4-106">\[em] identifica o assembly que está sendo descarregado.</span><span class="sxs-lookup"><span data-stu-id="146b4-106">\[in] Identifies the assembly that is being unloaded.</span></span>

- `hrStatus`

  <span data-ttu-id="146b4-107">\[em] um HRESULT que indica se o assembly foi descarregado com êxito.</span><span class="sxs-lookup"><span data-stu-id="146b4-107">\[in] An HRESULT that indicates whether the assembly was unloaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="146b4-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="146b4-108">Remarks</span></span>  
 <span data-ttu-id="146b4-109">O valor de `assemblyId` não é válido para uma solicitação de informações depois que o método [ICorProfilerCallback:: AssemblyUnloadStarted](icorprofilercallback-assemblyunloadstarted-method.md) retorna.</span><span class="sxs-lookup"><span data-stu-id="146b4-109">The value of `assemblyId` is not valid for an information request after the [ICorProfilerCallback::AssemblyUnloadStarted](icorprofilercallback-assemblyunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="146b4-110">Algumas partes do descarregamento do assembly podem continuar após o retorno de chamada `AssemblyUnloadFinished`.</span><span class="sxs-lookup"><span data-stu-id="146b4-110">Some parts of unloading the assembly might continue after the `AssemblyUnloadFinished` callback.</span></span> <span data-ttu-id="146b4-111">Uma falha HRESULT no `hrStatus` indica uma falha.</span><span class="sxs-lookup"><span data-stu-id="146b4-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="146b4-112">No entanto, um HRESULT de êxito em `hrStatus` indica apenas que a primeira parte do descarregamento do assembly foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="146b4-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="146b4-113">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="146b4-113">Requirements</span></span>  
 <span data-ttu-id="146b4-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="146b4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="146b4-115">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="146b4-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="146b4-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="146b4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="146b4-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="146b4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="146b4-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="146b4-118">See also</span></span>

- [<span data-ttu-id="146b4-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="146b4-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
