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
ms.openlocfilehash: a6b36883ec0914426b4f4c937390c1622faead25
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868285"
---
# <a name="icorprofilermoduleenumclone-method"></a><span data-ttu-id="abe2b-102">Método ICorProfilerModuleEnum::Clone</span><span class="sxs-lookup"><span data-stu-id="abe2b-102">ICorProfilerModuleEnum::Clone Method</span></span>
<span data-ttu-id="abe2b-103">Obtém um ponteiro de interface para uma cópia desta interface [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="abe2b-103">Gets an interface pointer to a copy of this [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abe2b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="abe2b-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone([out] ICorProfilerObjectEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="abe2b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="abe2b-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="abe2b-106">fora Um ponteiro para o ponteiro de interface que, por sua vez, aponta para a cópia dessa interface [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="abe2b-106">[out] A pointer to the interface pointer that in turn points to the copy of this [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span> <span data-ttu-id="abe2b-107">A cópia do enumerador mantém seu próprio estado de enumeração separadamente deste enumerador.</span><span class="sxs-lookup"><span data-stu-id="abe2b-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="abe2b-108">No entanto, a posição inicial do cursor da cópia é igual à posição atual do cursor do enumerador.</span><span class="sxs-lookup"><span data-stu-id="abe2b-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abe2b-109">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="abe2b-109">Requirements</span></span>  
 <span data-ttu-id="abe2b-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abe2b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abe2b-111">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="abe2b-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="abe2b-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="abe2b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="abe2b-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abe2b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abe2b-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="abe2b-114">See also</span></span>

- [<span data-ttu-id="abe2b-115">Interface ICorProfilerModuleEnum</span><span class="sxs-lookup"><span data-stu-id="abe2b-115">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="abe2b-116">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="abe2b-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
