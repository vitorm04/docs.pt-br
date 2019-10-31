---
title: Método ICorDebugObjectEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugObjectEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugObjectEnum interface [.NET Framework debugging]
- ICorDebugObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 10093e3d-26b6-4ad7-8ef3-bbf66243fc02
topic_type:
- apiref
ms.openlocfilehash: adcfbf1207ad7895ab55f7e5cf9581905cb826bf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096101"
---
# <a name="icordebugobjectenumnext-method"></a><span data-ttu-id="4b136-102">Método ICorDebugObjectEnum::Next</span><span class="sxs-lookup"><span data-stu-id="4b136-102">ICorDebugObjectEnum::Next Method</span></span>
<span data-ttu-id="4b136-103">Obtém os endereços virtuais relativos (RVAs) do número especificado de objetos da enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="4b136-103">Gets the relative virtual addresses (RVAs) of the specified number of objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b136-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4b136-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]    
        CORDB_ADDRESS objects[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b136-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4b136-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="4b136-106">no O número de objetos a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="4b136-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="4b136-107">fora Uma matriz de ponteiros, cada um dos quais aponta para um objeto CORDB_ADDRESS.</span><span class="sxs-lookup"><span data-stu-id="4b136-107">[out] An array of pointers, each of which points to a CORDB_ADDRESS object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="4b136-108">fora Aponta para o número de objetos realmente retornados.</span><span class="sxs-lookup"><span data-stu-id="4b136-108">[out] Pointer to the number of objects actually returned.</span></span> <span data-ttu-id="4b136-109">Esse valor pode ser nulo se `celt` for um.</span><span class="sxs-lookup"><span data-stu-id="4b136-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b136-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4b136-110">Requirements</span></span>  
 <span data-ttu-id="4b136-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b136-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b136-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4b136-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4b136-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b136-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b136-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b136-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b136-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4b136-115">See also</span></span>
