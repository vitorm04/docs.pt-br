---
title: Método ICorProfilerInfo::BeginInprocDebugging
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3e23f39f8e7a1812366e15ffec9589f756c73f94
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481680"
---
# <a name="icorprofilerinfobegininprocdebugging-method"></a><span data-ttu-id="11fa2-102">Método ICorProfilerInfo::BeginInprocDebugging</span><span class="sxs-lookup"><span data-stu-id="11fa2-102">ICorProfilerInfo::BeginInprocDebugging Method</span></span>
<span data-ttu-id="11fa2-103">Inicializa suporte à depuração em processo.</span><span class="sxs-lookup"><span data-stu-id="11fa2-103">Initializes in-process debugging support.</span></span> <span data-ttu-id="11fa2-104">Este método é obsoleto no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="11fa2-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11fa2-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="11fa2-105">Syntax</span></span>  
  
```  
HRESULT BeginInprocDebugging(  
    [in]  BOOL   fThisThreadOnly,  
    [out] DWORD *pdwProfilerContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11fa2-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="11fa2-106">Parameters</span></span>  
 `fThisThreadOnly`  
 <span data-ttu-id="11fa2-107">[in] Defina esse valor como `true` para inicializar o suporte à depuração de apenas o thread atual; defina-a como `false` para inicializar o suporte à depuração de todos os threads.</span><span class="sxs-lookup"><span data-stu-id="11fa2-107">[in] Set this value to `true` to initialize debugging support for only the current thread; set it to `false` to initialize debugging support for all threads.</span></span>  
  
 `pdwProfilerContext`  
 <span data-ttu-id="11fa2-108">[out] O ponteiro para um valor retornado que identifica a sessão de depuração.</span><span class="sxs-lookup"><span data-stu-id="11fa2-108">[out] The pointer to a returned value that identifies the debugging session.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11fa2-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="11fa2-109">Remarks</span></span>  
 <span data-ttu-id="11fa2-110">Os serviços de depuração do CLR tem suporte limitado em processo depuração nas versões do .NET Framework 1.0 e 1.1.</span><span class="sxs-lookup"><span data-stu-id="11fa2-110">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="11fa2-111">No processo de depuração habilitado um criador de perfil usar as partes de inspeção da API de depuração.</span><span class="sxs-lookup"><span data-stu-id="11fa2-111">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="11fa2-112">No entanto, devido a comentários dos clientes, no processo de depuração foi removido do .NET Framework versão 2.0 e substituída por um conjunto de funcionalidade que é mais alinhada com a API de criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="11fa2-112">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11fa2-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="11fa2-113">Requirements</span></span>  
 <span data-ttu-id="11fa2-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11fa2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11fa2-115">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="11fa2-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="11fa2-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11fa2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11fa2-117">**Versão do .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="11fa2-117">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11fa2-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="11fa2-118">See also</span></span>
- [<span data-ttu-id="11fa2-119">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="11fa2-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
