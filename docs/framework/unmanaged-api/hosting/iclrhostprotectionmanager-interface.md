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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61944658"
---
# <a name="iclrhostprotectionmanager-interface"></a><span data-ttu-id="2ee8e-102">Interface ICLRHostProtectionManager</span><span class="sxs-lookup"><span data-stu-id="2ee8e-102">ICLRHostProtectionManager Interface</span></span>
<span data-ttu-id="2ee8e-103">Permite que o host ao bloquear classes gerenciadas específicas, métodos, propriedades e campos da execução em código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="2ee8e-103">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2ee8e-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="2ee8e-104">Methods</span></span>  
  
|<span data-ttu-id="2ee8e-105">Método</span><span class="sxs-lookup"><span data-stu-id="2ee8e-105">Method</span></span>|<span data-ttu-id="2ee8e-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="2ee8e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2ee8e-107">SetEagerSerializeGrantSets</span><span class="sxs-lookup"><span data-stu-id="2ee8e-107">SetEagerSerializeGrantSets</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|<span data-ttu-id="2ee8e-108">Fornece uma garantia de que certas condições raras de corrida que podem causar erros de runtime (CLR) de linguagem comum fatal nunca surgirão.</span><span class="sxs-lookup"><span data-stu-id="2ee8e-108">Provides a guarantee that certain rare race conditions that can cause fatal common language runtime (CLR) errors will never arise.</span></span>|  
|[<span data-ttu-id="2ee8e-109">Método SetProtectedCategories</span><span class="sxs-lookup"><span data-stu-id="2ee8e-109">SetProtectedCategories Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md)|<span data-ttu-id="2ee8e-110">Especifica as categorias de tipos gerenciados e os membros que devem ser impedidos de executar código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="2ee8e-110">Specifies the categories of managed types and members that should be blocked from running in partially trusted code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2ee8e-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2ee8e-111">Requirements</span></span>  
 <span data-ttu-id="2ee8e-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ee8e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ee8e-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2ee8e-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2ee8e-114">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="2ee8e-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2ee8e-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ee8e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ee8e-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2ee8e-116">See also</span></span>

- [<span data-ttu-id="2ee8e-117">Enumeração EApiCategories</span><span class="sxs-lookup"><span data-stu-id="2ee8e-117">EApiCategories Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)
- [<span data-ttu-id="2ee8e-118">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="2ee8e-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
