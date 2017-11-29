---
title: "ICorDebugILCode::Método GetEHClauses"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugILCode.GetEHClauses
api_location: mscordbi.dll
api_type: COM
ms.assetid: cf7a0e00-06ae-47a5-8037-598b26196802
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 39d30ef572423d8cb988c074971de095f1709e8c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugilcodegetehclauses-method"></a><span data-ttu-id="2cd8b-102">ICorDebugILCode::Método GetEHClauses</span><span class="sxs-lookup"><span data-stu-id="2cd8b-102">ICorDebugILCode::GetEHClauses Method</span></span>
<span data-ttu-id="2cd8b-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="2cd8b-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="2cd8b-104">Retorna um ponteiro para uma lista de cláusulas de tratamento de exceção (EH) que estão definidas para esta linguagem intermediária (IL).</span><span class="sxs-lookup"><span data-stu-id="2cd8b-104">Returns a pointer to a list of exception handling (EH) clauses that are defined for this intermediate language (IL).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cd8b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2cd8b-105">Syntax</span></span>  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2cd8b-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2cd8b-106">Parameters</span></span>  
 `cClauses`  
 <span data-ttu-id="2cd8b-107">[in] A capacidade de armazenamento da matriz de `clauses`.</span><span class="sxs-lookup"><span data-stu-id="2cd8b-107">[in] The storage capacity of the `clauses` array.</span></span> <span data-ttu-id="2cd8b-108">Consulte a seção Comentários para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="2cd8b-108">See the Remarks section for more information.</span></span>  
  
 `pcClauses`  
 <span data-ttu-id="2cd8b-109">[out] O número de cláusulas sobre quais informações são gravadas na matriz `clauses`.</span><span class="sxs-lookup"><span data-stu-id="2cd8b-109">[out] The number of clauses about which information is written to the `clauses` array.</span></span>  
  
 <span data-ttu-id="2cd8b-110">cláusulas</span><span class="sxs-lookup"><span data-stu-id="2cd8b-110">clauses</span></span>  
 <span data-ttu-id="2cd8b-111">[out] Uma matriz de [CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) objetos que contêm informações sobre cláusulas definidas para esse nível de integridade de tratamento de exceção.</span><span class="sxs-lookup"><span data-stu-id="2cd8b-111">[out] An array of [CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) objects that contain information on exception handling clauses defined for this IL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2cd8b-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="2cd8b-112">Remarks</span></span>  
 <span data-ttu-id="2cd8b-113">Se `cClauses` é 0 e `pcClauses` é não -**nulo**, `pcClauses` é definido como o número de cláusulas de tratamento de exceção disponível.</span><span class="sxs-lookup"><span data-stu-id="2cd8b-113">If `cClauses` is 0 and `pcClauses` is non-**null**, `pcClauses` is set to the number of available exception handling clauses.</span></span> <span data-ttu-id="2cd8b-114">Se `cClauses` for não zero, representará a capacidade de armazenamento da matriz do `clauses`.</span><span class="sxs-lookup"><span data-stu-id="2cd8b-114">If `cClauses` is non-zero, it represents the storage capacity of the `clauses` array.</span></span> <span data-ttu-id="2cd8b-115">Quando o método retorna, `clauses` contém o máximo de itens `cClauses` e `pcClauses` estará definido como o número de cláusulas realmente gravadas na matriz `clauses`.</span><span class="sxs-lookup"><span data-stu-id="2cd8b-115">When the method returns, `clauses` contains a maximum of `cClauses` items, and `pcClauses` is set to the number of clauses actually written to the `clauses` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cd8b-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2cd8b-116">Requirements</span></span>  
 <span data-ttu-id="2cd8b-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2cd8b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cd8b-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2cd8b-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2cd8b-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2cd8b-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2cd8b-120">**Versões do .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cd8b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cd8b-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2cd8b-121">See Also</span></span>  
 [<span data-ttu-id="2cd8b-122">Interface ICorDebugILCode</span><span class="sxs-lookup"><span data-stu-id="2cd8b-122">ICorDebugILCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)  
 [<span data-ttu-id="2cd8b-123">Estrutura CorDebugEHClause</span><span class="sxs-lookup"><span data-stu-id="2cd8b-123">CorDebugEHClause Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)  
 [<span data-ttu-id="2cd8b-124">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="2cd8b-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
