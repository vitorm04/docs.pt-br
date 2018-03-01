---
title: "Método ICorDebugModule::IsInMemory"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugModule.IsInMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::IsInMemory
helpviewer_keywords:
- IsInMemory method [.NET Framework debugging]
- ICorDebugModule::IsInMemory method [.NET Framework debugging]
ms.assetid: 89940711-98e7-4aa6-bffc-5e39e91e1b7d
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 448458874c4de96503261bc0fe34fae160395c49
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmoduleisinmemory-method"></a><span data-ttu-id="ea437-102">Método ICorDebugModule::IsInMemory</span><span class="sxs-lookup"><span data-stu-id="ea437-102">ICorDebugModule::IsInMemory Method</span></span>
<span data-ttu-id="ea437-103">Obtém um valor que indica se este módulo existe apenas na memória.</span><span class="sxs-lookup"><span data-stu-id="ea437-103">Gets a value that indicates whether this module exists only in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea437-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ea437-104">Syntax</span></span>  
  
```  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ea437-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ea437-105">Parameters</span></span>  
 `pInMemory`  
 <span data-ttu-id="ea437-106">[out] `true` se esse módulo existe apenas na memória; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="ea437-106">[out] `true` if this module exists only in memory; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea437-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="ea437-107">Remarks</span></span>  
 <span data-ttu-id="ea437-108">O common language runtime (CLR) suporta o carregamento dos módulos de fluxos brutos de bytes.</span><span class="sxs-lookup"><span data-stu-id="ea437-108">The common language runtime (CLR) supports the loading of modules from raw streams of bytes.</span></span> <span data-ttu-id="ea437-109">Esses módulos são chamados de *módulos de memória* e não existe no disco.</span><span class="sxs-lookup"><span data-stu-id="ea437-109">Such modules are called *in-memory modules* and do not exist on disk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea437-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ea437-110">Requirements</span></span>  
 <span data-ttu-id="ea437-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea437-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea437-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ea437-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ea437-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ea437-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea437-114">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea437-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea437-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ea437-115">See Also</span></span>  
    
 
