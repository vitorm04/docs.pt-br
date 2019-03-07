---
title: Método ICorDebugAssembly::GetAppDomain
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetAppDomain
helpviewer_keywords:
- ICorDebugAssembly::GetAppDomain method [.NET Framework debugging]
- GetAppDomain method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 14e18510-23ac-4cba-9f96-c86147a2df9d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9ba09b80d7118b0ccd9b1647011a7fc7cd74e22
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485103"
---
# <a name="icordebugassemblygetappdomain-method"></a><span data-ttu-id="16a0f-102">Método ICorDebugAssembly::GetAppDomain</span><span class="sxs-lookup"><span data-stu-id="16a0f-102">ICorDebugAssembly::GetAppDomain Method</span></span>
<span data-ttu-id="16a0f-103">Obtém um ponteiro de interface para o domínio do aplicativo que contém este `ICorDebugAssembly` instância.</span><span class="sxs-lookup"><span data-stu-id="16a0f-103">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16a0f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="16a0f-104">Syntax</span></span>  
  
```  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16a0f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="16a0f-105">Parameters</span></span>  
 `ppAppDomain`  
 <span data-ttu-id="16a0f-106">[out] Um ponteiro para o endereço de uma interface ICorDebugAppDomain que representa o domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="16a0f-106">[out] A pointer to the address of an ICorDebugAppDomain interface that represents the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16a0f-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="16a0f-107">Remarks</span></span>  
 <span data-ttu-id="16a0f-108">Se esse assembly é o assembly do sistema, `GetAppDomain` retorna null.</span><span class="sxs-lookup"><span data-stu-id="16a0f-108">If this assembly is the system assembly, `GetAppDomain` returns null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16a0f-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="16a0f-109">Requirements</span></span>  
 <span data-ttu-id="16a0f-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16a0f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16a0f-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="16a0f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16a0f-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16a0f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16a0f-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16a0f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
