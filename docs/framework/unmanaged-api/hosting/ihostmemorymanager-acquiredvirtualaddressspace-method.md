---
title: Método IHostMemoryManager::AcquiredVirtualAddressSpace
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.AcquiredVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::AcquiredVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::AcquiredVirtualAddressSpace method [.NET Framework hosting]
- AcquiredVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: ef2f83c2-127e-4c38-8385-306c03cd2167
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b6133b558e62d66cfaac201317f66d784aac264c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54513705"
---
# <a name="ihostmemorymanageracquiredvirtualaddressspace-method"></a><span data-ttu-id="76219-102">Método IHostMemoryManager::AcquiredVirtualAddressSpace</span><span class="sxs-lookup"><span data-stu-id="76219-102">IHostMemoryManager::AcquiredVirtualAddressSpace Method</span></span>
<span data-ttu-id="76219-103">Notifica o host que o common language runtime (CLR) adquiriu a memória especificada do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="76219-103">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76219-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="76219-104">Syntax</span></span>  
  
```  
HRESULT AcquiredVirtualAddressSpace(  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="76219-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="76219-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="76219-106">[in] O endereço inicial da memória.</span><span class="sxs-lookup"><span data-stu-id="76219-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="76219-107">[in] O tamanho, em bytes, da memória.</span><span class="sxs-lookup"><span data-stu-id="76219-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76219-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="76219-108">Remarks</span></span>  
 <span data-ttu-id="76219-109">O `AcquiredVirtualAddressSpace` é um método de retorno de chamada de método e deve ser implementado pelo gravador do aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="76219-109">The `AcquiredVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="76219-110">Ele é chamado pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="76219-110">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76219-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="76219-111">Requirements</span></span>  
 <span data-ttu-id="76219-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76219-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76219-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="76219-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="76219-114">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="76219-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="76219-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76219-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76219-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="76219-116">See also</span></span>
- [<span data-ttu-id="76219-117">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="76219-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
