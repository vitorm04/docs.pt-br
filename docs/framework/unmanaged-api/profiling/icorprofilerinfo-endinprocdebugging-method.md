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
ms.openlocfilehash: f86c680a10a3dcb1009b4f0cedd777ab9da5ac1f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501741"
---
# <a name="icorprofilerinfoendinprocdebugging-method"></a><span data-ttu-id="26d68-102">Método ICorProfilerInfo::EndInprocDebugging</span><span class="sxs-lookup"><span data-stu-id="26d68-102">ICorProfilerInfo::EndInprocDebugging Method</span></span>
<span data-ttu-id="26d68-103">Fecha uma sessão de depuração em processo.</span><span class="sxs-lookup"><span data-stu-id="26d68-103">Shuts down an in-process debugging session.</span></span> <span data-ttu-id="26d68-104">Este método é obsoleto no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="26d68-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26d68-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="26d68-105">Syntax</span></span>  
  
```  
HRESULT EndInprocDebugging(  
    [in]  DWORD dwProfilerContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26d68-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="26d68-106">Parameters</span></span>  
 `dwProfilerContext`  
 <span data-ttu-id="26d68-107">[in] Um valor que identifica a sessão de depuração.</span><span class="sxs-lookup"><span data-stu-id="26d68-107">[in] A value that identifies the debugging session.</span></span> <span data-ttu-id="26d68-108">Esse valor deve ser o mesmo que recebeu na [ICorProfilerInfo:: BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="26d68-108">This value must be the same as that received in the [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26d68-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="26d68-109">Remarks</span></span>  
 <span data-ttu-id="26d68-110">Você deve chamar [ICorProfilerInfo:: BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) e `EndInprocDebugging` dentro do mesmo método de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="26d68-110">You must call [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) and `EndInprocDebugging` within the same callback method.</span></span>  
  
 <span data-ttu-id="26d68-111">Os serviços de depuração do CLR tem suporte limitado em processo depuração nas versões do .NET Framework 1.0 e 1.1.</span><span class="sxs-lookup"><span data-stu-id="26d68-111">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="26d68-112">No processo de depuração habilitado um criador de perfil usar as partes de inspeção da API de depuração.</span><span class="sxs-lookup"><span data-stu-id="26d68-112">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="26d68-113">No entanto, devido a comentários dos clientes, no processo de depuração foi removido do .NET Framework versão 2.0 e substituída por um conjunto de funcionalidade que é mais alinhada com a API de criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="26d68-113">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26d68-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="26d68-114">Requirements</span></span>  
 <span data-ttu-id="26d68-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26d68-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26d68-116">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="26d68-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="26d68-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26d68-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26d68-118">**Versão do .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="26d68-118">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26d68-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26d68-119">See also</span></span>
- [<span data-ttu-id="26d68-120">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="26d68-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
