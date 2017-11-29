---
title: "Método ICorProfilerInfo::GetInprocInspectionIThisThread"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetInprocInspectionIThisThread
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetInprocInspectionIThisThread
helpviewer_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread method [.NET Framework profiling]
- GetInprocInspectionIThisThread method [.NET Framework profiling]
ms.assetid: badddccd-f85c-416e-9f0f-419eab2c9d42
topic_type: apiref
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9a260143e36939f4201d7949f5783f80e5c20ba7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogetinprocinspectionithisthread-method"></a><span data-ttu-id="e8173-102">Método ICorProfilerInfo::GetInprocInspectionIThisThread</span><span class="sxs-lookup"><span data-stu-id="e8173-102">ICorProfilerInfo::GetInprocInspectionIThisThread Method</span></span>
<span data-ttu-id="e8173-103">Obtém um objeto que pode ser consultado para a interface ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="e8173-103">Gets an object that can be queried for the ICorDebugThread interface.</span></span> <span data-ttu-id="e8173-104">Este método está obsoleto no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="e8173-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8173-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e8173-105">Syntax</span></span>  
  
```  
HRESULT GetInprocInspectionIThisThread(  
    [out] IUnknown **ppicd);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e8173-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e8173-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="e8173-107">[out](/cpp/atl/iunknown) objeto que pode ser consultado para o `ICorDebugThread` interface.</span><span class="sxs-lookup"><span data-stu-id="e8173-107">[out](/cpp/atl/iunknown) object that can be queried for the `ICorDebugThread` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8173-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="e8173-108">Remarks</span></span>  
 <span data-ttu-id="e8173-109">O common language runtime (CLR) serviços de depuração tem suporte limitado em processo depuração do .NET Framework versão 1.0.</span><span class="sxs-lookup"><span data-stu-id="e8173-109">The common language runtime (CLR) debugging services supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="e8173-110">No processo de depuração habilitado um criador de perfil usar as partes de inspeção da API de depuração.</span><span class="sxs-lookup"><span data-stu-id="e8173-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="e8173-111">Como resultado de comentários do cliente, no processo de depuração foi removido do .NET Framework versão 2.0 e substituído por um conjunto de funcionalidades mais alinhados com a API de criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="e8173-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8173-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e8173-112">Requirements</span></span>  
 <span data-ttu-id="e8173-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8173-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8173-114">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e8173-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e8173-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8173-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8173-116">**Versão do .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="e8173-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8173-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e8173-117">See Also</span></span>  
 [<span data-ttu-id="e8173-118">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="e8173-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
