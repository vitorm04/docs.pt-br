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
ms.openlocfilehash: ef2c518f8f3f3069e93f06de89add1385cb4e45e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445122"
---
# <a name="icorprofilercallbackclassloadfinished-method"></a><span data-ttu-id="912af-102">Método ICorProfilerCallback::ClassLoadFinished</span><span class="sxs-lookup"><span data-stu-id="912af-102">ICorProfilerCallback::ClassLoadFinished Method</span></span>
<span data-ttu-id="912af-103">Notifica o criador de perfil que a conclusão do carregamento de uma classe.</span><span class="sxs-lookup"><span data-stu-id="912af-103">Notifies the profiler that a class has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="912af-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="912af-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassLoadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="912af-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="912af-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="912af-106">no Identifica a classe que foi carregada.</span><span class="sxs-lookup"><span data-stu-id="912af-106">[in] Identifies the class that was loaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="912af-107">no Um HRESULT que indica se a classe foi carregada com êxito.</span><span class="sxs-lookup"><span data-stu-id="912af-107">[in] An HRESULT that indicates whether the class loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="912af-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="912af-108">Remarks</span></span>  
 <span data-ttu-id="912af-109">O valor de `classId` não é válido para uma solicitação de informações até que o método `ClassLoadFinished` seja chamado.</span><span class="sxs-lookup"><span data-stu-id="912af-109">The value of `classId` is not valid for an information request until the `ClassLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="912af-110">Algumas partes do carregamento da classe podem continuar após o retorno de chamada `ClassLoadFinished`.</span><span class="sxs-lookup"><span data-stu-id="912af-110">Some parts of loading the class might continue after the `ClassLoadFinished` callback.</span></span> <span data-ttu-id="912af-111">Uma falha HRESULT no `hrStatus` indica uma falha.</span><span class="sxs-lookup"><span data-stu-id="912af-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="912af-112">No entanto, um HRESULT de êxito em `hrStatus` indica apenas que a primeira parte do carregamento da classe foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="912af-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="912af-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="912af-113">Requirements</span></span>  
 <span data-ttu-id="912af-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="912af-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="912af-115">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="912af-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="912af-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="912af-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="912af-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="912af-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="912af-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="912af-118">See also</span></span>

- [<span data-ttu-id="912af-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="912af-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="912af-120">Método ClassLoadStarted</span><span class="sxs-lookup"><span data-stu-id="912af-120">ClassLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)
