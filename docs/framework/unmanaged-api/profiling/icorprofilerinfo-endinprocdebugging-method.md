---
title: Método ICorProfilerInfo::EndInprocDebugging
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.EndInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::EndInprocDebugging
helpviewer_keywords:
- ICorProfilerInfo::EndInprocDebugging method [.NET Framework profiling]
- EndInprocDebugging method [.NET Framework profiling]
ms.assetid: 35bc1188-9767-4141-8038-60ea015b99ac
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cbf7e2e7de54b065f25f3a1873d760ab5051cc91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452605"
---
# <a name="icorprofilerinfoendinprocdebugging-method"></a><span data-ttu-id="31f6f-102">Método ICorProfilerInfo::EndInprocDebugging</span><span class="sxs-lookup"><span data-stu-id="31f6f-102">ICorProfilerInfo::EndInprocDebugging Method</span></span>
<span data-ttu-id="31f6f-103">Fecha uma sessão de depuração em andamento.</span><span class="sxs-lookup"><span data-stu-id="31f6f-103">Shuts down an in-process debugging session.</span></span> <span data-ttu-id="31f6f-104">Este método está obsoleto no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="31f6f-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31f6f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="31f6f-105">Syntax</span></span>  
  
```  
HRESULT EndInprocDebugging(  
    [in]  DWORD dwProfilerContext);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="31f6f-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="31f6f-106">Parameters</span></span>  
 `dwProfilerContext`  
 <span data-ttu-id="31f6f-107">[in] Um valor que identifica a sessão de depuração.</span><span class="sxs-lookup"><span data-stu-id="31f6f-107">[in] A value that identifies the debugging session.</span></span> <span data-ttu-id="31f6f-108">Esse valor deve ser o mesmo que a recebida no [: BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="31f6f-108">This value must be the same as that received in the [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31f6f-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="31f6f-109">Remarks</span></span>  
 <span data-ttu-id="31f6f-110">Você deve chamar [: BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) e `EndInprocDebugging` dentro do mesmo método de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="31f6f-110">You must call [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) and `EndInprocDebugging` within the same callback method.</span></span>  
  
 <span data-ttu-id="31f6f-111">Os serviços de depuração do CLR tem suporte limitado depuração em andamento nas versões do .NET Framework 1.0 e 1.1.</span><span class="sxs-lookup"><span data-stu-id="31f6f-111">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="31f6f-112">No processo de depuração habilitado um criador de perfil usar as partes de inspeção da API de depuração.</span><span class="sxs-lookup"><span data-stu-id="31f6f-112">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="31f6f-113">No entanto, devido a comentários dos clientes, no processo de depuração foi removido do .NET Framework versão 2.0 e substituído por um conjunto de funcionalidades mais alinhados com a API de criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="31f6f-113">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31f6f-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="31f6f-114">Requirements</span></span>  
 <span data-ttu-id="31f6f-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31f6f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31f6f-116">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="31f6f-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="31f6f-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="31f6f-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31f6f-118">**Versão do .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="31f6f-118">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31f6f-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="31f6f-119">See Also</span></span>  
 [<span data-ttu-id="31f6f-120">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="31f6f-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
