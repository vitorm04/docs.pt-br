---
title: Interface IGCHost2
ms.date: 03/30/2017
api_name:
- IGCHost2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2
helpviewer_keywords:
- IGCHost2 interface [.NET Framework hosting]
ms.assetid: e5323fa4-18ac-424d-859d-a65a550d08d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5c6cbf44bd02a45b9b99d2dad63fc5bd6219c4ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437671"
---
# <a name="igchost2-interface"></a><span data-ttu-id="e7bf9-102">Interface IGCHost2</span><span class="sxs-lookup"><span data-stu-id="e7bf9-102">IGCHost2 Interface</span></span>
<span data-ttu-id="e7bf9-103">Fornece métodos para obter informações sobre o sistema de coleta de lixo e para controlar alguns aspectos da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="e7bf9-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7bf9-104">Para novos desenvolvimentos, recomendamos que você use o [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) interface em vez disso.</span><span class="sxs-lookup"><span data-stu-id="e7bf9-104">For new development, we recommend that you use the [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) interface instead.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e7bf9-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="e7bf9-105">Methods</span></span>  
  
|<span data-ttu-id="e7bf9-106">Método</span><span class="sxs-lookup"><span data-stu-id="e7bf9-106">Method</span></span>|<span data-ttu-id="e7bf9-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e7bf9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e7bf9-108">Método SetGCStartupLimitsEx</span><span class="sxs-lookup"><span data-stu-id="e7bf9-108">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)|<span data-ttu-id="e7bf9-109">Define o tamanho do segmento e o tamanho máximo de geração 0.</span><span class="sxs-lookup"><span data-stu-id="e7bf9-109">Sets the segment size and the maximum size for generation 0.</span></span> <span data-ttu-id="e7bf9-110">Habilita a geração 0 e tamanhos de segmento maior do que `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="e7bf9-110">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e7bf9-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e7bf9-111">Requirements</span></span>  
 <span data-ttu-id="e7bf9-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7bf9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7bf9-113">**Cabeçalho:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="e7bf9-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="e7bf9-114">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="e7bf9-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e7bf9-115">**Versões do .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7bf9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7bf9-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e7bf9-116">See Also</span></span>  
 [<span data-ttu-id="e7bf9-117">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="e7bf9-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="e7bf9-118">Interfaces de hospedagem CLR</span><span class="sxs-lookup"><span data-stu-id="e7bf9-118">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [<span data-ttu-id="e7bf9-119">Coclass CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="e7bf9-119">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
