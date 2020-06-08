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
ms.openlocfilehash: d6f348eb781efdef89926ec1bc267281bf3a5004
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503101"
---
# <a name="icorprofilerfunctionenumclone-method"></a><span data-ttu-id="80846-102">Método ICorProfilerFunctionEnum::Clone</span><span class="sxs-lookup"><span data-stu-id="80846-102">ICorProfilerFunctionEnum::Clone Method</span></span>
<span data-ttu-id="80846-103">Obtém um ponteiro de interface para uma cópia desta interface [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="80846-103">Gets an interface pointer to a copy of this [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80846-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="80846-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone([out] ICorProfilerFunctionEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80846-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="80846-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="80846-106">fora Um ponteiro para o ponteiro de interface, que, por sua vez, aponta para a cópia dessa interface [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="80846-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) interface.</span></span> <span data-ttu-id="80846-107">A cópia do enumerador mantém seu próprio estado de enumeração separadamente deste enumerador.</span><span class="sxs-lookup"><span data-stu-id="80846-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="80846-108">No entanto, a posição inicial do cursor da cópia é igual à posição atual do cursor do enumerador.</span><span class="sxs-lookup"><span data-stu-id="80846-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80846-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="80846-109">Requirements</span></span>  
 <span data-ttu-id="80846-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80846-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80846-111">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="80846-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="80846-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="80846-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80846-113">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80846-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80846-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="80846-114">See also</span></span>

- [<span data-ttu-id="80846-115">Interface ICorProfilerFunctionEnum</span><span class="sxs-lookup"><span data-stu-id="80846-115">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="80846-116">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="80846-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
