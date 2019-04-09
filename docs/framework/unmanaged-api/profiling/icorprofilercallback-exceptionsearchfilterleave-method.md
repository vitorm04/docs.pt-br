---
title: Método ICorProfilerCallback::ExceptionSearchFilterLeave
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFilterLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFilterLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionSearchFilterLeave method [.NET Framework profiling]
- ExceptionSearchFilterLeave method [.NET Framework profiling]
ms.assetid: c28a2a82-dd11-4385-843f-b509fb61753b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e89b76f7a246277737123e180c20874940437506
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124638"
---
# <a name="icorprofilercallbackexceptionsearchfilterleave-method"></a><span data-ttu-id="36100-102">Método ICorProfilerCallback::ExceptionSearchFilterLeave</span><span class="sxs-lookup"><span data-stu-id="36100-102">ICorProfilerCallback::ExceptionSearchFilterLeave Method</span></span>
<span data-ttu-id="36100-103">Notifica o criador de perfil que um filtro de usuário concluiu a execução.</span><span class="sxs-lookup"><span data-stu-id="36100-103">Notifies the profiler that a user filter has just finished executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36100-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="36100-104">Syntax</span></span>  
  
```  
HRESULT ExceptionSearchFilterLeave();  
```  
  
## <a name="requirements"></a><span data-ttu-id="36100-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="36100-105">Requirements</span></span>  
 <span data-ttu-id="36100-106">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36100-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36100-107">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="36100-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="36100-108">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36100-108">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="36100-109">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="36100-109">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="36100-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36100-110">See also</span></span>

- [<span data-ttu-id="36100-111">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="36100-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="36100-112">Método ExceptionSearchFilterEnter</span><span class="sxs-lookup"><span data-stu-id="36100-112">ExceptionSearchFilterEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)
