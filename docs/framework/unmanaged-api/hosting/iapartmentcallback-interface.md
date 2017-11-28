---
title: Interface IApartmentCallback
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IApartmentCallback
api_location: mscoree.dll
api_type: COM
f1_keywords: IApartmentCallback
helpviewer_keywords: IApartmentCallback interface [.NET Framework hosting]
ms.assetid: 57c33c58-bf0b-4533-b569-e6a682d02cba
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5d2f2ea73da2273ff6f0abb725ec3e3fb8ca79ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="iapartmentcallback-interface"></a><span data-ttu-id="2da64-102">Interface IApartmentCallback</span><span class="sxs-lookup"><span data-stu-id="2da64-102">IApartmentCallback Interface</span></span>
<span data-ttu-id="2da64-103">Fornece métodos para fazer retornos de chamada em um apartment.</span><span class="sxs-lookup"><span data-stu-id="2da64-103">Provides methods for making callbacks within an apartment.</span></span> <span data-ttu-id="2da64-104">Um *apartment* é um contêiner lógico em um processo para objetos que compartilham os mesmos requisitos de acesso de thread.</span><span class="sxs-lookup"><span data-stu-id="2da64-104">An *apartment* is a logical container within a process for objects that share the same thread access requirements.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2da64-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="2da64-105">Methods</span></span>  
  
|<span data-ttu-id="2da64-106">Método</span><span class="sxs-lookup"><span data-stu-id="2da64-106">Method</span></span>|<span data-ttu-id="2da64-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="2da64-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2da64-108">Método DoCallback</span><span class="sxs-lookup"><span data-stu-id="2da64-108">DoCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-docallback-method.md)|<span data-ttu-id="2da64-109">Executa a função especificada em um apartment.</span><span class="sxs-lookup"><span data-stu-id="2da64-109">Executes the specified function within an apartment.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2da64-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2da64-110">Requirements</span></span>  
 <span data-ttu-id="2da64-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2da64-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2da64-112">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2da64-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2da64-113">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="2da64-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2da64-114">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2da64-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2da64-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2da64-115">See Also</span></span>  
 [<span data-ttu-id="2da64-116">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="2da64-116">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
