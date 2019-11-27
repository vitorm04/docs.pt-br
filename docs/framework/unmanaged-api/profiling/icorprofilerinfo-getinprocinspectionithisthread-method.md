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
ms.openlocfilehash: bcc324d0f5cd14e1de9f02c8e6844a5868b70e8b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438904"
---
# <a name="icorprofilerinfogetinprocinspectionithisthread-method"></a><span data-ttu-id="3e7f2-102">Método ICorProfilerInfo::GetInprocInspectionIThisThread</span><span class="sxs-lookup"><span data-stu-id="3e7f2-102">ICorProfilerInfo::GetInprocInspectionIThisThread Method</span></span>
<span data-ttu-id="3e7f2-103">Obtém um objeto que pode ser consultado para a interface ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="3e7f2-103">Gets an object that can be queried for the ICorDebugThread interface.</span></span> <span data-ttu-id="3e7f2-104">Esse método é obsoleto no .NET Framework versão 2,0.</span><span class="sxs-lookup"><span data-stu-id="3e7f2-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e7f2-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3e7f2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInprocInspectionIThisThread(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e7f2-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3e7f2-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="3e7f2-107">objeto de [saída](/cpp/atl/iunknown) que pode ser consultado para a interface `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="3e7f2-107">[out](/cpp/atl/iunknown) object that can be queried for the `ICorDebugThread` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e7f2-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="3e7f2-108">Remarks</span></span>  
 <span data-ttu-id="3e7f2-109">Os serviços de depuração Common Language Runtime (CLR) com suporte para a depuração em processo limitada na versão .NET Framework 1,0.</span><span class="sxs-lookup"><span data-stu-id="3e7f2-109">The common language runtime (CLR) debugging services supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="3e7f2-110">A depuração em processo habilitou um criador de perfil para usar as partes de inspeção da API de depuração.</span><span class="sxs-lookup"><span data-stu-id="3e7f2-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="3e7f2-111">Como resultado dos comentários dos clientes, a depuração em processo foi removida da .NET Framework na versão 2,0 e substituída por um conjunto de funcionalidades que está mais alinhado com a API de criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="3e7f2-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e7f2-112">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="3e7f2-112">Requirements</span></span>  
 <span data-ttu-id="3e7f2-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e7f2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e7f2-114">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3e7f2-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3e7f2-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e7f2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e7f2-116">**Versão do .NET Framework:** 1,0</span><span class="sxs-lookup"><span data-stu-id="3e7f2-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e7f2-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e7f2-117">See also</span></span>

- [<span data-ttu-id="3e7f2-118">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="3e7f2-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
