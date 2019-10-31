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
ms.openlocfilehash: f09c6bb79d7bd28f4d8b74237b6f343a07b79062
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141475"
---
# <a name="stackoverflowtype-enumeration"></a><span data-ttu-id="5d588-102">Enumeração StackOverflowType</span><span class="sxs-lookup"><span data-stu-id="5d588-102">StackOverflowType Enumeration</span></span>
<span data-ttu-id="5d588-103">Contém valores que indicam a causa subjacente de um evento de estouro de pilha.</span><span class="sxs-lookup"><span data-stu-id="5d588-103">Contains values that indicate the underlying cause of a stack overflow event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d588-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5d588-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a><span data-ttu-id="5d588-105">Membros</span><span class="sxs-lookup"><span data-stu-id="5d588-105">Members</span></span>  
  
|<span data-ttu-id="5d588-106">Membro</span><span class="sxs-lookup"><span data-stu-id="5d588-106">Member</span></span>|<span data-ttu-id="5d588-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5d588-107">Description</span></span>|  
|------------|-----------------|  
|`SO_ClrEngine`|<span data-ttu-id="5d588-108">O estouro de pilha foi causado pelo mecanismo de execução.</span><span class="sxs-lookup"><span data-stu-id="5d588-108">The stack overflow was caused by the execution engine.</span></span>|  
|`SO_Managed`|<span data-ttu-id="5d588-109">O estouro de pilha foi causado por código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5d588-109">The stack overflow was caused by managed code.</span></span>|  
|`SO_Other`|<span data-ttu-id="5d588-110">O estouro de pilha foi causado por código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5d588-110">The stack overflow was caused by unmanaged code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d588-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="5d588-111">Remarks</span></span>  
 <span data-ttu-id="5d588-112">Essas informações são passadas para o host por meio de uma chamada para o método [IActionOnCLREvent:: OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5d588-112">This information is passed to the host through a call to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d588-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5d588-113">Requirements</span></span>  
 <span data-ttu-id="5d588-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d588-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d588-115">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5d588-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5d588-116">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5d588-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5d588-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d588-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d588-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d588-118">See also</span></span>

- [<span data-ttu-id="5d588-119">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="5d588-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
