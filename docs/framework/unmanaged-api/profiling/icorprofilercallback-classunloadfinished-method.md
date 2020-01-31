---
title: Método ICorProfilerCallback::ClassUnloadFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadFinished
helpviewer_keywords:
- ICorProfilerCallback::ClassUnloadFinished method [.NET Framework profiling]
- ClassUnloadFinished method [.NET Framework profiling]
ms.assetid: 55674b68-678a-4747-ae06-4e91519c7305
topic_type:
- apiref
ms.openlocfilehash: 5d9474f78dd8b999a37f60e0698cfd04240b897a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866566"
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a><span data-ttu-id="f805f-102">Método ICorProfilerCallback::ClassUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="f805f-102">ICorProfilerCallback::ClassUnloadFinished Method</span></span>
<span data-ttu-id="f805f-103">Notifica o criador de perfil de que uma classe concluiu o descarregamento.</span><span class="sxs-lookup"><span data-stu-id="f805f-103">Notifies the profiler that a class has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f805f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f805f-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f805f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f805f-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="f805f-106">\[em] identifica a classe que foi descarregada.</span><span class="sxs-lookup"><span data-stu-id="f805f-106">\[in] Identifies the class that was unloaded.</span></span>

- `hrStatus`

  <span data-ttu-id="f805f-107">\[em] um HRESULT que indica se a classe foi descarregada com êxito.</span><span class="sxs-lookup"><span data-stu-id="f805f-107">\[in] An HRESULT that indicates whether the class was unloaded successfully.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="f805f-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="f805f-108">Remarks</span></span>  
 <span data-ttu-id="f805f-109">Algumas partes do descarregamento da classe podem continuar após o retorno de chamada `ClassUnloadFinished`.</span><span class="sxs-lookup"><span data-stu-id="f805f-109">Some parts of unloading the class might continue after the `ClassUnloadFinished` callback.</span></span> <span data-ttu-id="f805f-110">Uma falha HRESULT no `hrStatus` indica uma falha.</span><span class="sxs-lookup"><span data-stu-id="f805f-110">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="f805f-111">No entanto, um HRESULT de êxito em `hrStatus` indica apenas que a primeira parte do descarregamento da classe foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="f805f-111">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f805f-112">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="f805f-112">Requirements</span></span>  
 <span data-ttu-id="f805f-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f805f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f805f-114">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f805f-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f805f-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f805f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f805f-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f805f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f805f-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="f805f-117">See also</span></span>

- [<span data-ttu-id="f805f-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="f805f-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="f805f-119">Método ClassUnloadStarted</span><span class="sxs-lookup"><span data-stu-id="f805f-119">ClassUnloadStarted Method</span></span>](icorprofilercallback-classunloadstarted-method.md)
