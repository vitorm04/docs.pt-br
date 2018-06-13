---
title: Método ICorDebugThread2::GetActiveFunctions
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetActiveFunctions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetActiveFunctions
helpviewer_keywords:
- GetActiveFunctions method [.NET Framework debugging]
- ICorDebugThread2::GetActiveFunctions method [.NET Framework debugging]
ms.assetid: 27fae01a-ecec-423a-973e-24f8de55826c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f7ed7787f0302826cab67664780177f05e551199
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421100"
---
# <a name="icordebugthread2getactivefunctions-method"></a><span data-ttu-id="a0c2f-102">Método ICorDebugThread2::GetActiveFunctions</span><span class="sxs-lookup"><span data-stu-id="a0c2f-102">ICorDebugThread2::GetActiveFunctions Method</span></span>
<span data-ttu-id="a0c2f-103">Obtém informações sobre a função active em cada um dos quadros desse segmento.</span><span class="sxs-lookup"><span data-stu-id="a0c2f-103">Gets information about the active function in each of this thread's frames.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0c2f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a0c2f-104">Syntax</span></span>  
  
```  
HRESULT GetActiveFunctions (  
    [in]   ULONG32             cFunctions,  
    [out]  ULONG32             *pcFunctions,  
    [in, out, size_is(cFunctions), length_is(*pcFunctions)]  
        COR_ACTIVE_FUNCTION    pFunctions[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a0c2f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a0c2f-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="a0c2f-106">[in] O tamanho do `pFunctions` matriz.</span><span class="sxs-lookup"><span data-stu-id="a0c2f-106">[in] The size of the `pFunctions` array.</span></span>  
  
 `pcFunctions`  
 <span data-ttu-id="a0c2f-107">[out] Um ponteiro para o número de objetos retornados na `pFunctions` matriz.</span><span class="sxs-lookup"><span data-stu-id="a0c2f-107">[out] A pointer to the number of objects returned in the `pFunctions` array.</span></span> <span data-ttu-id="a0c2f-108">O número de objetos retornados será igual ao número de quadros gerenciados na pilha.</span><span class="sxs-lookup"><span data-stu-id="a0c2f-108">The number of objects returned will be equal to the number of managed frames on the stack.</span></span>  
  
 `pFunctions`  
 <span data-ttu-id="a0c2f-109">[out no] Uma matriz de objetos COR_ACTIVE_FUNCTION, cada uma delas contém informações sobre as funções ativas em quadros desse segmento.</span><span class="sxs-lookup"><span data-stu-id="a0c2f-109">[in, out] An array of COR_ACTIVE_FUNCTION objects, each of which contains information about the active functions in this thread's frames.</span></span>  
  
 <span data-ttu-id="a0c2f-110">O primeiro elemento será usado para o quadro folha e assim por diante novamente para a raiz da pilha.</span><span class="sxs-lookup"><span data-stu-id="a0c2f-110">The first element will be used for the leaf frame, and so on back to the root of the stack.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0c2f-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="a0c2f-111">Remarks</span></span>  
 <span data-ttu-id="a0c2f-112">Se `pFunctions` for nulo na entrada, `GetActiveFunctions` retorna somente o número de funções que estão na pilha.</span><span class="sxs-lookup"><span data-stu-id="a0c2f-112">If `pFunctions` is null on input, `GetActiveFunctions` returns only the number of functions that are on the stack.</span></span> <span data-ttu-id="a0c2f-113">Ou seja, se `pFunctions` for nulo na entrada, `GetActiveFunctions` retorna um valor somente em `pcFunctions`.</span><span class="sxs-lookup"><span data-stu-id="a0c2f-113">That is, If `pFunctions` is null on input, `GetActiveFunctions` returns a value only in `pcFunctions`.</span></span>  
  
 <span data-ttu-id="a0c2f-114">O `GetActiveFunctions` método destina-se como uma otimização em obter as mesmas informações de quadros em um rastreamento de pilha e inclui apenas os quadros que teria um objeto ICorDebugILFrame para eles no rastreamento de pilha completos.</span><span class="sxs-lookup"><span data-stu-id="a0c2f-114">The `GetActiveFunctions` method is intended as an optimization over getting the same information from frames in a stack trace, and includes only frames that would have had an ICorDebugILFrame object for them in the full stack trace.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0c2f-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a0c2f-115">Requirements</span></span>  
 <span data-ttu-id="a0c2f-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0c2f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0c2f-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a0c2f-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a0c2f-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0c2f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0c2f-119">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0c2f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
