---
title: "Método ICorProfilerInfo::GetHandleFromThread"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetHandleFromThread
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetHandleFromThread
helpviewer_keywords:
- GetHandleFromThread method [.NET Framework profiling]
- ICorProfilerInfo::GetHandleFromThread method [.NET Framework profiling]
ms.assetid: 36cdc9f5-7579-4cd2-aa36-fc05c741584c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: be925bbbcc86785feae28353dbc6563974aae2c1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogethandlefromthread-method"></a><span data-ttu-id="ba699-102">Método ICorProfilerInfo::GetHandleFromThread</span><span class="sxs-lookup"><span data-stu-id="ba699-102">ICorProfilerInfo::GetHandleFromThread Method</span></span>
<span data-ttu-id="ba699-103">A ID de um thread é mapeado para um identificador de thread Win32.</span><span class="sxs-lookup"><span data-stu-id="ba699-103">Maps the ID of a thread to a Win32 thread handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba699-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ba699-104">Syntax</span></span>  
  
```  
HRESULT GetHandleFromThread(  
    [in]  ThreadID threadId,  
    [out] HANDLE  *phThread);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ba699-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ba699-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="ba699-106">[in] A ID do thread a ser mapeada.</span><span class="sxs-lookup"><span data-stu-id="ba699-106">[in] The thread ID to be mapped.</span></span>  
  
 `phThread`  
 <span data-ttu-id="ba699-107">[out] Um ponteiro para um identificador de thread Win32.</span><span class="sxs-lookup"><span data-stu-id="ba699-107">[out] A pointer to a Win32 thread handle.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba699-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="ba699-108">Remarks</span></span>  
 <span data-ttu-id="ba699-109">O criador de perfil deve chamar o Win32 `DuplicateHandle` função no identificador do antes de usá-lo.</span><span class="sxs-lookup"><span data-stu-id="ba699-109">The profiler must call the Win32 `DuplicateHandle` function on the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba699-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ba699-110">Requirements</span></span>  
 <span data-ttu-id="ba699-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba699-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba699-112">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ba699-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ba699-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba699-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba699-114">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba699-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba699-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ba699-115">See Also</span></span>  
 [<span data-ttu-id="ba699-116">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="ba699-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
