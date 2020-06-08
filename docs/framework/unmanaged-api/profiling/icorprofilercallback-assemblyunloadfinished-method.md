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
ms.openlocfilehash: d00e67d29921edc6b7487ceeb12aaa9e9f9bd0ac
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500410"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a><span data-ttu-id="d2fae-102">Método ICorProfilerCallback::AssemblyUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="d2fae-102">ICorProfilerCallback::AssemblyUnloadFinished Method</span></span>
<span data-ttu-id="d2fae-103">Notifica o criador de perfil de que um assembly foi descarregado.</span><span class="sxs-lookup"><span data-stu-id="d2fae-103">Notifies the profiler that an assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2fae-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d2fae-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2fae-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d2fae-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="d2fae-106">\[in] identifica o assembly que está sendo descarregado.</span><span class="sxs-lookup"><span data-stu-id="d2fae-106">\[in] Identifies the assembly that is being unloaded.</span></span>

- `hrStatus`

  <span data-ttu-id="d2fae-107">\[in] um HRESULT que indica se o assembly foi descarregado com êxito.</span><span class="sxs-lookup"><span data-stu-id="d2fae-107">\[in] An HRESULT that indicates whether the assembly was unloaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="d2fae-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="d2fae-108">Remarks</span></span>  
 <span data-ttu-id="d2fae-109">O valor de `assemblyId` não é válido para uma solicitação de informações depois que o método [ICorProfilerCallback:: AssemblyUnloadStarted](icorprofilercallback-assemblyunloadstarted-method.md) retorna.</span><span class="sxs-lookup"><span data-stu-id="d2fae-109">The value of `assemblyId` is not valid for an information request after the [ICorProfilerCallback::AssemblyUnloadStarted](icorprofilercallback-assemblyunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="d2fae-110">Algumas partes do descarregamento do assembly podem continuar após o `AssemblyUnloadFinished` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="d2fae-110">Some parts of unloading the assembly might continue after the `AssemblyUnloadFinished` callback.</span></span> <span data-ttu-id="d2fae-111">Um HRESULT de falha em `hrStatus` indica uma falha.</span><span class="sxs-lookup"><span data-stu-id="d2fae-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="d2fae-112">No entanto, um HRESULT de êxito em `hrStatus` indica apenas que a primeira parte do descarregamento do assembly foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="d2fae-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2fae-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d2fae-113">Requirements</span></span>  
 <span data-ttu-id="d2fae-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2fae-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2fae-115">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d2fae-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d2fae-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d2fae-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2fae-117">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2fae-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2fae-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="d2fae-118">See also</span></span>

- [<span data-ttu-id="d2fae-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="d2fae-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
