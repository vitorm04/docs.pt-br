---
title: "Método ICorProfilerCallback::ClassLoadFinished"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerCallback.ClassLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadFinished
helpviewer_keywords:
- ClassLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ClassLoadFinished method [.NET Framework profiling]
ms.assetid: 3dd80fbe-d62d-4d4d-acf8-5b7d0efe607e
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ae55325f514f9bec3efdf4764958e4b3fafd922b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackclassloadfinished-method"></a><span data-ttu-id="66240-102">Método ICorProfilerCallback::ClassLoadFinished</span><span class="sxs-lookup"><span data-stu-id="66240-102">ICorProfilerCallback::ClassLoadFinished Method</span></span>
<span data-ttu-id="66240-103">Notifica o criador de perfil que uma classe terminou o carregamento.</span><span class="sxs-lookup"><span data-stu-id="66240-103">Notifies the profiler that a class has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66240-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="66240-104">Syntax</span></span>  
  
```  
HRESULT ClassLoadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="66240-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="66240-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="66240-106">[in] Identifica a classe que foi carregada.</span><span class="sxs-lookup"><span data-stu-id="66240-106">[in] Identifies the class that was loaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="66240-107">[in] Um HRESULT que indica se a classe é carregada com êxito.</span><span class="sxs-lookup"><span data-stu-id="66240-107">[in] An HRESULT that indicates whether the class loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66240-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="66240-108">Remarks</span></span>  
 <span data-ttu-id="66240-109">O valor de `classId` não é válido para uma solicitação de informações até que o `ClassLoadFinished` método é chamado.</span><span class="sxs-lookup"><span data-stu-id="66240-109">The value of `classId` is not valid for an information request until the `ClassLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="66240-110">Algumas partes do carregamento de classe podem continuar após o `ClassLoadFinished` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="66240-110">Some parts of loading the class might continue after the `ClassLoadFinished` callback.</span></span> <span data-ttu-id="66240-111">Uma falha de HRESULT em `hrStatus` indica uma falha.</span><span class="sxs-lookup"><span data-stu-id="66240-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="66240-112">No entanto, um HRESULT de sucesso em `hrStatus` indica apenas que a primeira parte do carregamento de classe teve êxito.</span><span class="sxs-lookup"><span data-stu-id="66240-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66240-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="66240-113">Requirements</span></span>  
 <span data-ttu-id="66240-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66240-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66240-115">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="66240-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="66240-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66240-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66240-117">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66240-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66240-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="66240-118">See Also</span></span>  
 [<span data-ttu-id="66240-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="66240-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="66240-120">Método ClassLoadStarted</span><span class="sxs-lookup"><span data-stu-id="66240-120">ClassLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)
