---
title: Método ICorProfilerCallback::ExceptionCLRCatcherFound
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCLRCatcherFound
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherFound
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherFound method [.NET Framework profiling]
- ExceptionCLRCatcherFound method [.NET Framework profiling]
ms.assetid: 73fe8b4b-8f9a-4ba5-a10c-b26521396a66
topic_type:
- apiref
ms.openlocfilehash: ef5122d49c428af4faa27f3827a5c60721ef0f74
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435835"
---
# <a name="icorprofilercallbackexceptionclrcatcherfound-method"></a><span data-ttu-id="abc6c-102">Método ICorProfilerCallback::ExceptionCLRCatcherFound</span><span class="sxs-lookup"><span data-stu-id="abc6c-102">ICorProfilerCallback::ExceptionCLRCatcherFound Method</span></span>
<span data-ttu-id="abc6c-103">Chamado quando um bloco de `catch` para uma exceção é encontrado dentro do Common Language Runtime (CLR) em si.</span><span class="sxs-lookup"><span data-stu-id="abc6c-103">Called when a `catch` block for an exception is found inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="abc6c-104">Esse método é obsoleto no .NET Framework versão 2,0.</span><span class="sxs-lookup"><span data-stu-id="abc6c-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abc6c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="abc6c-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCLRCatcherFound();  
```  
  
## <a name="requirements"></a><span data-ttu-id="abc6c-106">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="abc6c-106">Requirements</span></span>  
 <span data-ttu-id="abc6c-107">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abc6c-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abc6c-108">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="abc6c-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="abc6c-109">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="abc6c-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="abc6c-110">**Versão do .NET Framework:** 1,0</span><span class="sxs-lookup"><span data-stu-id="abc6c-110">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abc6c-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="abc6c-111">See also</span></span>

- [<span data-ttu-id="abc6c-112">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="abc6c-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="abc6c-113">Método ExceptionCLRCatcherExecute</span><span class="sxs-lookup"><span data-stu-id="abc6c-113">ExceptionCLRCatcherExecute Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherexecute-method.md)
