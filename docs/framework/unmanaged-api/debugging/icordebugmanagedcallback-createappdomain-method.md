---
title: "Método ICorDebugManagedCallback::CreateAppDomain"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.CreateAppDomain
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::CreateAppDomain
helpviewer_keywords:
- CreateAppDomain method [.NET Framework debugging]
- ICorDebugManagedCallback::CreateAppDomain method [.NET Framework debugging]
ms.assetid: 48d410d7-6749-4125-a8fd-f9562c7088e9
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6d2cb90f780d4d680e6c81ebd9579341d5a3b1fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackcreateappdomain-method"></a><span data-ttu-id="177c8-102">Método ICorDebugManagedCallback::CreateAppDomain</span><span class="sxs-lookup"><span data-stu-id="177c8-102">ICorDebugManagedCallback::CreateAppDomain Method</span></span>
<span data-ttu-id="177c8-103">Notifica o depurador um domínio de aplicativo foi criado.</span><span class="sxs-lookup"><span data-stu-id="177c8-103">Notifies the debugger that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="177c8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="177c8-104">Syntax</span></span>  
  
```  
HRESULT CreateAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="177c8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="177c8-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="177c8-106">[in] Um ponteiro para um objeto ICorDebugProcess que representa o processo no qual o domínio de aplicativo foi criado.</span><span class="sxs-lookup"><span data-stu-id="177c8-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the application domain was created.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="177c8-107">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo que foi criado.</span><span class="sxs-lookup"><span data-stu-id="177c8-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has been created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="177c8-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="177c8-108">Requirements</span></span>  
 <span data-ttu-id="177c8-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="177c8-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="177c8-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="177c8-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="177c8-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="177c8-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="177c8-112">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="177c8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="177c8-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="177c8-113">See Also</span></span>  
 [<span data-ttu-id="177c8-114">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="177c8-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
