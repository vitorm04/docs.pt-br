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
ms.openlocfilehash: 976673a0caab4e041cc80e5536544c195fcf692a
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805173"
---
# <a name="igchost2-interface"></a><span data-ttu-id="089ca-102">Interface IGCHost2</span><span class="sxs-lookup"><span data-stu-id="089ca-102">IGCHost2 Interface</span></span>
<span data-ttu-id="089ca-103">Fornece métodos para obter informações sobre o sistema de coleta de lixo e para controlar alguns aspectos da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="089ca-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="089ca-104">Para um novo desenvolvimento, recomendamos que você use a interface [ICLRGCManager2](iclrgcmanager2-interface.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="089ca-104">For new development, we recommend that you use the [ICLRGCManager2](iclrgcmanager2-interface.md) interface instead.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="089ca-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="089ca-105">Methods</span></span>  
  
|<span data-ttu-id="089ca-106">Método</span><span class="sxs-lookup"><span data-stu-id="089ca-106">Method</span></span>|<span data-ttu-id="089ca-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="089ca-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="089ca-108">Método SetGCStartupLimitsEx</span><span class="sxs-lookup"><span data-stu-id="089ca-108">SetGCStartupLimitsEx Method</span></span>](igchost2-setgcstartuplimitsex-method.md)|<span data-ttu-id="089ca-109">Define o tamanho do segmento e o tamanho máximo para a geração 0.</span><span class="sxs-lookup"><span data-stu-id="089ca-109">Sets the segment size and the maximum size for generation 0.</span></span> <span data-ttu-id="089ca-110">Habilita a geração 0 e os tamanhos de segmento maiores que `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="089ca-110">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="089ca-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="089ca-111">Requirements</span></span>  
 <span data-ttu-id="089ca-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="089ca-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="089ca-113">**Cabeçalho:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="089ca-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="089ca-114">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="089ca-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="089ca-115">**.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="089ca-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="089ca-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="089ca-116">See also</span></span>

- [<span data-ttu-id="089ca-117">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="089ca-117">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="089ca-118">Interfaces de hospedagem CLR</span><span class="sxs-lookup"><span data-stu-id="089ca-118">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="089ca-119">Coclass CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="089ca-119">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
