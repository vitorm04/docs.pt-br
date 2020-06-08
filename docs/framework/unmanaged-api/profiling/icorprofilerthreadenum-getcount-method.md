---
title: Método ICorProfilerThreadEnum::GetCount
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.GetCount
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::GetCount
helpviewer_keywords:
- ICorProfilerThreadEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: d6dbdc4a-6115-455d-a3f3-704a81d3646b
topic_type:
- apiref
ms.openlocfilehash: 4bc2ea083d5278afc9278d388f57b048f7682ca6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494391"
---
# <a name="icorprofilerthreadenumgetcount-method"></a><span data-ttu-id="ef894-102">Método ICorProfilerThreadEnum::GetCount</span><span class="sxs-lookup"><span data-stu-id="ef894-102">ICorProfilerThreadEnum::GetCount Method</span></span>
<span data-ttu-id="ef894-103">Obtém o número de threads que são usados pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ef894-103">Gets the number of threads that are used by the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef894-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ef894-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (    [out] ULONG * pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef894-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ef894-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="ef894-106">fora O número de threads usados pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ef894-106">[out] The number of threads used by the application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef894-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ef894-107">Requirements</span></span>  
 <span data-ttu-id="ef894-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef894-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef894-109">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ef894-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ef894-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef894-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef894-111">**.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef894-111">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef894-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="ef894-112">See also</span></span>

- [<span data-ttu-id="ef894-113">Interface ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="ef894-113">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="ef894-114">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="ef894-114">Profiling Interfaces</span></span>](profiling-interfaces.md)
