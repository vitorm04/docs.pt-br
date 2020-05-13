---
title: Método ICorDebugProcessEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugProcessEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcessEnum::Next
helpviewer_keywords:
- Next method, ICorDebugProcessEnum interface [.NET Framework debugging]
- ICorDebugProcessEnum::Next method [.NET Framework debugging]
ms.assetid: 4ac7077c-8d88-49c4-b360-b3af0c541c63
topic_type:
- apiref
ms.openlocfilehash: d00a5f71ac7e47d78deebca0e46350e465964c72
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210092"
---
# <a name="icordebugprocessenumnext-method"></a><span data-ttu-id="38442-102">Método ICorDebugProcessEnum::Next</span><span class="sxs-lookup"><span data-stu-id="38442-102">ICorDebugProcessEnum::Next Method</span></span>
<span data-ttu-id="38442-103">Obtém o número especificado de instâncias de ICorDebugProcess da enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="38442-103">Gets the specified number of ICorDebugProcess instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38442-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="38442-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugProcess *processes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38442-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="38442-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="38442-106">no O número de `ICorDebugProcess` instâncias a serem recuperadas.</span><span class="sxs-lookup"><span data-stu-id="38442-106">[in] The number of `ICorDebugProcess` instances to be retrieved.</span></span>  
  
 `processes`  
 <span data-ttu-id="38442-107">fora Uma matriz de ponteiros, cada um dos quais aponta para um `ICorDebugProcess` objeto que representa um processo.</span><span class="sxs-lookup"><span data-stu-id="38442-107">[out] An array of pointers, each of which points to an `ICorDebugProcess` object that represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="38442-108">fora Aponta para o número de `ICorDebugProcess` instâncias realmente retornadas.</span><span class="sxs-lookup"><span data-stu-id="38442-108">[out] Pointer to the number of `ICorDebugProcess` instances actually returned.</span></span> <span data-ttu-id="38442-109">Esse valor pode ser nulo se `celt` for um.</span><span class="sxs-lookup"><span data-stu-id="38442-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38442-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="38442-110">Requirements</span></span>  
 <span data-ttu-id="38442-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38442-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38442-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="38442-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38442-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38442-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38442-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38442-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
