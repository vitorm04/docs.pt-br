---
title: Método ICorDebugFrameEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugFrameEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrameEnum::Next
helpviewer_keywords:
- ICorDebugFrameEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugFrameEnum interface [.NET Framework debugging]
ms.assetid: 0bc96acb-6179-4328-a447-cda562ce9e98
topic_type:
- apiref
ms.openlocfilehash: 4652e4b34d614ad3b7b852925fcc63309bdd1498
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209455"
---
# <a name="icordebugframeenumnext-method"></a><span data-ttu-id="08142-102">Método ICorDebugFrameEnum::Next</span><span class="sxs-lookup"><span data-stu-id="08142-102">ICorDebugFrameEnum::Next Method</span></span>
<span data-ttu-id="08142-103">Obtém o número especificado de instâncias de ICorDebugFrame, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="08142-103">Gets the specified number of ICorDebugFrame instances, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08142-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="08142-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugFrame *frames[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08142-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="08142-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="08142-106">no O número de `ICorDebugFrame` instâncias a serem recuperadas.</span><span class="sxs-lookup"><span data-stu-id="08142-106">[in] The number of `ICorDebugFrame` instances to be retrieved.</span></span>  
  
 `frames`  
 <span data-ttu-id="08142-107">fora Uma matriz de ponteiros, cada um dos quais aponta para um `ICorDebugFrame` objeto.</span><span class="sxs-lookup"><span data-stu-id="08142-107">[out] An array of pointers, each of which points to an `ICorDebugFrame` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="08142-108">fora Um ponteiro para o número de `ICorDebugFrame` instâncias retornadas de fato.</span><span class="sxs-lookup"><span data-stu-id="08142-108">[out] A pointer to the number of `ICorDebugFrame` instances actually returned.</span></span> <span data-ttu-id="08142-109">Esse valor pode ser nulo se `celt` for um.</span><span class="sxs-lookup"><span data-stu-id="08142-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08142-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="08142-110">Requirements</span></span>  
 <span data-ttu-id="08142-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08142-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08142-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="08142-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="08142-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="08142-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08142-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08142-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
