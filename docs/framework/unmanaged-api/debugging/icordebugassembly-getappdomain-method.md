---
title: "Método ICorDebugAssembly::GetAppDomain"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAssembly.GetAppDomain
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAssembly::GetAppDomain
helpviewer_keywords:
- ICorDebugAssembly::GetAppDomain method [.NET Framework debugging]
- GetAppDomain method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 14e18510-23ac-4cba-9f96-c86147a2df9d
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f97795568b9811d0dbf7852fd64d5256c29b8f30
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugassemblygetappdomain-method"></a><span data-ttu-id="c4378-102">Método ICorDebugAssembly::GetAppDomain</span><span class="sxs-lookup"><span data-stu-id="c4378-102">ICorDebugAssembly::GetAppDomain Method</span></span>
<span data-ttu-id="c4378-103">Obtém um ponteiro de interface para o domínio de aplicativo que contém essa `ICorDebugAssembly` instância.</span><span class="sxs-lookup"><span data-stu-id="c4378-103">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4378-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c4378-104">Syntax</span></span>  
  
```  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c4378-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c4378-105">Parameters</span></span>  
 `ppAppDomain`  
 <span data-ttu-id="c4378-106">[out] Um ponteiro para o endereço de uma interface ICorDebugAppDomain que representa o domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c4378-106">[out] A pointer to the address of an ICorDebugAppDomain interface that represents the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4378-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="c4378-107">Remarks</span></span>  
 <span data-ttu-id="c4378-108">Se esse assembly é o assembly do sistema, `GetAppDomain` retorna nulo.</span><span class="sxs-lookup"><span data-stu-id="c4378-108">If this assembly is the system assembly, `GetAppDomain` returns null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4378-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c4378-109">Requirements</span></span>  
 <span data-ttu-id="c4378-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4378-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4378-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c4378-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4378-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4378-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4378-113">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4378-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
