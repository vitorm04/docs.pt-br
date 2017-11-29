---
title: Interface ICLRHostProtectionManager
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRHostProtectionManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRHostProtectionManager
helpviewer_keywords: ICLRHostProtectionManager interface [.NET Framework hosting]
ms.assetid: ce2770ae-23d0-45d9-8bcf-46504ac5020e
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c88279eb26b819adaaaf86dcf59105c6ac728017
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrhostprotectionmanager-interface"></a><span data-ttu-id="00f92-102">Interface ICLRHostProtectionManager</span><span class="sxs-lookup"><span data-stu-id="00f92-102">ICLRHostProtectionManager Interface</span></span>
<span data-ttu-id="00f92-103">Permite que o host bloquear as classes gerenciadas específicos, métodos, propriedades e campos da execução de código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="00f92-103">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="00f92-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="00f92-104">Methods</span></span>  
  
|<span data-ttu-id="00f92-105">Método</span><span class="sxs-lookup"><span data-stu-id="00f92-105">Method</span></span>|<span data-ttu-id="00f92-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="00f92-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="00f92-107">SetEagerSerializeGrantSets</span><span class="sxs-lookup"><span data-stu-id="00f92-107">SetEagerSerializeGrantSets</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|<span data-ttu-id="00f92-108">Fornece uma garantia de que certas condições raras de corrida que podem causar erros de tempo de execução (CLR) de linguagem comum fatal nunca ocorrerá.</span><span class="sxs-lookup"><span data-stu-id="00f92-108">Provides a guarantee that certain rare race conditions that can cause fatal common language runtime (CLR) errors will never arise.</span></span>|  
|[<span data-ttu-id="00f92-109">Método SetProtectedCategories</span><span class="sxs-lookup"><span data-stu-id="00f92-109">SetProtectedCategories Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md)|<span data-ttu-id="00f92-110">Especifica as categorias de tipos gerenciados e os membros que devem ser bloqueados da execução de código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="00f92-110">Specifies the categories of managed types and members that should be blocked from running in partially trusted code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="00f92-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="00f92-111">Requirements</span></span>  
 <span data-ttu-id="00f92-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00f92-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00f92-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="00f92-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="00f92-114">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="00f92-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="00f92-115">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00f92-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00f92-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="00f92-116">See Also</span></span>  
 [<span data-ttu-id="00f92-117">Enumeração EApiCategories</span><span class="sxs-lookup"><span data-stu-id="00f92-117">EApiCategories Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)  
 [<span data-ttu-id="00f92-118">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="00f92-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
