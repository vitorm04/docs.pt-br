---
title: Método ICorProfilerInfo::GetHandleFromThread
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetHandleFromThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetHandleFromThread
helpviewer_keywords:
- GetHandleFromThread method [.NET Framework profiling]
- ICorProfilerInfo::GetHandleFromThread method [.NET Framework profiling]
ms.assetid: 36cdc9f5-7579-4cd2-aa36-fc05c741584c
topic_type:
- apiref
ms.openlocfilehash: 419195d9450bf07e5ad8c7cedcac76e175137c96
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498174"
---
# <a name="icorprofilerinfogethandlefromthread-method"></a><span data-ttu-id="0d11c-102">Método ICorProfilerInfo::GetHandleFromThread</span><span class="sxs-lookup"><span data-stu-id="0d11c-102">ICorProfilerInfo::GetHandleFromThread Method</span></span>
<span data-ttu-id="0d11c-103">Mapeia a ID de um thread para um identificador de thread do Win32.</span><span class="sxs-lookup"><span data-stu-id="0d11c-103">Maps the ID of a thread to a Win32 thread handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d11c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0d11c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandleFromThread(  
    [in]  ThreadID threadId,  
    [out] HANDLE  *phThread);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d11c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0d11c-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="0d11c-106">no A ID do thread a ser mapeada.</span><span class="sxs-lookup"><span data-stu-id="0d11c-106">[in] The thread ID to be mapped.</span></span>  
  
 `phThread`  
 <span data-ttu-id="0d11c-107">fora Um ponteiro para um identificador de Thread Win32.</span><span class="sxs-lookup"><span data-stu-id="0d11c-107">[out] A pointer to a Win32 thread handle.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d11c-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="0d11c-108">Remarks</span></span>  
 <span data-ttu-id="0d11c-109">O criador de perfil deve chamar a função do Win32 `DuplicateHandle` na alça antes de usá-la.</span><span class="sxs-lookup"><span data-stu-id="0d11c-109">The profiler must call the Win32 `DuplicateHandle` function on the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d11c-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0d11c-110">Requirements</span></span>  
 <span data-ttu-id="0d11c-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d11c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d11c-112">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0d11c-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0d11c-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d11c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d11c-114">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d11c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d11c-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="0d11c-115">See also</span></span>

- [<span data-ttu-id="0d11c-116">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="0d11c-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
