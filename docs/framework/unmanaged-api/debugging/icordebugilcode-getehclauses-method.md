---
title: ICorDebugILCode::Método GetEHClauses
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode.GetEHClauses
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: cf7a0e00-06ae-47a5-8037-598b26196802
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e890629f307e3d3cff11dabdb2db90a5e88ece5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59105048"
---
# <a name="icordebugilcodegetehclauses-method"></a><span data-ttu-id="01e35-102">ICorDebugILCode::Método GetEHClauses</span><span class="sxs-lookup"><span data-stu-id="01e35-102">ICorDebugILCode::GetEHClauses Method</span></span>
<span data-ttu-id="01e35-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="01e35-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="01e35-104">Retorna um ponteiro para uma lista de cláusulas de tratamento de exceção (EH) que estão definidas para esta linguagem intermediária (IL).</span><span class="sxs-lookup"><span data-stu-id="01e35-104">Returns a pointer to a list of exception handling (EH) clauses that are defined for this intermediate language (IL).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01e35-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="01e35-105">Syntax</span></span>  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01e35-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="01e35-106">Parameters</span></span>  
 `cClauses`  
 <span data-ttu-id="01e35-107">[in] A capacidade de armazenamento da matriz de `clauses`.</span><span class="sxs-lookup"><span data-stu-id="01e35-107">[in] The storage capacity of the `clauses` array.</span></span> <span data-ttu-id="01e35-108">Consulte a seção Comentários para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="01e35-108">See the Remarks section for more information.</span></span>  
  
 `pcClauses`  
 <span data-ttu-id="01e35-109">[out] O número de cláusulas sobre quais informações são gravadas na matriz `clauses`.</span><span class="sxs-lookup"><span data-stu-id="01e35-109">[out] The number of clauses about which information is written to the `clauses` array.</span></span>  
  
 <span data-ttu-id="01e35-110">cláusulas</span><span class="sxs-lookup"><span data-stu-id="01e35-110">clauses</span></span>  
 <span data-ttu-id="01e35-111">[out] Uma matriz de [CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) objetos que contêm informações sobre cláusulas definidas para esse IL de tratamento de exceção.</span><span class="sxs-lookup"><span data-stu-id="01e35-111">[out] An array of [CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) objects that contain information on exception handling clauses defined for this IL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01e35-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="01e35-112">Remarks</span></span>  
 <span data-ttu-id="01e35-113">Se `cClauses` é 0 e `pcClauses` é não -**nulo**, `pcClauses` é definido como o número de cláusulas de tratamento de exceção disponível.</span><span class="sxs-lookup"><span data-stu-id="01e35-113">If `cClauses` is 0 and `pcClauses` is non-**null**, `pcClauses` is set to the number of available exception handling clauses.</span></span> <span data-ttu-id="01e35-114">Se `cClauses` for não zero, representará a capacidade de armazenamento da matriz do `clauses`.</span><span class="sxs-lookup"><span data-stu-id="01e35-114">If `cClauses` is non-zero, it represents the storage capacity of the `clauses` array.</span></span> <span data-ttu-id="01e35-115">Quando o método retorna, `clauses` contém o máximo de itens `cClauses` e `pcClauses` estará definido como o número de cláusulas realmente gravadas na matriz `clauses`.</span><span class="sxs-lookup"><span data-stu-id="01e35-115">When the method returns, `clauses` contains a maximum of `cClauses` items, and `pcClauses` is set to the number of clauses actually written to the `clauses` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01e35-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="01e35-116">Requirements</span></span>  
 <span data-ttu-id="01e35-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01e35-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01e35-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="01e35-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="01e35-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01e35-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01e35-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01e35-120">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01e35-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="01e35-121">See also</span></span>

- [<span data-ttu-id="01e35-122">Interface ICorDebugILCode</span><span class="sxs-lookup"><span data-stu-id="01e35-122">ICorDebugILCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)
- [<span data-ttu-id="01e35-123">Estrutura CorDebugEHClause</span><span class="sxs-lookup"><span data-stu-id="01e35-123">CorDebugEHClause Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)
- [<span data-ttu-id="01e35-124">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="01e35-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
