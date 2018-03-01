---
title: "Método ICorProfilerInfo::BeginInprocDebugging"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerInfo.BeginInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::BeginInprocDebugging
helpviewer_keywords:
- BeginInprocDebugging method [.NET Framework profiling]
- ICorProfilerInfo::BeginInprocDebugging method [.NET Framework profiling]
ms.assetid: c5c82c69-99f8-4447-aee0-42cca0a5eb5c
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 91306bbea7b099f7e9e408f8bf69625f1d7da68e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfobegininprocdebugging-method"></a><span data-ttu-id="e953e-102">Método ICorProfilerInfo::BeginInprocDebugging</span><span class="sxs-lookup"><span data-stu-id="e953e-102">ICorProfilerInfo::BeginInprocDebugging Method</span></span>
<span data-ttu-id="e953e-103">Inicializa suporte à depuração no processo.</span><span class="sxs-lookup"><span data-stu-id="e953e-103">Initializes in-process debugging support.</span></span> <span data-ttu-id="e953e-104">Este método está obsoleto no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="e953e-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e953e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e953e-105">Syntax</span></span>  
  
```  
HRESULT BeginInprocDebugging(  
    [in]  BOOL   fThisThreadOnly,  
    [out] DWORD *pdwProfilerContext);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e953e-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e953e-106">Parameters</span></span>  
 `fThisThreadOnly`  
 <span data-ttu-id="e953e-107">[in] Defina esse valor como `true` para inicializar o suporte à depuração somente do thread atual; defina-a como `false` para inicializar o suporte à depuração de todos os threads.</span><span class="sxs-lookup"><span data-stu-id="e953e-107">[in] Set this value to `true` to initialize debugging support for only the current thread; set it to `false` to initialize debugging support for all threads.</span></span>  
  
 `pdwProfilerContext`  
 <span data-ttu-id="e953e-108">[out] O ponteiro para um valor retornado que identifica a sessão de depuração.</span><span class="sxs-lookup"><span data-stu-id="e953e-108">[out] The pointer to a returned value that identifies the debugging session.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e953e-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="e953e-109">Remarks</span></span>  
 <span data-ttu-id="e953e-110">Os serviços de depuração do CLR tem suporte limitado depuração em andamento nas versões do .NET Framework 1.0 e 1.1.</span><span class="sxs-lookup"><span data-stu-id="e953e-110">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="e953e-111">No processo de depuração habilitado um criador de perfil usar as partes de inspeção da API de depuração.</span><span class="sxs-lookup"><span data-stu-id="e953e-111">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="e953e-112">No entanto, devido a comentários dos clientes, no processo de depuração foi removido do .NET Framework versão 2.0 e substituído por um conjunto de funcionalidades mais alinhados com a API de criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="e953e-112">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e953e-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e953e-113">Requirements</span></span>  
 <span data-ttu-id="e953e-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e953e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e953e-115">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e953e-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e953e-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e953e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e953e-117">**Versão do .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="e953e-117">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e953e-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e953e-118">See Also</span></span>  
 [<span data-ttu-id="e953e-119">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="e953e-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
