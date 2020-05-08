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
ms.openlocfilehash: 17bf4c92b1e1347a8fe790c8df5937de0f95df4d
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895079"
---
# <a name="icordebugappdomainenumnext-method"></a><span data-ttu-id="3f3e7-102">Método ICorDebugAppDomainEnum::Next</span><span class="sxs-lookup"><span data-stu-id="3f3e7-102">ICorDebugAppDomainEnum::Next Method</span></span>
<span data-ttu-id="3f3e7-103">Obtém o número especificado de domínios de aplicativo da coleção, começando na posição atual do cursor.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-103">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f3e7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3f3e7-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                           ICorDebugAppDomain *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f3e7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3f3e7-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="3f3e7-106">no O número de domínios de aplicativo a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-106">[in] The number of application domains to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="3f3e7-107">fora Uma matriz de ponteiros, cada um dos quais aponta para um objeto ICorDebugAppDomain que representa um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-107">[out] An array of pointers, each of which points to an ICorDebugAppDomain object that represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="3f3e7-108">fora Um ponteiro para o número de domínios de aplicativo realmente retornados.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-108">[out] A pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="3f3e7-109">Esse valor pode ser nulo se `celt` for um.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f3e7-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3f3e7-110">Requirements</span></span>  
 <span data-ttu-id="3f3e7-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f3e7-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f3e7-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3f3e7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3f3e7-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3f3e7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f3e7-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f3e7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
