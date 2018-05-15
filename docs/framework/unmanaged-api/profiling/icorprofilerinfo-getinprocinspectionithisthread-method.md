---
title: Método ICorProfilerInfo::GetInprocInspectionIThisThread
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetInprocInspectionIThisThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread
helpviewer_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread method [.NET Framework profiling]
- GetInprocInspectionIThisThread method [.NET Framework profiling]
ms.assetid: badddccd-f85c-416e-9f0f-419eab2c9d42
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6d603d9bc7a343a41224cf8d889a69823875d9db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfogetinprocinspectionithisthread-method"></a><span data-ttu-id="9a783-102">Método ICorProfilerInfo::GetInprocInspectionIThisThread</span><span class="sxs-lookup"><span data-stu-id="9a783-102">ICorProfilerInfo::GetInprocInspectionIThisThread Method</span></span>
<span data-ttu-id="9a783-103">Obtém um objeto que pode ser consultado para a interface ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="9a783-103">Gets an object that can be queried for the ICorDebugThread interface.</span></span> <span data-ttu-id="9a783-104">Este método está obsoleto no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="9a783-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a783-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9a783-105">Syntax</span></span>  
  
```  
HRESULT GetInprocInspectionIThisThread(  
    [out] IUnknown **ppicd);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9a783-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9a783-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="9a783-107">[out](/cpp/atl/iunknown) objeto que pode ser consultado para o `ICorDebugThread` interface.</span><span class="sxs-lookup"><span data-stu-id="9a783-107">[out](/cpp/atl/iunknown) object that can be queried for the `ICorDebugThread` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a783-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="9a783-108">Remarks</span></span>  
 <span data-ttu-id="9a783-109">O common language runtime (CLR) serviços de depuração tem suporte limitado em processo depuração do .NET Framework versão 1.0.</span><span class="sxs-lookup"><span data-stu-id="9a783-109">The common language runtime (CLR) debugging services supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="9a783-110">No processo de depuração habilitado um criador de perfil usar as partes de inspeção da API de depuração.</span><span class="sxs-lookup"><span data-stu-id="9a783-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="9a783-111">Como resultado de comentários do cliente, no processo de depuração foi removido do .NET Framework versão 2.0 e substituído por um conjunto de funcionalidades mais alinhados com a API de criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="9a783-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a783-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9a783-112">Requirements</span></span>  
 <span data-ttu-id="9a783-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a783-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a783-114">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9a783-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9a783-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a783-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a783-116">**Versão do .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="9a783-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a783-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9a783-117">See Also</span></span>  
 [<span data-ttu-id="9a783-118">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="9a783-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
