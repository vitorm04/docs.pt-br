---
title: "Método IHostMemoryManager::ReleasedVirtualAddressSpace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.ReleasedVirtualAddressSpace
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::ReleasedVirtualAddressSpace
helpviewer_keywords:
- ReleasedVirtualAddressSpace method [.NET Framework hosting]
- IHostMemoryManager::ReleasedVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: d1876601-6ab9-48e1-8ebd-184af1d0cd76
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c0f2588c34429366794fcfb30c6d6e7038814506
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ihostmemorymanagerreleasedvirtualaddressspace-method"></a><span data-ttu-id="b23b9-102">Método IHostMemoryManager::ReleasedVirtualAddressSpace</span><span class="sxs-lookup"><span data-stu-id="b23b9-102">IHostMemoryManager::ReleasedVirtualAddressSpace Method</span></span>
<span data-ttu-id="b23b9-103">Notifica o host que o common language runtime (CLR) terminou de usar a memória especificada.</span><span class="sxs-lookup"><span data-stu-id="b23b9-103">Notifies the host that the common language runtime (CLR) has finished using the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b23b9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b23b9-104">Syntax</span></span>  
  
```  
HRESULT ReleasedVirtualAddressSpace(  
    [in] LPVOID startAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b23b9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b23b9-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="b23b9-106">[in] Ponteiro para o endereço inicial da memória para ser liberado.</span><span class="sxs-lookup"><span data-stu-id="b23b9-106">[in] Pointer to the starting address of the memory to be released.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b23b9-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="b23b9-107">Remarks</span></span>  
 <span data-ttu-id="b23b9-108">O `ReleasedVirtualAddressSpace` é um método de retorno de chamada de método e deve ser implementado pelo gerador de aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="b23b9-108">The `ReleasedVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="b23b9-109">Ele é chamado pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="b23b9-109">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b23b9-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b23b9-110">Requirements</span></span>  
 <span data-ttu-id="b23b9-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b23b9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b23b9-112">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b23b9-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b23b9-113">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="b23b9-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b23b9-114">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b23b9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b23b9-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b23b9-115">See Also</span></span>  
 [<span data-ttu-id="b23b9-116">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="b23b9-116">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
