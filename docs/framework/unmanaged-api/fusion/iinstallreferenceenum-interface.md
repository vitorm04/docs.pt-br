---
title: Interface IInstallReferenceEnum
ms.date: 03/30/2017
api_name:
- IInstallReferenceEnum
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceEnum
helpviewer_keywords:
- IInstallReferenceEnum interface [.NET Framework fusion]
ms.assetid: 2863b33b-a541-462c-bbe8-702a2832898e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 35faeb69e864a428dc40394ad89a7d50b95bbcab
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59103316"
---
# <a name="iinstallreferenceenum-interface"></a><span data-ttu-id="17f77-102">Interface IInstallReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="17f77-102">IInstallReferenceEnum Interface</span></span>
<span data-ttu-id="17f77-103">Representa um enumerador para os assemblies referenciados instalados no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="17f77-103">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17f77-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="17f77-104">Syntax</span></span>  
  
```  
interface IInstallReferenceEnum : IUnknown {  
    HRESULT GetNextInstallReferenceItem (  
        [out] IInstallReferenceItem **ppRefItem,  
        [in]  DWORD dwFlags,  
        [in]  LPVOID pvReserved  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="17f77-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="17f77-105">Methods</span></span>  
  
|<span data-ttu-id="17f77-106">Método</span><span class="sxs-lookup"><span data-stu-id="17f77-106">Method</span></span>|<span data-ttu-id="17f77-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="17f77-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="17f77-108">Método GetNextInstallReferenceItem</span><span class="sxs-lookup"><span data-stu-id="17f77-108">GetNextInstallReferenceItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-getnextinstallreferenceitem-method.md)|<span data-ttu-id="17f77-109">Obtém um ponteiro para a próxima `IInstallReferenceItem` contidas neste `IInstallReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="17f77-109">Gets a pointer to the next `IInstallReferenceItem` contained in this `IInstallReferenceEnum`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="17f77-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="17f77-110">Requirements</span></span>  
 <span data-ttu-id="17f77-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17f77-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17f77-112">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="17f77-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="17f77-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17f77-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17f77-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="17f77-114">See also</span></span>

- [<span data-ttu-id="17f77-115">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="17f77-115">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="17f77-116">Interface IInstallReferenceItem</span><span class="sxs-lookup"><span data-stu-id="17f77-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)
