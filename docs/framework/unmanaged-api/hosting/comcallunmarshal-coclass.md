---
title: Coclass ComCallUnmarshal
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ComCallUnmarshal Coclass
api_location: mscoree.dll
api_type: COM
f1_keywords: ComCallUnmarshal
helpviewer_keywords: ComCallUnmarshal coclass [.NET Framework hosting]
ms.assetid: 2adb5827-2268-4914-a1c6-f62b61880a45
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2760fc84466c85e022421bcc17dcee6444ec859a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="comcallunmarshal-coclass"></a><span data-ttu-id="18e82-102">Coclass ComCallUnmarshal</span><span class="sxs-lookup"><span data-stu-id="18e82-102">ComCallUnmarshal Coclass</span></span>
<span data-ttu-id="18e82-103">Fornece interfaces para gerenciar o marshaling de ponteiros de interface.</span><span class="sxs-lookup"><span data-stu-id="18e82-103">Provides interfaces for managing the marshaling of interface pointers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18e82-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="18e82-104">Syntax</span></span>  
  
```  
coclass ComCallUnmarshal {  
    [default] interface IMarshal;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="18e82-105">Interfaces</span><span class="sxs-lookup"><span data-stu-id="18e82-105">Interfaces</span></span>  
  
|<span data-ttu-id="18e82-106">Interface</span><span class="sxs-lookup"><span data-stu-id="18e82-106">Interface</span></span>|<span data-ttu-id="18e82-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="18e82-107">Description</span></span>|  
|---------------|-----------------|  
|`IMarshal`|<span data-ttu-id="18e82-108">Fornece métodos para criar, inicializar e gerenciando um proxy em um processo de cliente.</span><span class="sxs-lookup"><span data-stu-id="18e82-108">Provides methods for creating, initializing, and managing a proxy in a client process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="18e82-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="18e82-109">Requirements</span></span>  
 <span data-ttu-id="18e82-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18e82-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18e82-111">**Cabeçalho:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="18e82-111">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="18e82-112">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="18e82-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="18e82-113">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18e82-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18e82-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="18e82-114">See Also</span></span>  
 [<span data-ttu-id="18e82-115">Coclasses de hospedagem</span><span class="sxs-lookup"><span data-stu-id="18e82-115">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
