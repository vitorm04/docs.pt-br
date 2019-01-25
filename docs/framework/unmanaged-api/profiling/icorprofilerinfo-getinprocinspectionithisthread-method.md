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
ms.openlocfilehash: 019a85d6d58c99adb7c16be5cc3b31b029b0312d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54513122"
---
# <a name="icorprofilerinfogetinprocinspectionithisthread-method"></a><span data-ttu-id="fb71b-102">Método ICorProfilerInfo::GetInprocInspectionIThisThread</span><span class="sxs-lookup"><span data-stu-id="fb71b-102">ICorProfilerInfo::GetInprocInspectionIThisThread Method</span></span>
<span data-ttu-id="fb71b-103">Obtém um objeto que pode ser consultado para a interface ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="fb71b-103">Gets an object that can be queried for the ICorDebugThread interface.</span></span> <span data-ttu-id="fb71b-104">Este método é obsoleto no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="fb71b-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb71b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fb71b-105">Syntax</span></span>  
  
```  
HRESULT GetInprocInspectionIThisThread(  
    [out] IUnknown **ppicd);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fb71b-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fb71b-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="fb71b-107">[-out](/cpp/atl/iunknown) objeto que pode ser consultado para o `ICorDebugThread` interface.</span><span class="sxs-lookup"><span data-stu-id="fb71b-107">[out](/cpp/atl/iunknown) object that can be queried for the `ICorDebugThread` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb71b-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="fb71b-108">Remarks</span></span>  
 <span data-ttu-id="fb71b-109">O common language runtime (CLR) depurando serviços de suporte para depuração em andamento limitados no .NET Framework versão 1.0.</span><span class="sxs-lookup"><span data-stu-id="fb71b-109">The common language runtime (CLR) debugging services supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="fb71b-110">No processo de depuração habilitado um criador de perfil usar as partes de inspeção da API de depuração.</span><span class="sxs-lookup"><span data-stu-id="fb71b-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="fb71b-111">Como resultado de comentários do cliente, no processo de depuração foi removido do .NET Framework versão 2.0 e substituída por um conjunto de funcionalidade que é mais alinhada com a API de criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="fb71b-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb71b-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fb71b-112">Requirements</span></span>  
 <span data-ttu-id="fb71b-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb71b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb71b-114">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fb71b-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fb71b-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb71b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb71b-116">**Versão do .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="fb71b-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb71b-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fb71b-117">See also</span></span>
- [<span data-ttu-id="fb71b-118">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="fb71b-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
