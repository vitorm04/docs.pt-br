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
ms.openlocfilehash: e0ff90f99c1127b5a4626f47514ba7099b5d48af
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866592"
---
# <a name="icorprofilercallbackclassloadfinished-method"></a><span data-ttu-id="3fb82-102">Método ICorProfilerCallback::ClassLoadFinished</span><span class="sxs-lookup"><span data-stu-id="3fb82-102">ICorProfilerCallback::ClassLoadFinished Method</span></span>
<span data-ttu-id="3fb82-103">Notifica o criador de perfil que a conclusão do carregamento de uma classe.</span><span class="sxs-lookup"><span data-stu-id="3fb82-103">Notifies the profiler that a class has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fb82-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3fb82-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassLoadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3fb82-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3fb82-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="3fb82-106">\[em] identifica a classe que foi carregada.</span><span class="sxs-lookup"><span data-stu-id="3fb82-106">\[in] Identifies the class that was loaded.</span></span>

- `hrStatus`

  <span data-ttu-id="3fb82-107">\[em] um HRESULT que indica se a classe foi carregada com êxito.</span><span class="sxs-lookup"><span data-stu-id="3fb82-107">\[in] An HRESULT that indicates whether the class loaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="3fb82-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="3fb82-108">Remarks</span></span>  
 <span data-ttu-id="3fb82-109">O valor de `classId` não é válido para uma solicitação de informações até que o método `ClassLoadFinished` seja chamado.</span><span class="sxs-lookup"><span data-stu-id="3fb82-109">The value of `classId` is not valid for an information request until the `ClassLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="3fb82-110">Algumas partes do carregamento da classe podem continuar após o retorno de chamada `ClassLoadFinished`.</span><span class="sxs-lookup"><span data-stu-id="3fb82-110">Some parts of loading the class might continue after the `ClassLoadFinished` callback.</span></span> <span data-ttu-id="3fb82-111">Uma falha HRESULT no `hrStatus` indica uma falha.</span><span class="sxs-lookup"><span data-stu-id="3fb82-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="3fb82-112">No entanto, um HRESULT de êxito em `hrStatus` indica apenas que a primeira parte do carregamento da classe foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="3fb82-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fb82-113">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="3fb82-113">Requirements</span></span>  
 <span data-ttu-id="3fb82-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fb82-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fb82-115">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3fb82-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3fb82-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3fb82-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3fb82-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fb82-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fb82-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="3fb82-118">See also</span></span>

- [<span data-ttu-id="3fb82-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="3fb82-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="3fb82-120">Método ClassLoadStarted</span><span class="sxs-lookup"><span data-stu-id="3fb82-120">ClassLoadStarted Method</span></span>](icorprofilercallback-classloadstarted-method.md)
