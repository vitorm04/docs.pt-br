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
ms.openlocfilehash: 1384acff4ea3d1aa820b065cd2c56f649f0cbdbb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127918"
---
# <a name="icordebugmoduleisinmemory-method"></a><span data-ttu-id="e1987-102">Método ICorDebugModule::IsInMemory</span><span class="sxs-lookup"><span data-stu-id="e1987-102">ICorDebugModule::IsInMemory Method</span></span>
<span data-ttu-id="e1987-103">Obtém um valor que indica se esse módulo existe apenas na memória.</span><span class="sxs-lookup"><span data-stu-id="e1987-103">Gets a value that indicates whether this module exists only in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1987-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e1987-104">Syntax</span></span>  
  
```cpp  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1987-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1987-105">Parameters</span></span>  
 `pInMemory`  
 <span data-ttu-id="e1987-106">[fora] `true` se esse módulo existir apenas na memória; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="e1987-106">[out] `true` if this module exists only in memory; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1987-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="e1987-107">Remarks</span></span>  
 <span data-ttu-id="e1987-108">O Common Language Runtime (CLR) dá suporte ao carregamento de módulos de fluxos brutos de bytes.</span><span class="sxs-lookup"><span data-stu-id="e1987-108">The common language runtime (CLR) supports the loading of modules from raw streams of bytes.</span></span> <span data-ttu-id="e1987-109">Esses módulos são chamados *de módulos na memória* e não existem no disco.</span><span class="sxs-lookup"><span data-stu-id="e1987-109">Such modules are called *in-memory modules* and do not exist on disk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1987-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e1987-110">Requirements</span></span>  
 <span data-ttu-id="e1987-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1987-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1987-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e1987-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e1987-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1987-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1987-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1987-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1987-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e1987-115">See also</span></span>
