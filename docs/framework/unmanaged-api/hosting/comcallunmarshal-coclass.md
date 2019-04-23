---
title: Coclass ComCallUnmarshal
ms.date: 03/30/2017
api_name:
- ComCallUnmarshal Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ComCallUnmarshal
helpviewer_keywords:
- ComCallUnmarshal coclass [.NET Framework hosting]
ms.assetid: 2adb5827-2268-4914-a1c6-f62b61880a45
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2f17a88a90905006432ae8c5dc040277124c947b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59166875"
---
# <a name="comcallunmarshal-coclass"></a><span data-ttu-id="6c6b0-102">Coclass ComCallUnmarshal</span><span class="sxs-lookup"><span data-stu-id="6c6b0-102">ComCallUnmarshal Coclass</span></span>
<span data-ttu-id="6c6b0-103">Fornece interfaces para gerenciar o marshaling de ponteiros de interface.</span><span class="sxs-lookup"><span data-stu-id="6c6b0-103">Provides interfaces for managing the marshaling of interface pointers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c6b0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6c6b0-104">Syntax</span></span>  
  
```  
coclass ComCallUnmarshal {  
    [default] interface IMarshal;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="6c6b0-105">Interfaces</span><span class="sxs-lookup"><span data-stu-id="6c6b0-105">Interfaces</span></span>  
  
|<span data-ttu-id="6c6b0-106">Interface</span><span class="sxs-lookup"><span data-stu-id="6c6b0-106">Interface</span></span>|<span data-ttu-id="6c6b0-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="6c6b0-107">Description</span></span>|  
|---------------|-----------------|  
|`IMarshal`|<span data-ttu-id="6c6b0-108">Fornece métodos para criar, inicializar e gerenciar um proxy em um processo de cliente.</span><span class="sxs-lookup"><span data-stu-id="6c6b0-108">Provides methods for creating, initializing, and managing a proxy in a client process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6c6b0-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6c6b0-109">Requirements</span></span>  
 <span data-ttu-id="6c6b0-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c6b0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c6b0-111">**Cabeçalho:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="6c6b0-111">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="6c6b0-112">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="6c6b0-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6c6b0-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c6b0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c6b0-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6c6b0-114">See also</span></span>

- [<span data-ttu-id="6c6b0-115">Coclasses de hospedagem</span><span class="sxs-lookup"><span data-stu-id="6c6b0-115">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
