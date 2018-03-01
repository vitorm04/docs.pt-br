---
title: "Método ICorProfilerObjectEnum::Clone"
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
- ICorProfilerObjectEnum.Clone
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerObjectEnum interface [.NET Framework profiling]
- ICorProfilerObjectEnum::Clone method [.NET Framework profiling]
ms.assetid: b0b2facd-5991-4f4c-932d-c4937f45cef9
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2d8e478eb9165b4aa5bf019f02f4f128931d928b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerobjectenumclone-method"></a><span data-ttu-id="56656-102">Método ICorProfilerObjectEnum::Clone</span><span class="sxs-lookup"><span data-stu-id="56656-102">ICorProfilerObjectEnum::Clone Method</span></span>
<span data-ttu-id="56656-103">Obtém um ponteiro de interface para uma cópia deste [ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="56656-103">Gets an interface pointer to a copy of this [ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56656-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="56656-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] ICorProfilerObjectEnum   **ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="56656-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="56656-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="56656-106">[out] Um ponteiro para o ponteiro de interface que aponta para a cópia desse `ICorProfilerObjectEnum` interface.</span><span class="sxs-lookup"><span data-stu-id="56656-106">[out] A pointer to the interface pointer that in turn points to the copy of this `ICorProfilerObjectEnum` interface.</span></span> <span data-ttu-id="56656-107">A cópia mantém seu próprio estado de enumeração separadamente daquela.</span><span class="sxs-lookup"><span data-stu-id="56656-107">The copy maintains its own enumeration state separately from this one.</span></span> <span data-ttu-id="56656-108">No entanto, posição de cursor inicial da cópia será o mesmo que a posição atual do cursor deste enumerador.</span><span class="sxs-lookup"><span data-stu-id="56656-108">However, the copy's initial cursor position will be the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56656-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="56656-109">Requirements</span></span>  
 <span data-ttu-id="56656-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56656-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56656-111">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="56656-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="56656-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56656-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56656-113">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56656-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56656-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="56656-114">See Also</span></span>  
 [<span data-ttu-id="56656-115">Interface ICorProfilerObjectEnum</span><span class="sxs-lookup"><span data-stu-id="56656-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
