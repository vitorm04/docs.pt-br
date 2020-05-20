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
ms.openlocfilehash: 7b1fc70380fff3c551c56043f49c2deda507e366
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703845"
---
# <a name="iclrhostprotectionmanager-interface"></a><span data-ttu-id="641c6-102">Interface ICLRHostProtectionManager</span><span class="sxs-lookup"><span data-stu-id="641c6-102">ICLRHostProtectionManager Interface</span></span>
<span data-ttu-id="641c6-103">Permite que o host bloqueie classes gerenciadas, métodos, propriedades e campos específicos da execução em código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="641c6-103">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="641c6-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="641c6-104">Methods</span></span>  
  
|<span data-ttu-id="641c6-105">Método</span><span class="sxs-lookup"><span data-stu-id="641c6-105">Method</span></span>|<span data-ttu-id="641c6-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="641c6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="641c6-107">SetEagerSerializeGrantSets</span><span class="sxs-lookup"><span data-stu-id="641c6-107">SetEagerSerializeGrantSets</span></span>](iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|<span data-ttu-id="641c6-108">Fornece uma garantia de que certas condições raras de corrida que podem causar erros fatais de Common Language Runtime (CLR) nunca surgirão.</span><span class="sxs-lookup"><span data-stu-id="641c6-108">Provides a guarantee that certain rare race conditions that can cause fatal common language runtime (CLR) errors will never arise.</span></span>|  
|[<span data-ttu-id="641c6-109">Método SetProtectedCategories</span><span class="sxs-lookup"><span data-stu-id="641c6-109">SetProtectedCategories Method</span></span>](iclrhostprotectionmanager-setprotectedcategories-method.md)|<span data-ttu-id="641c6-110">Especifica as categorias de tipos gerenciados e membros que devem ser impedidos de serem executados em código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="641c6-110">Specifies the categories of managed types and members that should be blocked from running in partially trusted code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="641c6-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="641c6-111">Requirements</span></span>  
 <span data-ttu-id="641c6-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="641c6-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="641c6-113">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="641c6-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="641c6-114">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="641c6-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="641c6-115">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="641c6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="641c6-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="641c6-116">See also</span></span>

- [<span data-ttu-id="641c6-117">Enumeração EApiCategories</span><span class="sxs-lookup"><span data-stu-id="641c6-117">EApiCategories Enumeration</span></span>](eapicategories-enumeration.md)
- [<span data-ttu-id="641c6-118">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="641c6-118">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
