---
title: Método ICorProfilerThreadEnum::Clone
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Clone
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Clone method [.NET Framework profiling]
ms.assetid: 5a278bc9-88e2-4c69-b035-9d550dd77081
topic_type:
- apiref
ms.openlocfilehash: 890bb9bdd3b639d38f4f290eed86ad72b6a53f0f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494443"
---
# <a name="icorprofilerthreadenumclone-method"></a><span data-ttu-id="24aaa-102">Método ICorProfilerThreadEnum::Clone</span><span class="sxs-lookup"><span data-stu-id="24aaa-102">ICorProfilerThreadEnum::Clone Method</span></span>
<span data-ttu-id="24aaa-103">Obtém um ponteiro de interface para uma cópia desta interface [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="24aaa-103">Gets an interface pointer to a copy of this [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24aaa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="24aaa-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (    [out] ICorProfilerThreadEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24aaa-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="24aaa-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="24aaa-106">fora Um ponteiro para o ponteiro de interface, que, por sua vez, aponta para a cópia dessa interface [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="24aaa-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) interface.</span></span> <span data-ttu-id="24aaa-107">A cópia do enumerador mantém seu próprio estado de enumeração separadamente deste enumerador.</span><span class="sxs-lookup"><span data-stu-id="24aaa-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="24aaa-108">No entanto, a posição inicial do cursor da cópia é igual à atual posição do cursor do enumerador.</span><span class="sxs-lookup"><span data-stu-id="24aaa-108">However, the initial cursor position of the copy is the same as this current cursor position of the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24aaa-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="24aaa-109">Requirements</span></span>  
 <span data-ttu-id="24aaa-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24aaa-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24aaa-111">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="24aaa-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="24aaa-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24aaa-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24aaa-113">**.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24aaa-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24aaa-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="24aaa-114">See also</span></span>

- [<span data-ttu-id="24aaa-115">ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="24aaa-115">ICorProfilerThreadEnum</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="24aaa-116">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="24aaa-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
