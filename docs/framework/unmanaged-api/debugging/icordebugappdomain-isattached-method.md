---
title: Método ICorDebugAppDomain::IsAttached
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.IsAttached
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::IsAttached
helpviewer_keywords:
- IsAttached method [.NET Framework debugging]
- ICorDebugAppDomain::IsAttached method [.NET Framework debugging]
ms.assetid: af0c67c7-f53e-47c9-b84b-be50bd04903e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f0412089fee27e556c2f9230e9b34de3391b9bd4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugappdomainisattached-method"></a><span data-ttu-id="bcf97-102">Método ICorDebugAppDomain::IsAttached</span><span class="sxs-lookup"><span data-stu-id="bcf97-102">ICorDebugAppDomain::IsAttached Method</span></span>
<span data-ttu-id="bcf97-103">Obtém um valor que indica se o depurador é anexado ao domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bcf97-103">Gets a value that indicates whether the debugger is attached to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcf97-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bcf97-104">Syntax</span></span>  
  
```  
HRESULT IsAttached (  
    [out] BOOL  *pbAttached  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bcf97-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bcf97-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="bcf97-106">[out] `true` se o depurador é anexado ao domínio do aplicativo; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="bcf97-106">[out] `true` if the debugger is attached to the application domain; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bcf97-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="bcf97-107">Remarks</span></span>  
 <span data-ttu-id="bcf97-108">Os métodos de ICorDebugController não podem ser usados até que o depurador se anexa ao domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bcf97-108">The ICorDebugController methods cannot be used until the debugger attaches to the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcf97-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bcf97-109">Requirements</span></span>  
 <span data-ttu-id="bcf97-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bcf97-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcf97-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bcf97-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bcf97-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bcf97-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bcf97-113">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcf97-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
