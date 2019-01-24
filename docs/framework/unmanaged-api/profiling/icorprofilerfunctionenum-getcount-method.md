---
title: Método ICorProfilerFunctionEnum::GetCount
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.GetCount Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::GetCount
helpviewer_keywords:
- ICorProfilerFunctionEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 62ec65e3-3e9d-400b-ae61-d24b8963995b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c7612b46cb0d7879e8e8301ae77d03b931856b85
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54531701"
---
# <a name="icorprofilerfunctionenumgetcount-method"></a><span data-ttu-id="90c46-102">Método ICorProfilerFunctionEnum::GetCount</span><span class="sxs-lookup"><span data-stu-id="90c46-102">ICorProfilerFunctionEnum::GetCount Method</span></span>
<span data-ttu-id="90c46-103">Obtém o número de funções que foram carregados pelo aplicativo ou à força pelo criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="90c46-103">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90c46-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="90c46-104">Syntax</span></span>  
  
```  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="90c46-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="90c46-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="90c46-106">[out] O número de funções que foram carregados.</span><span class="sxs-lookup"><span data-stu-id="90c46-106">[out] The number of functions that were loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90c46-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="90c46-107">Requirements</span></span>  
 <span data-ttu-id="90c46-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90c46-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90c46-109">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="90c46-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="90c46-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90c46-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90c46-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90c46-111">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90c46-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90c46-112">See also</span></span>
- [<span data-ttu-id="90c46-113">Interface ICorProfilerFunctionEnum</span><span class="sxs-lookup"><span data-stu-id="90c46-113">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="90c46-114">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="90c46-114">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
