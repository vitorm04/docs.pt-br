---
title: "Método ICorProfilerObjectEnum::GetCount"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerObjectEnum.GetCount
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerObjectEnum::GetCount
helpviewer_keywords:
- ICorProfilerObjectEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: 166b0761-ed80-4ccd-9973-dc20e61bf8fa
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0680921a64d8f8bf9cdc5b4137c56dd8dfb7878e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerobjectenumgetcount-method"></a><span data-ttu-id="f2b50-102">Método ICorProfilerObjectEnum::GetCount</span><span class="sxs-lookup"><span data-stu-id="f2b50-102">ICorProfilerObjectEnum::GetCount Method</span></span>
<span data-ttu-id="f2b50-103">Obtém o número total de objetos congelados na coleção.</span><span class="sxs-lookup"><span data-stu-id="f2b50-103">Gets the total number of frozen objects in the collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2b50-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f2b50-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f2b50-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f2b50-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="f2b50-106">[out] Um ponteiro para o número de objetos congelados na coleção.</span><span class="sxs-lookup"><span data-stu-id="f2b50-106">[out] A pointer to the number of frozen objects in the collection.</span></span>  
  
 <span data-ttu-id="f2b50-107">Esse método sempre retornará zero no .NET Framework versão 3.5 Service Pack 1 (SP1) e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="f2b50-107">This method will always return zero in the .NET Framework version 3.5 Service Pack 1 (SP1) and later versions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2b50-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f2b50-108">Requirements</span></span>  
 <span data-ttu-id="f2b50-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2b50-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2b50-110">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f2b50-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f2b50-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2b50-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2b50-112">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2b50-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2b50-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f2b50-113">See Also</span></span>  
 [<span data-ttu-id="f2b50-114">Interface ICorProfilerObjectEnum</span><span class="sxs-lookup"><span data-stu-id="f2b50-114">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
