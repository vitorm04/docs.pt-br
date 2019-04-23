---
title: Interface IApartmentCallback
ms.date: 03/30/2017
api_name:
- IApartmentCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IApartmentCallback
helpviewer_keywords:
- IApartmentCallback interface [.NET Framework hosting]
ms.assetid: 57c33c58-bf0b-4533-b569-e6a682d02cba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db933716cc0602ecda5da8a72726408ae4910179
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59129799"
---
# <a name="iapartmentcallback-interface"></a><span data-ttu-id="0060d-102">Interface IApartmentCallback</span><span class="sxs-lookup"><span data-stu-id="0060d-102">IApartmentCallback Interface</span></span>
<span data-ttu-id="0060d-103">Fornece métodos para fazer retornos de chamada dentro de um apartamento.</span><span class="sxs-lookup"><span data-stu-id="0060d-103">Provides methods for making callbacks within an apartment.</span></span> <span data-ttu-id="0060d-104">Uma *apartment* é um contêiner lógico dentro de um processo para objetos que compartilham os mesmos requisitos de acesso de thread.</span><span class="sxs-lookup"><span data-stu-id="0060d-104">An *apartment* is a logical container within a process for objects that share the same thread access requirements.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0060d-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="0060d-105">Methods</span></span>  
  
|<span data-ttu-id="0060d-106">Método</span><span class="sxs-lookup"><span data-stu-id="0060d-106">Method</span></span>|<span data-ttu-id="0060d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="0060d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0060d-108">Método DoCallback</span><span class="sxs-lookup"><span data-stu-id="0060d-108">DoCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-docallback-method.md)|<span data-ttu-id="0060d-109">Executa a função especificada em um apartment.</span><span class="sxs-lookup"><span data-stu-id="0060d-109">Executes the specified function within an apartment.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0060d-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0060d-110">Requirements</span></span>  
 <span data-ttu-id="0060d-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0060d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0060d-112">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0060d-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0060d-113">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="0060d-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0060d-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0060d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0060d-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0060d-115">See also</span></span>

- [<span data-ttu-id="0060d-116">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="0060d-116">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
