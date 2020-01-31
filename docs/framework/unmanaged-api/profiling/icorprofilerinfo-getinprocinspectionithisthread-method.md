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
ms.openlocfilehash: 0ab383f0968061667b3580a2058687eecda99dde
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76869992"
---
# <a name="icorprofilerinfogetinprocinspectionithisthread-method"></a><span data-ttu-id="0d38c-102">Método ICorProfilerInfo::GetInprocInspectionIThisThread</span><span class="sxs-lookup"><span data-stu-id="0d38c-102">ICorProfilerInfo::GetInprocInspectionIThisThread Method</span></span>
<span data-ttu-id="0d38c-103">Obtém um objeto que pode ser consultado para a interface ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="0d38c-103">Gets an object that can be queried for the ICorDebugThread interface.</span></span> <span data-ttu-id="0d38c-104">Esse método é obsoleto no .NET Framework versão 2,0.</span><span class="sxs-lookup"><span data-stu-id="0d38c-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d38c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0d38c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInprocInspectionIThisThread(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d38c-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0d38c-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="0d38c-107">objeto de [saída](/cpp/atl/iunknown) que pode ser consultado para a interface `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="0d38c-107">[out](/cpp/atl/iunknown) object that can be queried for the `ICorDebugThread` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d38c-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="0d38c-108">Remarks</span></span>  
 <span data-ttu-id="0d38c-109">Os serviços de depuração Common Language Runtime (CLR) com suporte para a depuração em processo limitada na versão .NET Framework 1,0.</span><span class="sxs-lookup"><span data-stu-id="0d38c-109">The common language runtime (CLR) debugging services supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="0d38c-110">A depuração em processo habilitou um criador de perfil para usar as partes de inspeção da API de depuração.</span><span class="sxs-lookup"><span data-stu-id="0d38c-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="0d38c-111">Como resultado dos comentários dos clientes, a depuração em processo foi removida da .NET Framework na versão 2,0 e substituída por um conjunto de funcionalidades que está mais alinhado com a API de criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="0d38c-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d38c-112">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="0d38c-112">Requirements</span></span>  
 <span data-ttu-id="0d38c-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d38c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d38c-114">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0d38c-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0d38c-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d38c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d38c-116">**Versão do .NET Framework:** 1,0</span><span class="sxs-lookup"><span data-stu-id="0d38c-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d38c-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="0d38c-117">See also</span></span>

- [<span data-ttu-id="0d38c-118">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="0d38c-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
