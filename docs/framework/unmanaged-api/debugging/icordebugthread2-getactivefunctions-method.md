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
ms.openlocfilehash: 9b9a301714ea60b4e3220eb75721e56e39bd9659
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139939"
---
# <a name="icordebugthread2getactivefunctions-method"></a><span data-ttu-id="aef7b-102">Método ICorDebugThread2::GetActiveFunctions</span><span class="sxs-lookup"><span data-stu-id="aef7b-102">ICorDebugThread2::GetActiveFunctions Method</span></span>
<span data-ttu-id="aef7b-103">Obtém informações sobre a função ativa em cada um dos quadros deste thread.</span><span class="sxs-lookup"><span data-stu-id="aef7b-103">Gets information about the active function in each of this thread's frames.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aef7b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aef7b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveFunctions (  
    [in]   ULONG32             cFunctions,  
    [out]  ULONG32             *pcFunctions,  
    [in, out, size_is(cFunctions), length_is(*pcFunctions)]  
        COR_ACTIVE_FUNCTION    pFunctions[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aef7b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="aef7b-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="aef7b-106">no O tamanho da matriz de `pFunctions`.</span><span class="sxs-lookup"><span data-stu-id="aef7b-106">[in] The size of the `pFunctions` array.</span></span>  
  
 `pcFunctions`  
 <span data-ttu-id="aef7b-107">fora Um ponteiro para o número de objetos retornados na matriz de `pFunctions`.</span><span class="sxs-lookup"><span data-stu-id="aef7b-107">[out] A pointer to the number of objects returned in the `pFunctions` array.</span></span> <span data-ttu-id="aef7b-108">O número de objetos retornados será igual ao número de quadros gerenciados na pilha.</span><span class="sxs-lookup"><span data-stu-id="aef7b-108">The number of objects returned will be equal to the number of managed frames on the stack.</span></span>  
  
 `pFunctions`  
 <span data-ttu-id="aef7b-109">[entrada, saída] Uma matriz de objetos COR_ACTIVE_FUNCTION, cada um dos quais contém informações sobre as funções ativas nos quadros deste thread.</span><span class="sxs-lookup"><span data-stu-id="aef7b-109">[in, out] An array of COR_ACTIVE_FUNCTION objects, each of which contains information about the active functions in this thread's frames.</span></span>  
  
 <span data-ttu-id="aef7b-110">O primeiro elemento será usado para o quadro folha e assim por diante de volta para a raiz da pilha.</span><span class="sxs-lookup"><span data-stu-id="aef7b-110">The first element will be used for the leaf frame, and so on back to the root of the stack.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aef7b-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="aef7b-111">Remarks</span></span>  
 <span data-ttu-id="aef7b-112">Se `pFunctions` for nulo na entrada, `GetActiveFunctions` retornará apenas o número de funções que estão na pilha.</span><span class="sxs-lookup"><span data-stu-id="aef7b-112">If `pFunctions` is null on input, `GetActiveFunctions` returns only the number of functions that are on the stack.</span></span> <span data-ttu-id="aef7b-113">Ou seja, se `pFunctions` for nulo na entrada, `GetActiveFunctions` retornará um valor somente em `pcFunctions`.</span><span class="sxs-lookup"><span data-stu-id="aef7b-113">That is, If `pFunctions` is null on input, `GetActiveFunctions` returns a value only in `pcFunctions`.</span></span>  
  
 <span data-ttu-id="aef7b-114">O método `GetActiveFunctions` é destinado como uma otimização ao obter as mesmas informações de quadros em um rastreamento de pilha e inclui apenas quadros que teriam um objeto ICorDebugILFrame para eles no rastreamento de pilha completo.</span><span class="sxs-lookup"><span data-stu-id="aef7b-114">The `GetActiveFunctions` method is intended as an optimization over getting the same information from frames in a stack trace, and includes only frames that would have had an ICorDebugILFrame object for them in the full stack trace.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aef7b-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aef7b-115">Requirements</span></span>  
 <span data-ttu-id="aef7b-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aef7b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aef7b-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aef7b-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aef7b-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aef7b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aef7b-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aef7b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
