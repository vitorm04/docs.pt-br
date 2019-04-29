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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 14e8086532eff5dba6883575cc2daf447a32343a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61597655"
---
# <a name="icorprofilerobjectenumclone-method"></a><span data-ttu-id="7b0fa-102">Método ICorProfilerObjectEnum::Clone</span><span class="sxs-lookup"><span data-stu-id="7b0fa-102">ICorProfilerObjectEnum::Clone Method</span></span>
<span data-ttu-id="7b0fa-103">Obtém um ponteiro de interface para uma cópia deste [ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="7b0fa-103">Gets an interface pointer to a copy of this [ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b0fa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7b0fa-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] ICorProfilerObjectEnum   **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b0fa-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7b0fa-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="7b0fa-106">[out] Um ponteiro para o ponteiro de interface que aponta para a cópia deste `ICorProfilerObjectEnum` interface.</span><span class="sxs-lookup"><span data-stu-id="7b0fa-106">[out] A pointer to the interface pointer that in turn points to the copy of this `ICorProfilerObjectEnum` interface.</span></span> <span data-ttu-id="7b0fa-107">A cópia mantém seu próprio estado de enumeração separadamente desta.</span><span class="sxs-lookup"><span data-stu-id="7b0fa-107">The copy maintains its own enumeration state separately from this one.</span></span> <span data-ttu-id="7b0fa-108">No entanto, posição de cursor inicial da cópia será o mesmo que a posição atual do cursor deste enumerador.</span><span class="sxs-lookup"><span data-stu-id="7b0fa-108">However, the copy's initial cursor position will be the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b0fa-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7b0fa-109">Requirements</span></span>  
 <span data-ttu-id="7b0fa-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b0fa-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b0fa-111">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7b0fa-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7b0fa-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b0fa-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b0fa-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b0fa-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b0fa-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7b0fa-114">See also</span></span>

- [<span data-ttu-id="7b0fa-115">Interface ICorProfilerObjectEnum</span><span class="sxs-lookup"><span data-stu-id="7b0fa-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
