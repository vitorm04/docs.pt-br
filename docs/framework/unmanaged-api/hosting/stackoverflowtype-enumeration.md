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
ms.openlocfilehash: 9e888b2359336c68ea6fdf52f798145fda12002e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440863"
---
# <a name="stackoverflowtype-enumeration"></a><span data-ttu-id="a78ea-102">Enumeração StackOverflowType</span><span class="sxs-lookup"><span data-stu-id="a78ea-102">StackOverflowType Enumeration</span></span>
<span data-ttu-id="a78ea-103">Contém valores que indicam a causa subjacente de um evento de estouro de pilha.</span><span class="sxs-lookup"><span data-stu-id="a78ea-103">Contains values that indicate the underlying cause of a stack overflow event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a78ea-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a78ea-104">Syntax</span></span>  
  
```  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a><span data-ttu-id="a78ea-105">Membros</span><span class="sxs-lookup"><span data-stu-id="a78ea-105">Members</span></span>  
  
|<span data-ttu-id="a78ea-106">Membro</span><span class="sxs-lookup"><span data-stu-id="a78ea-106">Member</span></span>|<span data-ttu-id="a78ea-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a78ea-107">Description</span></span>|  
|------------|-----------------|  
|`SO_ClrEngine`|<span data-ttu-id="a78ea-108">O estouro da pilha foi causado pelo mecanismo de execução.</span><span class="sxs-lookup"><span data-stu-id="a78ea-108">The stack overflow was caused by the execution engine.</span></span>|  
|`SO_Managed`|<span data-ttu-id="a78ea-109">O estouro da pilha foi causado pelo código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a78ea-109">The stack overflow was caused by managed code.</span></span>|  
|`SO_Other`|<span data-ttu-id="a78ea-110">O estouro da pilha foi causado pelo código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a78ea-110">The stack overflow was caused by unmanaged code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a78ea-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="a78ea-111">Remarks</span></span>  
 <span data-ttu-id="a78ea-112">Essas informações são passadas para o host por meio de uma chamada para o [Iactiononclrevent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="a78ea-112">This information is passed to the host through a call to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a78ea-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a78ea-113">Requirements</span></span>  
 <span data-ttu-id="a78ea-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a78ea-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a78ea-115">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a78ea-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a78ea-116">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a78ea-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a78ea-117">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a78ea-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a78ea-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a78ea-118">See Also</span></span>  
 [<span data-ttu-id="a78ea-119">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="a78ea-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
