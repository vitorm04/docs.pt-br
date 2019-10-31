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
ms.openlocfilehash: 46082ddcee0163d5e61b3e468eb32c71e9f242ce
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128625"
---
# <a name="ihostmemorymanagerreleasedvirtualaddressspace-method"></a><span data-ttu-id="31199-102">Método IHostMemoryManager::ReleasedVirtualAddressSpace</span><span class="sxs-lookup"><span data-stu-id="31199-102">IHostMemoryManager::ReleasedVirtualAddressSpace Method</span></span>
<span data-ttu-id="31199-103">Notifica o host que o Common Language Runtime (CLR) concluiu usando a memória especificada.</span><span class="sxs-lookup"><span data-stu-id="31199-103">Notifies the host that the common language runtime (CLR) has finished using the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31199-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="31199-104">Syntax</span></span>  
  
```cpp  
HRESULT ReleasedVirtualAddressSpace(  
    [in] LPVOID startAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31199-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="31199-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="31199-106">no Ponteiro para o endereço inicial da memória a ser liberada.</span><span class="sxs-lookup"><span data-stu-id="31199-106">[in] Pointer to the starting address of the memory to be released.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31199-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="31199-107">Remarks</span></span>  
 <span data-ttu-id="31199-108">O método `ReleasedVirtualAddressSpace` é um método de retorno de chamada e deve ser implementado pelo gravador do aplicativo de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="31199-108">The `ReleasedVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="31199-109">Ele é chamado pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="31199-109">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31199-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="31199-110">Requirements</span></span>  
 <span data-ttu-id="31199-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31199-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31199-112">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="31199-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="31199-113">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="31199-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="31199-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31199-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31199-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="31199-115">See also</span></span>

- [<span data-ttu-id="31199-116">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="31199-116">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
