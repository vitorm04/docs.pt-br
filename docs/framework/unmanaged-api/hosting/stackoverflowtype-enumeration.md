---
title: Enumeração StackOverflowType
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 06c9119a2b842a0efcd4af752ba72dbfda03bf13
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54653848"
---
# <a name="stackoverflowtype-enumeration"></a><span data-ttu-id="57ff6-102">Enumeração StackOverflowType</span><span class="sxs-lookup"><span data-stu-id="57ff6-102">StackOverflowType Enumeration</span></span>
<span data-ttu-id="57ff6-103">Contém valores que indicam a causa subjacente de um evento de estouro de pilha.</span><span class="sxs-lookup"><span data-stu-id="57ff6-103">Contains values that indicate the underlying cause of a stack overflow event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57ff6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="57ff6-104">Syntax</span></span>  
  
```  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a><span data-ttu-id="57ff6-105">Membros</span><span class="sxs-lookup"><span data-stu-id="57ff6-105">Members</span></span>  
  
|<span data-ttu-id="57ff6-106">Membro</span><span class="sxs-lookup"><span data-stu-id="57ff6-106">Member</span></span>|<span data-ttu-id="57ff6-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="57ff6-107">Description</span></span>|  
|------------|-----------------|  
|`SO_ClrEngine`|<span data-ttu-id="57ff6-108">O estouro da pilha foi causado pelo mecanismo de execução.</span><span class="sxs-lookup"><span data-stu-id="57ff6-108">The stack overflow was caused by the execution engine.</span></span>|  
|`SO_Managed`|<span data-ttu-id="57ff6-109">O estouro da pilha foi causado pelo código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="57ff6-109">The stack overflow was caused by managed code.</span></span>|  
|`SO_Other`|<span data-ttu-id="57ff6-110">O estouro da pilha foi causado pelo código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="57ff6-110">The stack overflow was caused by unmanaged code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57ff6-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="57ff6-111">Remarks</span></span>  
 <span data-ttu-id="57ff6-112">Essas informações são passadas para o host por meio de uma chamada para o [iactiononclrevent:: ONEVENT](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="57ff6-112">This information is passed to the host through a call to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57ff6-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="57ff6-113">Requirements</span></span>  
 <span data-ttu-id="57ff6-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57ff6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57ff6-115">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="57ff6-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="57ff6-116">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="57ff6-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="57ff6-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57ff6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57ff6-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="57ff6-118">See also</span></span>
- [<span data-ttu-id="57ff6-119">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="57ff6-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
