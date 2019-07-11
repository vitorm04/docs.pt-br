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
ms.openlocfilehash: 223989d883c421be228fb3d6a608643a5246c060
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763703"
---
# <a name="icordebugmoduleisinmemory-method"></a><span data-ttu-id="a3a22-102">Método ICorDebugModule::IsInMemory</span><span class="sxs-lookup"><span data-stu-id="a3a22-102">ICorDebugModule::IsInMemory Method</span></span>
<span data-ttu-id="a3a22-103">Obtém um valor que indica se este módulo existe apenas na memória.</span><span class="sxs-lookup"><span data-stu-id="a3a22-103">Gets a value that indicates whether this module exists only in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3a22-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a3a22-104">Syntax</span></span>  
  
```cpp  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3a22-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a3a22-105">Parameters</span></span>  
 `pInMemory`  
 <span data-ttu-id="a3a22-106">[out] `true` se esse módulo existe apenas na memória; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="a3a22-106">[out] `true` if this module exists only in memory; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3a22-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="a3a22-107">Remarks</span></span>  
 <span data-ttu-id="a3a22-108">O common language runtime (CLR) dá suporte o carregamento de módulos de brutos fluxos de bytes.</span><span class="sxs-lookup"><span data-stu-id="a3a22-108">The common language runtime (CLR) supports the loading of modules from raw streams of bytes.</span></span> <span data-ttu-id="a3a22-109">Esses módulos são chamados *módulos de memória* e não existem no disco.</span><span class="sxs-lookup"><span data-stu-id="a3a22-109">Such modules are called *in-memory modules* and do not exist on disk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3a22-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a3a22-110">Requirements</span></span>  
 <span data-ttu-id="a3a22-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3a22-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3a22-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a3a22-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a3a22-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a3a22-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3a22-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3a22-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3a22-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a3a22-115">See also</span></span>
