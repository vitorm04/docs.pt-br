---
title: Método ICorDebugModule::IsInMemory
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d79a8b0c3c56ffe2b8f57ec26f5942ee0d681194
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59187584"
---
# <a name="icordebugmoduleisinmemory-method"></a><span data-ttu-id="3b37f-102">Método ICorDebugModule::IsInMemory</span><span class="sxs-lookup"><span data-stu-id="3b37f-102">ICorDebugModule::IsInMemory Method</span></span>
<span data-ttu-id="3b37f-103">Obtém um valor que indica se este módulo existe apenas na memória.</span><span class="sxs-lookup"><span data-stu-id="3b37f-103">Gets a value that indicates whether this module exists only in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b37f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3b37f-104">Syntax</span></span>  
  
```  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b37f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3b37f-105">Parameters</span></span>  
 `pInMemory`  
 <span data-ttu-id="3b37f-106">[out] `true` se esse módulo existe apenas na memória; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="3b37f-106">[out] `true` if this module exists only in memory; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b37f-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="3b37f-107">Remarks</span></span>  
 <span data-ttu-id="3b37f-108">O common language runtime (CLR) dá suporte o carregamento de módulos de brutos fluxos de bytes.</span><span class="sxs-lookup"><span data-stu-id="3b37f-108">The common language runtime (CLR) supports the loading of modules from raw streams of bytes.</span></span> <span data-ttu-id="3b37f-109">Esses módulos são chamados *módulos de memória* e não existem no disco.</span><span class="sxs-lookup"><span data-stu-id="3b37f-109">Such modules are called *in-memory modules* and do not exist on disk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b37f-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3b37f-110">Requirements</span></span>  
 <span data-ttu-id="3b37f-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b37f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b37f-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3b37f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3b37f-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b37f-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="3b37f-114">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="3b37f-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3b37f-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3b37f-115">See also</span></span>
