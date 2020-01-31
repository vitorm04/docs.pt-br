---
title: Método ICorProfilerObjectEnum::Clone
ms.date: 03/30/2017
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
ms.openlocfilehash: 8153dbd27e168e3a5bd8e5aeada955a0382aaf75
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868246"
---
# <a name="icorprofilerobjectenumclone-method"></a><span data-ttu-id="5352a-102">Método ICorProfilerObjectEnum::Clone</span><span class="sxs-lookup"><span data-stu-id="5352a-102">ICorProfilerObjectEnum::Clone Method</span></span>
<span data-ttu-id="5352a-103">Obtém um ponteiro de interface para uma cópia desta interface [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="5352a-103">Gets an interface pointer to a copy of this [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5352a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5352a-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorProfilerObjectEnum   **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5352a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5352a-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="5352a-106">fora Um ponteiro para o ponteiro de interface que, por sua vez, aponta para a cópia dessa `ICorProfilerObjectEnum` interface.</span><span class="sxs-lookup"><span data-stu-id="5352a-106">[out] A pointer to the interface pointer that in turn points to the copy of this `ICorProfilerObjectEnum` interface.</span></span> <span data-ttu-id="5352a-107">A cópia mantém seu próprio estado de enumeração separadamente deste.</span><span class="sxs-lookup"><span data-stu-id="5352a-107">The copy maintains its own enumeration state separately from this one.</span></span> <span data-ttu-id="5352a-108">No entanto, a posição inicial do cursor da cópia será a mesma posição do cursor atual do enumerador.</span><span class="sxs-lookup"><span data-stu-id="5352a-108">However, the copy's initial cursor position will be the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5352a-109">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="5352a-109">Requirements</span></span>  
 <span data-ttu-id="5352a-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5352a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5352a-111">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5352a-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5352a-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5352a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5352a-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5352a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5352a-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="5352a-114">See also</span></span>

- [<span data-ttu-id="5352a-115">Interface ICorProfilerObjectEnum</span><span class="sxs-lookup"><span data-stu-id="5352a-115">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
