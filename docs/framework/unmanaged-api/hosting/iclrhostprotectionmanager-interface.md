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
ms.openlocfilehash: c630fcd4667c8b19c4e21335549674d32508e439
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432830"
---
# <a name="iclrhostprotectionmanager-interface"></a><span data-ttu-id="085b2-102">Interface ICLRHostProtectionManager</span><span class="sxs-lookup"><span data-stu-id="085b2-102">ICLRHostProtectionManager Interface</span></span>
<span data-ttu-id="085b2-103">Permite que o host bloquear as classes gerenciadas específicos, métodos, propriedades e campos da execução de código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="085b2-103">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="085b2-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="085b2-104">Methods</span></span>  
  
|<span data-ttu-id="085b2-105">Método</span><span class="sxs-lookup"><span data-stu-id="085b2-105">Method</span></span>|<span data-ttu-id="085b2-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="085b2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="085b2-107">SetEagerSerializeGrantSets</span><span class="sxs-lookup"><span data-stu-id="085b2-107">SetEagerSerializeGrantSets</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|<span data-ttu-id="085b2-108">Fornece uma garantia de que certas condições raras de corrida que podem causar erros de tempo de execução (CLR) de linguagem comum fatal nunca ocorrerá.</span><span class="sxs-lookup"><span data-stu-id="085b2-108">Provides a guarantee that certain rare race conditions that can cause fatal common language runtime (CLR) errors will never arise.</span></span>|  
|[<span data-ttu-id="085b2-109">Método SetProtectedCategories</span><span class="sxs-lookup"><span data-stu-id="085b2-109">SetProtectedCategories Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md)|<span data-ttu-id="085b2-110">Especifica as categorias de tipos gerenciados e os membros que devem ser bloqueados da execução de código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="085b2-110">Specifies the categories of managed types and members that should be blocked from running in partially trusted code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="085b2-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="085b2-111">Requirements</span></span>  
 <span data-ttu-id="085b2-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="085b2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="085b2-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="085b2-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="085b2-114">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="085b2-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="085b2-115">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="085b2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="085b2-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="085b2-116">See Also</span></span>  
 [<span data-ttu-id="085b2-117">Enumeração EApiCategories</span><span class="sxs-lookup"><span data-stu-id="085b2-117">EApiCategories Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)  
 [<span data-ttu-id="085b2-118">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="085b2-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
