---
title: "Método ICorProfilerThreadEnum::Clone"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerThreadEnum.Clone
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerThreadEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Clone method [.NET Framework profiling]
ms.assetid: 5a278bc9-88e2-4c69-b035-9d550dd77081
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8954381fda72122269e5ebf49863e20f17ac32c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerthreadenumclone-method"></a><span data-ttu-id="ae973-102">Método ICorProfilerThreadEnum::Clone</span><span class="sxs-lookup"><span data-stu-id="ae973-102">ICorProfilerThreadEnum::Clone Method</span></span>
<span data-ttu-id="ae973-103">Obtém um ponteiro de interface para uma cópia deste [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="ae973-103">Gets an interface pointer to a copy of this [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae973-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ae973-104">Syntax</span></span>  
  
```  
HRESULT Clone (    [out] ICorProfilerThreadEnum **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ae973-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ae973-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="ae973-106">[out] Um ponteiro para o ponteiro de interface, que, por sua vez, aponta para a cópia desse [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="ae973-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span> <span data-ttu-id="ae973-107">A cópia do enumerador mantém seu próprio estado de enumeração separadamente deste enumerador.</span><span class="sxs-lookup"><span data-stu-id="ae973-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="ae973-108">No entanto, a posição do cursor inicial da cópia é igual essa posição do cursor atual do enumerador.</span><span class="sxs-lookup"><span data-stu-id="ae973-108">However, the initial cursor position of the copy is the same as this current cursor position of the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae973-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ae973-109">Requirements</span></span>  
 <span data-ttu-id="ae973-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae973-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae973-111">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ae973-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ae973-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae973-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae973-113">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae973-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae973-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae973-114">See Also</span></span>  
 [<span data-ttu-id="ae973-115">ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="ae973-115">ICorProfilerThreadEnum</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 [<span data-ttu-id="ae973-116">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="ae973-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
