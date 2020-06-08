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
ms.openlocfilehash: 4f4d53b086453adce38902518f2de3dde1f2812f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500241"
---
# <a name="icorprofilercallbackexceptionclrcatcherfound-method"></a><span data-ttu-id="8cc32-102">Método ICorProfilerCallback::ExceptionCLRCatcherFound</span><span class="sxs-lookup"><span data-stu-id="8cc32-102">ICorProfilerCallback::ExceptionCLRCatcherFound Method</span></span>
<span data-ttu-id="8cc32-103">Chamado quando um `catch` bloco de uma exceção é encontrado dentro do Common Language Runtime (CLR) em si.</span><span class="sxs-lookup"><span data-stu-id="8cc32-103">Called when a `catch` block for an exception is found inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="8cc32-104">Esse método é obsoleto no .NET Framework versão 2,0.</span><span class="sxs-lookup"><span data-stu-id="8cc32-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cc32-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8cc32-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCLRCatcherFound();  
```  
  
## <a name="requirements"></a><span data-ttu-id="8cc32-106">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8cc32-106">Requirements</span></span>  
 <span data-ttu-id="8cc32-107">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8cc32-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cc32-108">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8cc32-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8cc32-109">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8cc32-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8cc32-110">**Versão do .NET Framework:** 1,0</span><span class="sxs-lookup"><span data-stu-id="8cc32-110">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cc32-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="8cc32-111">See also</span></span>

- [<span data-ttu-id="8cc32-112">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="8cc32-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="8cc32-113">Método ExceptionCLRCatcherExecute</span><span class="sxs-lookup"><span data-stu-id="8cc32-113">ExceptionCLRCatcherExecute Method</span></span>](icorprofilercallback-exceptionclrcatcherexecute-method.md)
