---
title: Método ICorProfilerModuleEnum::Clone
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Clone Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Clone method [.NET Framework profiling]
ms.assetid: 7dec7e36-8d88-416d-b437-abf98b76c1df
topic_type:
- apiref
ms.openlocfilehash: 395340d497294c89c59216ab5f294070690b74a9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444662"
---
# <a name="icorprofilermoduleenumclone-method"></a><span data-ttu-id="eef18-102">Método ICorProfilerModuleEnum::Clone</span><span class="sxs-lookup"><span data-stu-id="eef18-102">ICorProfilerModuleEnum::Clone Method</span></span>
<span data-ttu-id="eef18-103">Obtém um ponteiro de interface para uma cópia desta interface [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="eef18-103">Gets an interface pointer to a copy of this [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eef18-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eef18-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone([out] ICorProfilerObjectEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eef18-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="eef18-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="eef18-106">fora Um ponteiro para o ponteiro de interface que, por sua vez, aponta para a cópia dessa interface [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="eef18-106">[out] A pointer to the interface pointer that in turn points to the copy of this [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span></span> <span data-ttu-id="eef18-107">A cópia do enumerador mantém seu próprio estado de enumeração separadamente deste enumerador.</span><span class="sxs-lookup"><span data-stu-id="eef18-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="eef18-108">No entanto, a posição inicial do cursor da cópia é igual à posição atual do cursor do enumerador.</span><span class="sxs-lookup"><span data-stu-id="eef18-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eef18-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="eef18-109">Requirements</span></span>  
 <span data-ttu-id="eef18-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eef18-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eef18-111">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="eef18-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eef18-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eef18-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eef18-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eef18-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eef18-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eef18-114">See also</span></span>

- [<span data-ttu-id="eef18-115">Interface ICorProfilerModuleEnum</span><span class="sxs-lookup"><span data-stu-id="eef18-115">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="eef18-116">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="eef18-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
