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
ms.openlocfilehash: a543e5119a3ad5580fb67c31dc0e59ab62eab571
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866486"
---
# <a name="icorprofilercallbackexceptionclrcatcherfound-method"></a><span data-ttu-id="c0cc9-102">Método ICorProfilerCallback::ExceptionCLRCatcherFound</span><span class="sxs-lookup"><span data-stu-id="c0cc9-102">ICorProfilerCallback::ExceptionCLRCatcherFound Method</span></span>
<span data-ttu-id="c0cc9-103">Chamado quando um bloco de `catch` para uma exceção é encontrado dentro do Common Language Runtime (CLR) em si.</span><span class="sxs-lookup"><span data-stu-id="c0cc9-103">Called when a `catch` block for an exception is found inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="c0cc9-104">Esse método é obsoleto no .NET Framework versão 2,0.</span><span class="sxs-lookup"><span data-stu-id="c0cc9-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0cc9-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c0cc9-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCLRCatcherFound();  
```  
  
## <a name="requirements"></a><span data-ttu-id="c0cc9-106">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="c0cc9-106">Requirements</span></span>  
 <span data-ttu-id="c0cc9-107">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0cc9-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0cc9-108">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c0cc9-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c0cc9-109">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0cc9-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0cc9-110">**Versão do .NET Framework:** 1,0</span><span class="sxs-lookup"><span data-stu-id="c0cc9-110">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0cc9-111">Veja também</span><span class="sxs-lookup"><span data-stu-id="c0cc9-111">See also</span></span>

- [<span data-ttu-id="c0cc9-112">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="c0cc9-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="c0cc9-113">Método ExceptionCLRCatcherExecute</span><span class="sxs-lookup"><span data-stu-id="c0cc9-113">ExceptionCLRCatcherExecute Method</span></span>](icorprofilercallback-exceptionclrcatcherexecute-method.md)
