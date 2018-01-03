---
title: "Método ICorDebugAppDomain::IsAttached"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.IsAttached
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain::IsAttached
helpviewer_keywords:
- IsAttached method [.NET Framework debugging]
- ICorDebugAppDomain::IsAttached method [.NET Framework debugging]
ms.assetid: af0c67c7-f53e-47c9-b84b-be50bd04903e
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a1af550de7198041a885a788d6b36349c8e1c091
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomainisattached-method"></a><span data-ttu-id="f88f6-102">Método ICorDebugAppDomain::IsAttached</span><span class="sxs-lookup"><span data-stu-id="f88f6-102">ICorDebugAppDomain::IsAttached Method</span></span>
<span data-ttu-id="f88f6-103">Obtém um valor que indica se o depurador é anexado ao domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f88f6-103">Gets a value that indicates whether the debugger is attached to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f88f6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f88f6-104">Syntax</span></span>  
  
```  
HRESULT IsAttached (  
    [out] BOOL  *pbAttached  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f88f6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f88f6-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="f88f6-106">[out] `true` se o depurador é anexado ao domínio do aplicativo; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="f88f6-106">[out] `true` if the debugger is attached to the application domain; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f88f6-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="f88f6-107">Remarks</span></span>  
 <span data-ttu-id="f88f6-108">Os métodos de ICorDebugController não podem ser usados até que o depurador se anexa ao domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f88f6-108">The ICorDebugController methods cannot be used until the debugger attaches to the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f88f6-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f88f6-109">Requirements</span></span>  
 <span data-ttu-id="f88f6-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f88f6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f88f6-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f88f6-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f88f6-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f88f6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f88f6-113">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f88f6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
