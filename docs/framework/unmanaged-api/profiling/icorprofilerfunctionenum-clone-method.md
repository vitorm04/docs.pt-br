---
title: "Método ICorProfilerFunctionEnum::Clone"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerFunctionEnum.Clone Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerFunctionEnum::Clone
helpviewer_keywords:
- ICorProfilerFunctionEnum::Clone method [.NET Framework profiling]
- Clone method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0c3d4835-e111-4e82-af6d-53f140b8f2c9
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 449292d8bacd6bb965119da81671c739f12dc3a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerfunctionenumclone-method"></a><span data-ttu-id="03172-102">Método ICorProfilerFunctionEnum::Clone</span><span class="sxs-lookup"><span data-stu-id="03172-102">ICorProfilerFunctionEnum::Clone Method</span></span>
<span data-ttu-id="03172-103">Obtém um ponteiro de interface para uma cópia deste [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="03172-103">Gets an interface pointer to a copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03172-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="03172-104">Syntax</span></span>  
  
```  
HRESULT Clone([out] ICorProfilerFunctionEnum **ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="03172-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="03172-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="03172-106">[out] Um ponteiro para o ponteiro de interface, que, por sua vez, aponta para a cópia desse [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="03172-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span></span> <span data-ttu-id="03172-107">A cópia do enumerador mantém seu próprio estado de enumeração separadamente deste enumerador.</span><span class="sxs-lookup"><span data-stu-id="03172-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="03172-108">No entanto, posição de cursor inicial da cópia é igual a posição atual do cursor deste enumerador.</span><span class="sxs-lookup"><span data-stu-id="03172-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03172-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="03172-109">Requirements</span></span>  
 <span data-ttu-id="03172-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03172-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03172-111">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="03172-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="03172-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="03172-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03172-113">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03172-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03172-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="03172-114">See Also</span></span>  
 [<span data-ttu-id="03172-115">Interface ICorProfilerFunctionEnum</span><span class="sxs-lookup"><span data-stu-id="03172-115">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 [<span data-ttu-id="03172-116">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="03172-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
