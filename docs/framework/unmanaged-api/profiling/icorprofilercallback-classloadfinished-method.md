---
title: Método ICorProfilerCallback::ClassLoadFinished
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6508c989b143780090d582fd4175fe20bedeb770
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745445"
---
# <a name="icorprofilercallbackclassloadfinished-method"></a><span data-ttu-id="f5372-102">Método ICorProfilerCallback::ClassLoadFinished</span><span class="sxs-lookup"><span data-stu-id="f5372-102">ICorProfilerCallback::ClassLoadFinished Method</span></span>
<span data-ttu-id="f5372-103">Notifica o criador de perfil de uma classe terminou o carregamento.</span><span class="sxs-lookup"><span data-stu-id="f5372-103">Notifies the profiler that a class has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5372-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f5372-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassLoadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5372-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f5372-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="f5372-106">[in] Identifica a classe que foi carregada.</span><span class="sxs-lookup"><span data-stu-id="f5372-106">[in] Identifies the class that was loaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="f5372-107">[in] Um HRESULT que indica se a classe é carregada com êxito.</span><span class="sxs-lookup"><span data-stu-id="f5372-107">[in] An HRESULT that indicates whether the class loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5372-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="f5372-108">Remarks</span></span>  
 <span data-ttu-id="f5372-109">O valor de `classId` não é válido para uma solicitação de informações até que o `ClassLoadFinished` método é chamado.</span><span class="sxs-lookup"><span data-stu-id="f5372-109">The value of `classId` is not valid for an information request until the `ClassLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="f5372-110">Algumas partes de carregamento de classe podem continuar após o `ClassLoadFinished` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="f5372-110">Some parts of loading the class might continue after the `ClassLoadFinished` callback.</span></span> <span data-ttu-id="f5372-111">Uma falha HRESULT em `hrStatus` indica uma falha.</span><span class="sxs-lookup"><span data-stu-id="f5372-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="f5372-112">No entanto, um HRESULT de sucesso em `hrStatus` indica apenas que a primeira parte de carregamento de classe teve êxito.</span><span class="sxs-lookup"><span data-stu-id="f5372-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5372-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f5372-113">Requirements</span></span>  
 <span data-ttu-id="f5372-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5372-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5372-115">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f5372-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f5372-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5372-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5372-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5372-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5372-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f5372-118">See also</span></span>

- [<span data-ttu-id="f5372-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="f5372-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="f5372-120">Método ClassLoadStarted</span><span class="sxs-lookup"><span data-stu-id="f5372-120">ClassLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)
