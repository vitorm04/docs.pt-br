---
title: Método ICorProfilerCallback::ExceptionSearchFilterEnter
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFilterEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFilterEnter
helpviewer_keywords:
- ExceptionSearchFilterEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFilterEnter method [.NET Framework profiling]
ms.assetid: acc239ce-3eef-418c-b1df-c5a6dd8e8a4c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: be91772f07e1a06c7df5b16fd70812e6a522d736
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61597213"
---
# <a name="icorprofilercallbackexceptionsearchfilterenter-method"></a><span data-ttu-id="61431-102">Método ICorProfilerCallback::ExceptionSearchFilterEnter</span><span class="sxs-lookup"><span data-stu-id="61431-102">ICorProfilerCallback::ExceptionSearchFilterEnter Method</span></span>
<span data-ttu-id="61431-103">Notifica o criador de perfil que a fase de pesquisa de tratamento de exceções começou a execução de um filtro de exceção definidas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="61431-103">Notifies the profiler that the search phase of exception handling has begun executing a user-defined exception filter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61431-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="61431-104">Syntax</span></span>  
  
```  
HRESULT ExceptionSearchFilterEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61431-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="61431-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="61431-106">[in] A ID da função que contém o filtro.</span><span class="sxs-lookup"><span data-stu-id="61431-106">[in] The ID of the function that contains the filter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61431-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="61431-107">Requirements</span></span>  
 <span data-ttu-id="61431-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61431-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61431-109">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="61431-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="61431-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61431-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61431-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61431-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61431-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61431-112">See also</span></span>

- [<span data-ttu-id="61431-113">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="61431-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="61431-114">Método ExceptionSearchFilterLeave</span><span class="sxs-lookup"><span data-stu-id="61431-114">ExceptionSearchFilterLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)
