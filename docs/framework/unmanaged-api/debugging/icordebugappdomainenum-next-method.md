---
title: Método ICorDebugAppDomainEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomainEnum::Next method
helpviewer_keywords:
- ICorDebugAppDomainEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugAppDomainEnum interface [.NET Framework debugging]
ms.assetid: b8d1def7-0ebc-4314-a3a2-fd36a75973e7
topic_type:
- apiref
ms.openlocfilehash: 55e331ff4e6ada73dc92bb2e880f555887639714
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088785"
---
# <a name="icordebugappdomainenumnext-method"></a><span data-ttu-id="1965a-102">Método ICorDebugAppDomainEnum::Next</span><span class="sxs-lookup"><span data-stu-id="1965a-102">ICorDebugAppDomainEnum::Next Method</span></span>
<span data-ttu-id="1965a-103">Obtém o número especificado de domínios de aplicativo da coleção, começando na posição atual do cursor.</span><span class="sxs-lookup"><span data-stu-id="1965a-103">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1965a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1965a-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                           ICorDebugAppDomain *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1965a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1965a-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="1965a-106">no O número de domínios de aplicativo a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="1965a-106">[in] The number of application domains to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="1965a-107">fora Uma matriz de ponteiros, cada um dos quais aponta para um objeto ICorDebugAppDomain que representa um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1965a-107">[out] An array of pointers, each of which points to an ICorDebugAppDomain object that represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="1965a-108">fora Um ponteiro para o número de domínios de aplicativo realmente retornados.</span><span class="sxs-lookup"><span data-stu-id="1965a-108">[out] A pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="1965a-109">Esse valor pode ser nulo se `celt` for um.</span><span class="sxs-lookup"><span data-stu-id="1965a-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1965a-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1965a-110">Requirements</span></span>  
 <span data-ttu-id="1965a-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1965a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1965a-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1965a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1965a-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1965a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1965a-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1965a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
