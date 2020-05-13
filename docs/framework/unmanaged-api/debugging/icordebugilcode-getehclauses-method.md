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
ms.openlocfilehash: e1fd68cd079b381d941d416831133c54e49ac48a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210378"
---
# <a name="icordebugilcodegetehclauses-method"></a><span data-ttu-id="998a4-102">ICorDebugILCode::Método GetEHClauses</span><span class="sxs-lookup"><span data-stu-id="998a4-102">ICorDebugILCode::GetEHClauses Method</span></span>
<span data-ttu-id="998a4-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="998a4-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="998a4-104">Retorna um ponteiro para uma lista de cláusulas de tratamento de exceção (EH) que estão definidas para esta linguagem intermediária (IL).</span><span class="sxs-lookup"><span data-stu-id="998a4-104">Returns a pointer to a list of exception handling (EH) clauses that are defined for this intermediate language (IL).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="998a4-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="998a4-105">Syntax</span></span>  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="998a4-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="998a4-106">Parameters</span></span>  
 `cClauses`  
 <span data-ttu-id="998a4-107">[in] A capacidade de armazenamento da matriz de `clauses`.</span><span class="sxs-lookup"><span data-stu-id="998a4-107">[in] The storage capacity of the `clauses` array.</span></span> <span data-ttu-id="998a4-108">Para obter mais informações, consulte a seção Comentários.</span><span class="sxs-lookup"><span data-stu-id="998a4-108">See the Remarks section for more information.</span></span>  
  
 `pcClauses`  
 <span data-ttu-id="998a4-109">[out] O número de cláusulas sobre quais informações são gravadas na matriz `clauses`.</span><span class="sxs-lookup"><span data-stu-id="998a4-109">[out] The number of clauses about which information is written to the `clauses` array.</span></span>  
  
 <span data-ttu-id="998a4-110">cláusulas</span><span class="sxs-lookup"><span data-stu-id="998a4-110">clauses</span></span>  
 <span data-ttu-id="998a4-111">fora Uma matriz de objetos [CorDebugEHClause](cordebugehclause-structure.md) que contêm informações sobre cláusulas de tratamento de exceção definidas para esse Il.</span><span class="sxs-lookup"><span data-stu-id="998a4-111">[out] An array of [CorDebugEHClause](cordebugehclause-structure.md) objects that contain information on exception handling clauses defined for this IL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="998a4-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="998a4-112">Remarks</span></span>  
 <span data-ttu-id="998a4-113">Se `cClauses` for 0 e `pcClauses` for não**nulo**, `pcClauses` será definido como o número de cláusulas de tratamento de exceção disponíveis.</span><span class="sxs-lookup"><span data-stu-id="998a4-113">If `cClauses` is 0 and `pcClauses` is non-**null**, `pcClauses` is set to the number of available exception handling clauses.</span></span> <span data-ttu-id="998a4-114">Se `cClauses` for não zero, representará a capacidade de armazenamento da matriz do `clauses`.</span><span class="sxs-lookup"><span data-stu-id="998a4-114">If `cClauses` is non-zero, it represents the storage capacity of the `clauses` array.</span></span> <span data-ttu-id="998a4-115">Quando o método retorna, `clauses` contém o máximo de itens `cClauses` e `pcClauses` estará definido como o número de cláusulas realmente gravadas na matriz `clauses`.</span><span class="sxs-lookup"><span data-stu-id="998a4-115">When the method returns, `clauses` contains a maximum of `cClauses` items, and `pcClauses` is set to the number of clauses actually written to the `clauses` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="998a4-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="998a4-116">Requirements</span></span>  
 <span data-ttu-id="998a4-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="998a4-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="998a4-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="998a4-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="998a4-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="998a4-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="998a4-120">**.NET Framework versões:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="998a4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="998a4-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="998a4-121">See also</span></span>

- [<span data-ttu-id="998a4-122">Interface ICorDebugILCode</span><span class="sxs-lookup"><span data-stu-id="998a4-122">ICorDebugILCode Interface</span></span>](icordebugilcode-interface.md)
- [<span data-ttu-id="998a4-123">Estrutura CorDebugEHClause</span><span class="sxs-lookup"><span data-stu-id="998a4-123">CorDebugEHClause Structure</span></span>](cordebugehclause-structure.md)
- [<span data-ttu-id="998a4-124">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="998a4-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
