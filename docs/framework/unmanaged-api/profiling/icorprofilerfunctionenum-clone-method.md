---
title: Método ICorProfilerFunctionEnum::Clone
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Clone Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Clone
helpviewer_keywords:
- ICorProfilerFunctionEnum::Clone method [.NET Framework profiling]
- Clone method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0c3d4835-e111-4e82-af6d-53f140b8f2c9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5ffd1fcc36f0c6cc3c5f063c5a916e8918839566
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135584"
---
# <a name="icorprofilerfunctionenumclone-method"></a><span data-ttu-id="e7f8b-102">Método ICorProfilerFunctionEnum::Clone</span><span class="sxs-lookup"><span data-stu-id="e7f8b-102">ICorProfilerFunctionEnum::Clone Method</span></span>
<span data-ttu-id="e7f8b-103">Obtém um ponteiro de interface para uma cópia deste [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="e7f8b-103">Gets an interface pointer to a copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7f8b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e7f8b-104">Syntax</span></span>  
  
```  
HRESULT Clone([out] ICorProfilerFunctionEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7f8b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e7f8b-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="e7f8b-106">[out] Um ponteiro para o ponteiro de interface, que, por sua vez, aponta para a cópia deste [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="e7f8b-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span></span> <span data-ttu-id="e7f8b-107">A cópia do enumerador mantém seu próprio estado de enumeração separadamente deste enumerador.</span><span class="sxs-lookup"><span data-stu-id="e7f8b-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="e7f8b-108">No entanto, a posição do cursor inicial da cópia é igual a posição atual do cursor deste enumerador.</span><span class="sxs-lookup"><span data-stu-id="e7f8b-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7f8b-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e7f8b-109">Requirements</span></span>  
 <span data-ttu-id="e7f8b-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7f8b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7f8b-111">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e7f8b-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e7f8b-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7f8b-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="e7f8b-113">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="e7f8b-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e7f8b-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e7f8b-114">See also</span></span>

- [<span data-ttu-id="e7f8b-115">Interface ICorProfilerFunctionEnum</span><span class="sxs-lookup"><span data-stu-id="e7f8b-115">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="e7f8b-116">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="e7f8b-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
