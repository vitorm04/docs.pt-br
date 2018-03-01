---
title: Interface ICLRHostProtectionManager
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 37b1aaeef1d4c375f36ad043124287fc3b41e3fe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrhostprotectionmanager-interface"></a><span data-ttu-id="477d4-102">Interface ICLRHostProtectionManager</span><span class="sxs-lookup"><span data-stu-id="477d4-102">ICLRHostProtectionManager Interface</span></span>
<span data-ttu-id="477d4-103">Permite que o host bloquear as classes gerenciadas específicos, métodos, propriedades e campos da execução de código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="477d4-103">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="477d4-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="477d4-104">Methods</span></span>  
  
|<span data-ttu-id="477d4-105">Método</span><span class="sxs-lookup"><span data-stu-id="477d4-105">Method</span></span>|<span data-ttu-id="477d4-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="477d4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="477d4-107">SetEagerSerializeGrantSets</span><span class="sxs-lookup"><span data-stu-id="477d4-107">SetEagerSerializeGrantSets</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|<span data-ttu-id="477d4-108">Fornece uma garantia de que certas condições raras de corrida que podem causar erros de tempo de execução (CLR) de linguagem comum fatal nunca ocorrerá.</span><span class="sxs-lookup"><span data-stu-id="477d4-108">Provides a guarantee that certain rare race conditions that can cause fatal common language runtime (CLR) errors will never arise.</span></span>|  
|[<span data-ttu-id="477d4-109">Método SetProtectedCategories</span><span class="sxs-lookup"><span data-stu-id="477d4-109">SetProtectedCategories Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md)|<span data-ttu-id="477d4-110">Especifica as categorias de tipos gerenciados e os membros que devem ser bloqueados da execução de código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="477d4-110">Specifies the categories of managed types and members that should be blocked from running in partially trusted code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="477d4-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="477d4-111">Requirements</span></span>  
 <span data-ttu-id="477d4-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="477d4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="477d4-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="477d4-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="477d4-114">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="477d4-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="477d4-115">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="477d4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="477d4-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="477d4-116">See Also</span></span>  
 [<span data-ttu-id="477d4-117">Enumeração EApiCategories</span><span class="sxs-lookup"><span data-stu-id="477d4-117">EApiCategories Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)  
 [<span data-ttu-id="477d4-118">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="477d4-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
