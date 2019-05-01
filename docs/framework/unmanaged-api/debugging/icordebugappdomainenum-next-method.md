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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5fefc933cc84fede1f3dea16d4b13e09801a96e0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61996145"
---
# <a name="icordebugappdomainenumnext-method"></a><span data-ttu-id="2336f-102">Método ICorDebugAppDomainEnum::Next</span><span class="sxs-lookup"><span data-stu-id="2336f-102">ICorDebugAppDomainEnum::Next Method</span></span>
<span data-ttu-id="2336f-103">Obtém o número de domínios de aplicativo especificado da coleção, começando na posição atual do cursor.</span><span class="sxs-lookup"><span data-stu-id="2336f-103">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2336f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2336f-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                           ICorDebugAppDomain *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2336f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2336f-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="2336f-106">[in] O número de domínios de aplicativo a ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="2336f-106">[in] The number of application domains to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="2336f-107">[out] Uma matriz de ponteiros, cada um deles aponta para um objeto de ICorDebugAppDomain que representa um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2336f-107">[out] An array of pointers, each of which points to an ICorDebugAppDomain object that represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="2336f-108">[out] Um ponteiro para o número de domínios de aplicativo, na verdade, é retornado.</span><span class="sxs-lookup"><span data-stu-id="2336f-108">[out] A pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="2336f-109">Esse valor pode ser nulo se `celt` é um.</span><span class="sxs-lookup"><span data-stu-id="2336f-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2336f-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2336f-110">Requirements</span></span>  
 <span data-ttu-id="2336f-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2336f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2336f-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2336f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2336f-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2336f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2336f-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2336f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
