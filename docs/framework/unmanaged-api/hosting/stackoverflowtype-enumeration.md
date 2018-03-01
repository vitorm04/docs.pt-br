---
title: "Enumeração StackOverflowType"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- StackOverflowType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowType
helpviewer_keywords:
- StackOverflowType enumeration [.NET Framework hosting]
ms.assetid: dab648ad-972b-479c-b129-b4c1dcbd932e
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a04db61a16aeae24476fb0b191a3d2dc89743dee
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="stackoverflowtype-enumeration"></a><span data-ttu-id="543a4-102">Enumeração StackOverflowType</span><span class="sxs-lookup"><span data-stu-id="543a4-102">StackOverflowType Enumeration</span></span>
<span data-ttu-id="543a4-103">Contém valores que indicam a causa subjacente de um evento de estouro de pilha.</span><span class="sxs-lookup"><span data-stu-id="543a4-103">Contains values that indicate the underlying cause of a stack overflow event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="543a4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="543a4-104">Syntax</span></span>  
  
```  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a><span data-ttu-id="543a4-105">Membros</span><span class="sxs-lookup"><span data-stu-id="543a4-105">Members</span></span>  
  
|<span data-ttu-id="543a4-106">Membro</span><span class="sxs-lookup"><span data-stu-id="543a4-106">Member</span></span>|<span data-ttu-id="543a4-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="543a4-107">Description</span></span>|  
|------------|-----------------|  
|`SO_ClrEngine`|<span data-ttu-id="543a4-108">O estouro da pilha foi causado pelo mecanismo de execução.</span><span class="sxs-lookup"><span data-stu-id="543a4-108">The stack overflow was caused by the execution engine.</span></span>|  
|`SO_Managed`|<span data-ttu-id="543a4-109">O estouro da pilha foi causado pelo código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="543a4-109">The stack overflow was caused by managed code.</span></span>|  
|`SO_Other`|<span data-ttu-id="543a4-110">O estouro da pilha foi causado pelo código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="543a4-110">The stack overflow was caused by unmanaged code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="543a4-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="543a4-111">Remarks</span></span>  
 <span data-ttu-id="543a4-112">Essas informações são passadas para o host por meio de uma chamada para o [Iactiononclrevent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="543a4-112">This information is passed to the host through a call to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="543a4-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="543a4-113">Requirements</span></span>  
 <span data-ttu-id="543a4-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="543a4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="543a4-115">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="543a4-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="543a4-116">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="543a4-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="543a4-117">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="543a4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="543a4-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="543a4-118">See Also</span></span>  
 [<span data-ttu-id="543a4-119">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="543a4-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
