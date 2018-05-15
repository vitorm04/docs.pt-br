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
ms.openlocfilehash: 7884d53630ca13a30d7b4efd55d46684a9dd7d30
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="comcallunmarshal-coclass"></a><span data-ttu-id="da377-102">Coclass ComCallUnmarshal</span><span class="sxs-lookup"><span data-stu-id="da377-102">ComCallUnmarshal Coclass</span></span>
<span data-ttu-id="da377-103">Fornece interfaces para gerenciar o marshaling de ponteiros de interface.</span><span class="sxs-lookup"><span data-stu-id="da377-103">Provides interfaces for managing the marshaling of interface pointers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da377-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="da377-104">Syntax</span></span>  
  
```  
coclass ComCallUnmarshal {  
    [default] interface IMarshal;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="da377-105">Interfaces</span><span class="sxs-lookup"><span data-stu-id="da377-105">Interfaces</span></span>  
  
|<span data-ttu-id="da377-106">Interface</span><span class="sxs-lookup"><span data-stu-id="da377-106">Interface</span></span>|<span data-ttu-id="da377-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="da377-107">Description</span></span>|  
|---------------|-----------------|  
|`IMarshal`|<span data-ttu-id="da377-108">Fornece métodos para criar, inicializar e gerenciando um proxy em um processo de cliente.</span><span class="sxs-lookup"><span data-stu-id="da377-108">Provides methods for creating, initializing, and managing a proxy in a client process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="da377-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="da377-109">Requirements</span></span>  
 <span data-ttu-id="da377-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da377-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da377-111">**Cabeçalho:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="da377-111">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="da377-112">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="da377-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="da377-113">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da377-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da377-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="da377-114">See Also</span></span>  
 [<span data-ttu-id="da377-115">Coclasses de hospedagem</span><span class="sxs-lookup"><span data-stu-id="da377-115">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
