---
title: "Método IHostMemoryManager::NeedsVirtualAddressSpace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.NeedsVirtualAddressSpace
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::NeedsVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace method [.NET Framework hosting]
- NeedsVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: 71f0eab5-0170-46f8-9f88-1df5abdeb34a
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9251cbadaf182cda8d52f3f5792452310561c376
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmemorymanagerneedsvirtualaddressspace-method"></a><span data-ttu-id="a71d4-102">Método IHostMemoryManager::NeedsVirtualAddressSpace</span><span class="sxs-lookup"><span data-stu-id="a71d4-102">IHostMemoryManager::NeedsVirtualAddressSpace Method</span></span>
<span data-ttu-id="a71d4-103">Notifica o host que o common language runtime (CLR) vai tentar usar a memória especificada.</span><span class="sxs-lookup"><span data-stu-id="a71d4-103">Notifies the host that the common language runtime (CLR) is going to attempt to use the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a71d4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a71d4-104">Syntax</span></span>  
  
```  
HRESULT NeedsVirtualAddressSpace (  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a71d4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a71d4-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="a71d4-106">[in] O endereço inicial da memória.</span><span class="sxs-lookup"><span data-stu-id="a71d4-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="a71d4-107">[in] O tamanho, em bytes, da memória.</span><span class="sxs-lookup"><span data-stu-id="a71d4-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a71d4-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="a71d4-108">Remarks</span></span>  
 <span data-ttu-id="a71d4-109">O `NeedsVirtualAddressSpace` é um método de retorno de chamada de método e deve ser implementado pelo gerador de aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="a71d4-109">The `NeedsVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="a71d4-110">Ele é chamado pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="a71d4-110">It is called by the CLR.</span></span>  
  
 <span data-ttu-id="a71d4-111">Se o host não quer que o CLR para usar a memória especificada, ela pode retornar um HRESULT E_OUTOFMEMORY.</span><span class="sxs-lookup"><span data-stu-id="a71d4-111">If the host does not want the CLR to use the specified memory, it may return an E_OUTOFMEMORY HRESULT.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a71d4-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a71d4-112">Requirements</span></span>  
 <span data-ttu-id="a71d4-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a71d4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a71d4-114">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a71d4-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a71d4-115">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="a71d4-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a71d4-116">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a71d4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a71d4-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a71d4-117">See Also</span></span>  
 [<span data-ttu-id="a71d4-118">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="a71d4-118">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
