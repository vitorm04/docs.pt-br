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
ms.openlocfilehash: 8541ea7b614ff4a6ca666f0e2549a7f50e190192
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135870"
---
# <a name="stackoverflowtype-enumeration"></a><span data-ttu-id="22f1e-102">Enumeração StackOverflowType</span><span class="sxs-lookup"><span data-stu-id="22f1e-102">StackOverflowType Enumeration</span></span>
<span data-ttu-id="22f1e-103">Contém valores que indicam a causa subjacente de um evento de estouro de pilha.</span><span class="sxs-lookup"><span data-stu-id="22f1e-103">Contains values that indicate the underlying cause of a stack overflow event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22f1e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="22f1e-104">Syntax</span></span>  
  
```  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a><span data-ttu-id="22f1e-105">Membros</span><span class="sxs-lookup"><span data-stu-id="22f1e-105">Members</span></span>  
  
|<span data-ttu-id="22f1e-106">Membro</span><span class="sxs-lookup"><span data-stu-id="22f1e-106">Member</span></span>|<span data-ttu-id="22f1e-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="22f1e-107">Description</span></span>|  
|------------|-----------------|  
|`SO_ClrEngine`|<span data-ttu-id="22f1e-108">O estouro da pilha foi causado pelo mecanismo de execução.</span><span class="sxs-lookup"><span data-stu-id="22f1e-108">The stack overflow was caused by the execution engine.</span></span>|  
|`SO_Managed`|<span data-ttu-id="22f1e-109">O estouro da pilha foi causado pelo código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="22f1e-109">The stack overflow was caused by managed code.</span></span>|  
|`SO_Other`|<span data-ttu-id="22f1e-110">O estouro da pilha foi causado pelo código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="22f1e-110">The stack overflow was caused by unmanaged code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22f1e-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="22f1e-111">Remarks</span></span>  
 <span data-ttu-id="22f1e-112">Essas informações são passadas para o host por meio de uma chamada para o [iactiononclrevent:: ONEVENT](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="22f1e-112">This information is passed to the host through a call to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22f1e-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="22f1e-113">Requirements</span></span>  
 <span data-ttu-id="22f1e-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22f1e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22f1e-115">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="22f1e-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="22f1e-116">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="22f1e-116">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="22f1e-117">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="22f1e-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="22f1e-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="22f1e-118">See also</span></span>

- [<span data-ttu-id="22f1e-119">Hospedando enumerações</span><span class="sxs-lookup"><span data-stu-id="22f1e-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
