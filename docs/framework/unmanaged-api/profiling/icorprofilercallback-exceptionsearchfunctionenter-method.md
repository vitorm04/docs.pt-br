---
title: Método ICorProfilerCallback::ExceptionSearchFunctionEnter
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFunctionEnter
helpviewer_keywords:
- ExceptionSearchFunctionEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFunctionEnter method [.NET Framework profiling]
ms.assetid: bfd54573-b7e6-4bd1-a184-7f08a8b39fae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0615f37d97359f73eb1277da174b7e6401bfc313
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57500337"
---
# <a name="icorprofilercallbackexceptionsearchfunctionenter-method"></a><span data-ttu-id="1fbb7-102">Método ICorProfilerCallback::ExceptionSearchFunctionEnter</span><span class="sxs-lookup"><span data-stu-id="1fbb7-102">ICorProfilerCallback::ExceptionSearchFunctionEnter Method</span></span>
<span data-ttu-id="1fbb7-103">Notifica o criador de perfil que a fase de pesquisa de tratamento de exceção de começar a procurar uma função para localizar um manipulador para a exceção atual.</span><span class="sxs-lookup"><span data-stu-id="1fbb7-103">Notifies the profiler that the search phase of exception handling has begun searching a function to find a handler for the current exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fbb7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1fbb7-104">Syntax</span></span>  
  
```  
HRESULT ExceptionSearchFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1fbb7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1fbb7-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="1fbb7-106">[in] A ID da função que foi inserida.</span><span class="sxs-lookup"><span data-stu-id="1fbb7-106">[in] The ID of the function that has been entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fbb7-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1fbb7-107">Requirements</span></span>  
 <span data-ttu-id="1fbb7-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1fbb7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fbb7-109">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1fbb7-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1fbb7-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1fbb7-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1fbb7-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1fbb7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fbb7-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1fbb7-112">See also</span></span>
- [<span data-ttu-id="1fbb7-113">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="1fbb7-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="1fbb7-114">Método ExceptionSearchFunctionLeave</span><span class="sxs-lookup"><span data-stu-id="1fbb7-114">ExceptionSearchFunctionLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionleave-method.md)
