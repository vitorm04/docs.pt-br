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
ms.openlocfilehash: fb8917fa401db9424cff168fe0b06ad84065827c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737942"
---
# <a name="icordebugappdomaingetid-method"></a><span data-ttu-id="f6429-102">Método ICorDebugAppDomain::GetId</span><span class="sxs-lookup"><span data-stu-id="f6429-102">ICorDebugAppDomain::GetId Method</span></span>
<span data-ttu-id="f6429-103">Obtém o identificador exclusivo do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f6429-103">Gets the unique identifier of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6429-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f6429-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] ULONG32   *pId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6429-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f6429-105">Parameters</span></span>  
 `pId`  
 <span data-ttu-id="f6429-106">[out] O identificador exclusivo do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f6429-106">[out] The unique identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6429-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="f6429-107">Remarks</span></span>  
 <span data-ttu-id="f6429-108">O identificador para o domínio de aplicativo é exclusivo dentro do processo de recipiente.</span><span class="sxs-lookup"><span data-stu-id="f6429-108">The identifier for the application domain is unique within the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6429-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f6429-109">Requirements</span></span>  
 <span data-ttu-id="f6429-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6429-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6429-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f6429-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f6429-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f6429-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6429-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6429-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
