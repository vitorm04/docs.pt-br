---
title: "Método ICorDebugAppDomain::GetId"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.GetId
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain::GetId
helpviewer_keywords:
- GetId method, ICorDebugAppDomain interface [.NET Framework debugging]
- ICorDebugAppDomain::GetId method [.NET Framework debugging]
ms.assetid: 32c27576-71fa-42ee-8230-67b92913ea08
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8b151d5b0774576e98da5845e5c7afc24ada0001
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomaingetid-method"></a><span data-ttu-id="73d15-102">Método ICorDebugAppDomain::GetId</span><span class="sxs-lookup"><span data-stu-id="73d15-102">ICorDebugAppDomain::GetId Method</span></span>
<span data-ttu-id="73d15-103">Obtém o identificador exclusivo do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="73d15-103">Gets the unique identifier of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73d15-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="73d15-104">Syntax</span></span>  
  
```  
HRESULT GetID (  
    [out] ULONG32   *pId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="73d15-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="73d15-105">Parameters</span></span>  
 `pId`  
 <span data-ttu-id="73d15-106">[out] O identificador exclusivo do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="73d15-106">[out] The unique identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73d15-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="73d15-107">Remarks</span></span>  
 <span data-ttu-id="73d15-108">O identificador para o domínio de aplicativo é exclusivo dentro do processo que contém.</span><span class="sxs-lookup"><span data-stu-id="73d15-108">The identifier for the application domain is unique within the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73d15-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="73d15-109">Requirements</span></span>  
 <span data-ttu-id="73d15-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73d15-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73d15-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="73d15-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73d15-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73d15-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73d15-113">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73d15-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
