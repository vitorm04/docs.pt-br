---
title: Método ICorDebugAppDomain::GetId
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetId
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetId
helpviewer_keywords:
- GetId method, ICorDebugAppDomain interface [.NET Framework debugging]
- ICorDebugAppDomain::GetId method [.NET Framework debugging]
ms.assetid: 32c27576-71fa-42ee-8230-67b92913ea08
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0aefc19ca0c255c9c8ea40fcc12fc5cba1b00f6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61996249"
---
# <a name="icordebugappdomaingetid-method"></a><span data-ttu-id="3352f-102">Método ICorDebugAppDomain::GetId</span><span class="sxs-lookup"><span data-stu-id="3352f-102">ICorDebugAppDomain::GetId Method</span></span>
<span data-ttu-id="3352f-103">Obtém o identificador exclusivo do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3352f-103">Gets the unique identifier of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3352f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3352f-104">Syntax</span></span>  
  
```  
HRESULT GetID (  
    [out] ULONG32   *pId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3352f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3352f-105">Parameters</span></span>  
 `pId`  
 <span data-ttu-id="3352f-106">[out] O identificador exclusivo do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3352f-106">[out] The unique identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3352f-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="3352f-107">Remarks</span></span>  
 <span data-ttu-id="3352f-108">O identificador para o domínio de aplicativo é exclusivo dentro do processo de recipiente.</span><span class="sxs-lookup"><span data-stu-id="3352f-108">The identifier for the application domain is unique within the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3352f-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3352f-109">Requirements</span></span>  
 <span data-ttu-id="3352f-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3352f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3352f-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3352f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3352f-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3352f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3352f-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3352f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
