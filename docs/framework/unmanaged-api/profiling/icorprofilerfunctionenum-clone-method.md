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
ms.openlocfilehash: 2faa7185202b46e77e501d69bb471391a7c6eb68
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864616"
---
# <a name="icorprofilerfunctionenumclone-method"></a><span data-ttu-id="21e98-102">Método ICorProfilerFunctionEnum::Clone</span><span class="sxs-lookup"><span data-stu-id="21e98-102">ICorProfilerFunctionEnum::Clone Method</span></span>
<span data-ttu-id="21e98-103">Obtém um ponteiro de interface para uma cópia desta interface [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="21e98-103">Gets an interface pointer to a copy of this [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21e98-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="21e98-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone([out] ICorProfilerFunctionEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21e98-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="21e98-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="21e98-106">fora Um ponteiro para o ponteiro de interface, que, por sua vez, aponta para a cópia dessa interface [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="21e98-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) interface.</span></span> <span data-ttu-id="21e98-107">A cópia do enumerador mantém seu próprio estado de enumeração separadamente deste enumerador.</span><span class="sxs-lookup"><span data-stu-id="21e98-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="21e98-108">No entanto, a posição inicial do cursor da cópia é igual à posição atual do cursor do enumerador.</span><span class="sxs-lookup"><span data-stu-id="21e98-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21e98-109">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="21e98-109">Requirements</span></span>  
 <span data-ttu-id="21e98-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21e98-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21e98-111">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="21e98-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="21e98-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21e98-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21e98-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21e98-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21e98-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="21e98-114">See also</span></span>

- [<span data-ttu-id="21e98-115">Interface ICorProfilerFunctionEnum</span><span class="sxs-lookup"><span data-stu-id="21e98-115">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="21e98-116">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="21e98-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
