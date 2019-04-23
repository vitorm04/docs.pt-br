---
title: Interface ICLRHostProtectionManager
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager
helpviewer_keywords:
- ICLRHostProtectionManager interface [.NET Framework hosting]
ms.assetid: ce2770ae-23d0-45d9-8bcf-46504ac5020e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd096344c987d8901f0baab86e370abbb03528e5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59177769"
---
# <a name="iclrhostprotectionmanager-interface"></a><span data-ttu-id="e4408-102">Interface ICLRHostProtectionManager</span><span class="sxs-lookup"><span data-stu-id="e4408-102">ICLRHostProtectionManager Interface</span></span>
<span data-ttu-id="e4408-103">Permite que o host ao bloquear classes gerenciadas específicas, métodos, propriedades e campos da execução em código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="e4408-103">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e4408-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="e4408-104">Methods</span></span>  
  
|<span data-ttu-id="e4408-105">Método</span><span class="sxs-lookup"><span data-stu-id="e4408-105">Method</span></span>|<span data-ttu-id="e4408-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="e4408-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e4408-107">SetEagerSerializeGrantSets</span><span class="sxs-lookup"><span data-stu-id="e4408-107">SetEagerSerializeGrantSets</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|<span data-ttu-id="e4408-108">Fornece uma garantia de que certas condições raras de corrida que podem causar erros de runtime (CLR) de linguagem comum fatal nunca surgirão.</span><span class="sxs-lookup"><span data-stu-id="e4408-108">Provides a guarantee that certain rare race conditions that can cause fatal common language runtime (CLR) errors will never arise.</span></span>|  
|[<span data-ttu-id="e4408-109">Método SetProtectedCategories</span><span class="sxs-lookup"><span data-stu-id="e4408-109">SetProtectedCategories Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md)|<span data-ttu-id="e4408-110">Especifica as categorias de tipos gerenciados e os membros que devem ser impedidos de executar código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="e4408-110">Specifies the categories of managed types and members that should be blocked from running in partially trusted code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e4408-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e4408-111">Requirements</span></span>  
 <span data-ttu-id="e4408-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4408-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4408-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e4408-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e4408-114">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="e4408-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e4408-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4408-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4408-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e4408-116">See also</span></span>

- [<span data-ttu-id="e4408-117">Enumeração EApiCategories</span><span class="sxs-lookup"><span data-stu-id="e4408-117">EApiCategories Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)
- [<span data-ttu-id="e4408-118">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="e4408-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
