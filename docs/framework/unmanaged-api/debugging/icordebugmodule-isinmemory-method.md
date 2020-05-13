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
ms.openlocfilehash: c5fa55a84ed8907a5072f6099c3bf02cd6d78683
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213121"
---
# <a name="icordebugmoduleisinmemory-method"></a><span data-ttu-id="11096-102">Método ICorDebugModule::IsInMemory</span><span class="sxs-lookup"><span data-stu-id="11096-102">ICorDebugModule::IsInMemory Method</span></span>
<span data-ttu-id="11096-103">Obtém um valor que indica se esse módulo existe apenas na memória.</span><span class="sxs-lookup"><span data-stu-id="11096-103">Gets a value that indicates whether this module exists only in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11096-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="11096-104">Syntax</span></span>  
  
```cpp  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11096-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="11096-105">Parameters</span></span>  
 `pInMemory`  
 <span data-ttu-id="11096-106">[fora] `true` Se esse módulo existir apenas na memória; caso contrário, `false` .</span><span class="sxs-lookup"><span data-stu-id="11096-106">[out] `true` if this module exists only in memory; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11096-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="11096-107">Remarks</span></span>  
 <span data-ttu-id="11096-108">O Common Language Runtime (CLR) dá suporte ao carregamento de módulos de fluxos brutos de bytes.</span><span class="sxs-lookup"><span data-stu-id="11096-108">The common language runtime (CLR) supports the loading of modules from raw streams of bytes.</span></span> <span data-ttu-id="11096-109">Esses módulos são chamados *de módulos na memória* e não existem no disco.</span><span class="sxs-lookup"><span data-stu-id="11096-109">Such modules are called *in-memory modules* and do not exist on disk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11096-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="11096-110">Requirements</span></span>  
 <span data-ttu-id="11096-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11096-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11096-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="11096-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="11096-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11096-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11096-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11096-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11096-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="11096-115">See also</span></span>
