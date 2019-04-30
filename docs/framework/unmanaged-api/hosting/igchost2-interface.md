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
ms.openlocfilehash: 75bef91eb70c8109653741452362cd2e85f625ce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946101"
---
# <a name="igchost2-interface"></a><span data-ttu-id="9409c-102">Interface IGCHost2</span><span class="sxs-lookup"><span data-stu-id="9409c-102">IGCHost2 Interface</span></span>
<span data-ttu-id="9409c-103">Fornece métodos para obter informações sobre o sistema de coleta de lixo e para controlar alguns aspectos da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="9409c-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9409c-104">Para novos desenvolvimentos, recomendamos que você use o [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) interface em vez disso.</span><span class="sxs-lookup"><span data-stu-id="9409c-104">For new development, we recommend that you use the [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) interface instead.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9409c-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="9409c-105">Methods</span></span>  
  
|<span data-ttu-id="9409c-106">Método</span><span class="sxs-lookup"><span data-stu-id="9409c-106">Method</span></span>|<span data-ttu-id="9409c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9409c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9409c-108">Método SetGCStartupLimitsEx</span><span class="sxs-lookup"><span data-stu-id="9409c-108">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)|<span data-ttu-id="9409c-109">Define o tamanho do segmento e o tamanho máximo para a geração 0.</span><span class="sxs-lookup"><span data-stu-id="9409c-109">Sets the segment size and the maximum size for generation 0.</span></span> <span data-ttu-id="9409c-110">Habilita a geração 0 e tamanhos de segmento maiores do que `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="9409c-110">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9409c-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9409c-111">Requirements</span></span>  
 <span data-ttu-id="9409c-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9409c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9409c-113">**Cabeçalho:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="9409c-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="9409c-114">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="9409c-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9409c-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9409c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9409c-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9409c-116">See also</span></span>

- [<span data-ttu-id="9409c-117">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="9409c-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="9409c-118">Interfaces de hospedagem CLR</span><span class="sxs-lookup"><span data-stu-id="9409c-118">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="9409c-119">Coclass CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="9409c-119">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
