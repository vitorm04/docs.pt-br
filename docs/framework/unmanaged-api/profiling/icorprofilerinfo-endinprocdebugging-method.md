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
ms.openlocfilehash: 8a15843e9169442d89996375ee85f62b38f92e30
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864252"
---
# <a name="icorprofilerinfoendinprocdebugging-method"></a><span data-ttu-id="a3cfd-102">Método ICorProfilerInfo::EndInprocDebugging</span><span class="sxs-lookup"><span data-stu-id="a3cfd-102">ICorProfilerInfo::EndInprocDebugging Method</span></span>
<span data-ttu-id="a3cfd-103">Desliga uma sessão de depuração em processo.</span><span class="sxs-lookup"><span data-stu-id="a3cfd-103">Shuts down an in-process debugging session.</span></span> <span data-ttu-id="a3cfd-104">Esse método é obsoleto no .NET Framework versão 2,0.</span><span class="sxs-lookup"><span data-stu-id="a3cfd-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3cfd-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a3cfd-105">Syntax</span></span>  
  
```cpp  
HRESULT EndInprocDebugging(  
    [in]  DWORD dwProfilerContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3cfd-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a3cfd-106">Parameters</span></span>  
 `dwProfilerContext`  
 <span data-ttu-id="a3cfd-107">no Um valor que identifica a sessão de depuração.</span><span class="sxs-lookup"><span data-stu-id="a3cfd-107">[in] A value that identifies the debugging session.</span></span> <span data-ttu-id="a3cfd-108">Esse valor deve ser o mesmo que o recebido no método [ICorProfilerInfo:: BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a3cfd-108">This value must be the same as that received in the [ICorProfilerInfo::BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3cfd-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="a3cfd-109">Remarks</span></span>  
 <span data-ttu-id="a3cfd-110">Você deve chamar [ICorProfilerInfo:: BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) e `EndInprocDebugging` no mesmo método de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="a3cfd-110">You must call [ICorProfilerInfo::BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) and `EndInprocDebugging` within the same callback method.</span></span>  
  
 <span data-ttu-id="a3cfd-111">Os serviços de depuração CLR oferecem suporte à depuração em processo limitada no .NET Framework versões 1,0 e 1,1.</span><span class="sxs-lookup"><span data-stu-id="a3cfd-111">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="a3cfd-112">A depuração em processo habilitou um criador de perfil para usar as partes de inspeção da API de depuração.</span><span class="sxs-lookup"><span data-stu-id="a3cfd-112">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="a3cfd-113">No entanto, devido aos comentários do cliente, a depuração em processo foi removida da .NET Framework na versão 2,0 e substituída por um conjunto de funcionalidades que está mais alinhado com a API de criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="a3cfd-113">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3cfd-114">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="a3cfd-114">Requirements</span></span>  
 <span data-ttu-id="a3cfd-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3cfd-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3cfd-116">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a3cfd-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a3cfd-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a3cfd-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3cfd-118">**Versão do .NET Framework:** 1,0</span><span class="sxs-lookup"><span data-stu-id="a3cfd-118">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3cfd-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="a3cfd-119">See also</span></span>

- [<span data-ttu-id="a3cfd-120">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="a3cfd-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
