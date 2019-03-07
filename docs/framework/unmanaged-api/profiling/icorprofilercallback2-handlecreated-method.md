---
title: Método ICorProfilerCallback2::HandleCreated
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.HandleCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::HandleCreated
helpviewer_keywords:
- HandleCreated method [.NET Framework profiling]
- ICorProfilerCallback2::HandleCreated method [.NET Framework profiling]
ms.assetid: 6bbb7786-7c38-490f-9834-91aa2795c355
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e598c4f3a4f777cdb8a871cdc6ea56a080e3c9bc
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496905"
---
# <a name="icorprofilercallback2handlecreated-method"></a><span data-ttu-id="f2fa6-102">Método ICorProfilerCallback2::HandleCreated</span><span class="sxs-lookup"><span data-stu-id="f2fa6-102">ICorProfilerCallback2::HandleCreated Method</span></span>
<span data-ttu-id="f2fa6-103">Notifica o criador de perfil de código que foi criado um identificador da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="f2fa6-103">Notifies the code profiler that a garbage collection handle has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2fa6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f2fa6-104">Syntax</span></span>  
  
```  
HRESULT HandleCreated(  
    [in] GCHandleID handleId,  
    [in] ObjectID initialObjectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2fa6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f2fa6-105">Parameters</span></span>  
 `handleId`  
 <span data-ttu-id="f2fa6-106">[in] A ID do identificador para a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="f2fa6-106">[in] The ID of the handle for the garbage collection.</span></span>  
  
 `initialObjectId`  
 <span data-ttu-id="f2fa6-107">[in] A ID do objeto para o qual o identificador da coleta de lixo foi criado.</span><span class="sxs-lookup"><span data-stu-id="f2fa6-107">[in] The ID of the object for which the garbage collection handle was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2fa6-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f2fa6-108">Requirements</span></span>  
 <span data-ttu-id="f2fa6-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2fa6-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2fa6-110">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f2fa6-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f2fa6-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2fa6-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2fa6-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2fa6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2fa6-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f2fa6-113">See also</span></span>
- [<span data-ttu-id="f2fa6-114">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="f2fa6-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="f2fa6-115">Interface ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="f2fa6-115">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
