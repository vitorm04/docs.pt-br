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
ms.openlocfilehash: a2f6df7647ffe9f2adff963b6629ed29ece053c0
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895156"
---
# <a name="icordebugappdomainisattached-method"></a><span data-ttu-id="b4da8-102">Método ICorDebugAppDomain::IsAttached</span><span class="sxs-lookup"><span data-stu-id="b4da8-102">ICorDebugAppDomain::IsAttached Method</span></span>
<span data-ttu-id="b4da8-103">Obtém um valor que indica se o depurador está anexado ao domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b4da8-103">Gets a value that indicates whether the debugger is attached to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4da8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b4da8-104">Syntax</span></span>  
  
```cpp  
HRESULT IsAttached (  
    [out] BOOL  *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4da8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b4da8-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="b4da8-106">fora `true` se o depurador estiver anexado ao domínio do aplicativo; caso contrário `false`,.</span><span class="sxs-lookup"><span data-stu-id="b4da8-106">[out] `true` if the debugger is attached to the application domain; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4da8-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="b4da8-107">Remarks</span></span>  
 <span data-ttu-id="b4da8-108">Os métodos ICorDebugController não podem ser usados até que o depurador seja anexado ao domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b4da8-108">The ICorDebugController methods cannot be used until the debugger attaches to the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4da8-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b4da8-109">Requirements</span></span>  
 <span data-ttu-id="b4da8-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4da8-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4da8-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b4da8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4da8-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4da8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4da8-113">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4da8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
