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
ms.openlocfilehash: 09b1b81bde486db67acede99e0d67ff85cb01bae
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447761"
---
# <a name="icorprofilerinfoendinprocdebugging-method"></a><span data-ttu-id="92be2-102">Método ICorProfilerInfo::EndInprocDebugging</span><span class="sxs-lookup"><span data-stu-id="92be2-102">ICorProfilerInfo::EndInprocDebugging Method</span></span>
<span data-ttu-id="92be2-103">Desliga uma sessão de depuração em processo.</span><span class="sxs-lookup"><span data-stu-id="92be2-103">Shuts down an in-process debugging session.</span></span> <span data-ttu-id="92be2-104">Esse método é obsoleto no .NET Framework versão 2,0.</span><span class="sxs-lookup"><span data-stu-id="92be2-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92be2-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="92be2-105">Syntax</span></span>  
  
```cpp  
HRESULT EndInprocDebugging(  
    [in]  DWORD dwProfilerContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92be2-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="92be2-106">Parameters</span></span>  
 `dwProfilerContext`  
 <span data-ttu-id="92be2-107">no Um valor que identifica a sessão de depuração.</span><span class="sxs-lookup"><span data-stu-id="92be2-107">[in] A value that identifies the debugging session.</span></span> <span data-ttu-id="92be2-108">Esse valor deve ser o mesmo que o recebido no método [ICorProfilerInfo:: BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) .</span><span class="sxs-lookup"><span data-stu-id="92be2-108">This value must be the same as that received in the [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92be2-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="92be2-109">Remarks</span></span>  
 <span data-ttu-id="92be2-110">Você deve chamar [ICorProfilerInfo:: BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) e `EndInprocDebugging` no mesmo método de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="92be2-110">You must call [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) and `EndInprocDebugging` within the same callback method.</span></span>  
  
 <span data-ttu-id="92be2-111">Os serviços de depuração CLR oferecem suporte à depuração em processo limitada no .NET Framework versões 1,0 e 1,1.</span><span class="sxs-lookup"><span data-stu-id="92be2-111">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="92be2-112">A depuração em processo habilitou um criador de perfil para usar as partes de inspeção da API de depuração.</span><span class="sxs-lookup"><span data-stu-id="92be2-112">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="92be2-113">No entanto, devido aos comentários do cliente, a depuração em processo foi removida da .NET Framework na versão 2,0 e substituída por um conjunto de funcionalidades que está mais alinhado com a API de criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="92be2-113">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92be2-114">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="92be2-114">Requirements</span></span>  
 <span data-ttu-id="92be2-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92be2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92be2-116">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="92be2-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="92be2-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92be2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92be2-118">**Versão do .NET Framework:** 1,0</span><span class="sxs-lookup"><span data-stu-id="92be2-118">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92be2-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="92be2-119">See also</span></span>

- [<span data-ttu-id="92be2-120">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="92be2-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
