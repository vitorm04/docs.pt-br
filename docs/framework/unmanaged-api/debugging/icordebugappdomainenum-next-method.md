---
title: "Método ICorDebugAppDomainEnum::Next"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomainEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomainEnum::Next method
helpviewer_keywords:
- ICorDebugAppDomainEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugAppDomainEnum interface [.NET Framework debugging]
ms.assetid: b8d1def7-0ebc-4314-a3a2-fd36a75973e7
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 10d53ebac99942ac9376041f217df53965bdbb2f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomainenumnext-method"></a><span data-ttu-id="daf28-102">Método ICorDebugAppDomainEnum::Next</span><span class="sxs-lookup"><span data-stu-id="daf28-102">ICorDebugAppDomainEnum::Next Method</span></span>
<span data-ttu-id="daf28-103">Obtém o número de domínios de aplicativo especificado da coleção, começando na posição atual do cursor.</span><span class="sxs-lookup"><span data-stu-id="daf28-103">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="daf28-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="daf28-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                           ICorDebugAppDomain *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="daf28-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="daf28-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="daf28-106">[in] O número de domínios de aplicativo a ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="daf28-106">[in] The number of application domains to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="daf28-107">[out] Uma matriz de ponteiros, cada um deles aponta para um objeto ICorDebugAppDomain que representa um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="daf28-107">[out] An array of pointers, each of which points to an ICorDebugAppDomain object that represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="daf28-108">[out] Um ponteiro para o número de domínios de aplicativo, na verdade, retornadas.</span><span class="sxs-lookup"><span data-stu-id="daf28-108">[out] A pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="daf28-109">Esse valor pode ser null se `celt` é um.</span><span class="sxs-lookup"><span data-stu-id="daf28-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="daf28-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="daf28-110">Requirements</span></span>  
 <span data-ttu-id="daf28-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="daf28-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="daf28-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="daf28-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="daf28-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="daf28-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="daf28-114">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="daf28-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
