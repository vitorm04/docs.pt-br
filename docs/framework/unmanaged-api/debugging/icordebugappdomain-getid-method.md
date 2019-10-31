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
ms.openlocfilehash: 87c43d6f05dffbf10ca1dd9253abfe893db9adf5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73110476"
---
# <a name="icordebugappdomaingetid-method"></a><span data-ttu-id="e32a6-102">Método ICorDebugAppDomain::GetId</span><span class="sxs-lookup"><span data-stu-id="e32a6-102">ICorDebugAppDomain::GetId Method</span></span>
<span data-ttu-id="e32a6-103">Obtém o identificador exclusivo do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e32a6-103">Gets the unique identifier of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e32a6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e32a6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] ULONG32   *pId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e32a6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e32a6-105">Parameters</span></span>  
 `pId`  
 <span data-ttu-id="e32a6-106">fora O identificador exclusivo do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e32a6-106">[out] The unique identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e32a6-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="e32a6-107">Remarks</span></span>  
 <span data-ttu-id="e32a6-108">O identificador para o domínio do aplicativo é exclusivo dentro do processo que o contém.</span><span class="sxs-lookup"><span data-stu-id="e32a6-108">The identifier for the application domain is unique within the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e32a6-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e32a6-109">Requirements</span></span>  
 <span data-ttu-id="e32a6-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e32a6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e32a6-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e32a6-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e32a6-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e32a6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e32a6-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e32a6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
