---
title: Método ICorProfilerCallback::ExceptionCLRCatcherExecute
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCLRCatcherExecute
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherExecute
helpviewer_keywords:
- ExceptionCLRCatcherExecute method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionCLRCatcherExecute method [.NET Framework profiling]
ms.assetid: aaac8f98-5cf4-42c7-b04b-556cce367e36
topic_type:
- apiref
ms.openlocfilehash: b79c8dd9f27805e00535dde53c6ee9f5ee457b42
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500257"
---
# <a name="icorprofilercallbackexceptionclrcatcherexecute-method"></a><span data-ttu-id="84fe6-102">Método ICorProfilerCallback::ExceptionCLRCatcherExecute</span><span class="sxs-lookup"><span data-stu-id="84fe6-102">ICorProfilerCallback::ExceptionCLRCatcherExecute Method</span></span>
<span data-ttu-id="84fe6-103">Chamado quando um `catch` bloco de uma exceção é executado dentro do Common Language Runtime (CLR) em si.</span><span class="sxs-lookup"><span data-stu-id="84fe6-103">Called when a `catch` block for an exception is executed inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="84fe6-104">Esse método é obsoleto no .NET Framework versão 2,0.</span><span class="sxs-lookup"><span data-stu-id="84fe6-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84fe6-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="84fe6-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCLRCatcherExecute();  
```  
  
## <a name="requirements"></a><span data-ttu-id="84fe6-106">Requisitos</span><span class="sxs-lookup"><span data-stu-id="84fe6-106">Requirements</span></span>  
 <span data-ttu-id="84fe6-107">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84fe6-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84fe6-108">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="84fe6-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="84fe6-109">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84fe6-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84fe6-110">**Versões do .NET Framework:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="84fe6-110">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84fe6-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="84fe6-111">See also</span></span>

- [<span data-ttu-id="84fe6-112">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="84fe6-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="84fe6-113">Método ExceptionCLRCatcherFound</span><span class="sxs-lookup"><span data-stu-id="84fe6-113">ExceptionCLRCatcherFound Method</span></span>](icorprofilercallback-exceptionclrcatcherfound-method.md)
