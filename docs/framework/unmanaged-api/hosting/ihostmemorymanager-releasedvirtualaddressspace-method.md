---
title: Método IHostMemoryManager::ReleasedVirtualAddressSpace
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.ReleasedVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::ReleasedVirtualAddressSpace
helpviewer_keywords:
- ReleasedVirtualAddressSpace method [.NET Framework hosting]
- IHostMemoryManager::ReleasedVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: d1876601-6ab9-48e1-8ebd-184af1d0cd76
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b7bf2a3e359ca05a147553d89a1d2bb3d235209
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54571043"
---
# <a name="ihostmemorymanagerreleasedvirtualaddressspace-method"></a><span data-ttu-id="89ee3-102">Método IHostMemoryManager::ReleasedVirtualAddressSpace</span><span class="sxs-lookup"><span data-stu-id="89ee3-102">IHostMemoryManager::ReleasedVirtualAddressSpace Method</span></span>
<span data-ttu-id="89ee3-103">Notifica o host que o common language runtime (CLR) foi concluída usando a memória especificada.</span><span class="sxs-lookup"><span data-stu-id="89ee3-103">Notifies the host that the common language runtime (CLR) has finished using the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89ee3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="89ee3-104">Syntax</span></span>  
  
```  
HRESULT ReleasedVirtualAddressSpace(  
    [in] LPVOID startAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="89ee3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="89ee3-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="89ee3-106">[in] Ponteiro para o endereço inicial da memória para ser liberado.</span><span class="sxs-lookup"><span data-stu-id="89ee3-106">[in] Pointer to the starting address of the memory to be released.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89ee3-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="89ee3-107">Remarks</span></span>  
 <span data-ttu-id="89ee3-108">O `ReleasedVirtualAddressSpace` é um método de retorno de chamada de método e deve ser implementado pelo gravador do aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="89ee3-108">The `ReleasedVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="89ee3-109">Ele é chamado pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="89ee3-109">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89ee3-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="89ee3-110">Requirements</span></span>  
 <span data-ttu-id="89ee3-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89ee3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89ee3-112">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="89ee3-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="89ee3-113">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="89ee3-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="89ee3-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89ee3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89ee3-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="89ee3-115">See also</span></span>
- [<span data-ttu-id="89ee3-116">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="89ee3-116">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
