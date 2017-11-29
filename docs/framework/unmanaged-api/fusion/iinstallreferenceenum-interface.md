---
title: Interface IInstallReferenceEnum
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IInstallReferenceEnum
api_location: fusion.dll
api_type: COM
f1_keywords: IInstallReferenceEnum
helpviewer_keywords: IInstallReferenceEnum interface [.NET Framework fusion]
ms.assetid: 2863b33b-a541-462c-bbe8-702a2832898e
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d3847d06c77a92eb6e63542f03405ca0cb9c9560
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iinstallreferenceenum-interface"></a><span data-ttu-id="98a0f-102">Interface IInstallReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="98a0f-102">IInstallReferenceEnum Interface</span></span>
<span data-ttu-id="98a0f-103">Representa um enumerador para os assemblies referenciados instalados no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="98a0f-103">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98a0f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="98a0f-104">Syntax</span></span>  
  
```  
interface IInstallReferenceEnum : IUnknown {  
    HRESULT GetNextInstallReferenceItem (  
        [out] IInstallReferenceItem **ppRefItem,  
        [in]  DWORD dwFlags,  
        [in]  LPVOID pvReserved  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="98a0f-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="98a0f-105">Methods</span></span>  
  
|<span data-ttu-id="98a0f-106">Método</span><span class="sxs-lookup"><span data-stu-id="98a0f-106">Method</span></span>|<span data-ttu-id="98a0f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="98a0f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="98a0f-108">Método GetNextInstallReferenceItem</span><span class="sxs-lookup"><span data-stu-id="98a0f-108">GetNextInstallReferenceItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-getnextinstallreferenceitem-method.md)|<span data-ttu-id="98a0f-109">Obtém um ponteiro para o próximo `IInstallReferenceItem` contidos neste `IInstallReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="98a0f-109">Gets a pointer to the next `IInstallReferenceItem` contained in this `IInstallReferenceEnum`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="98a0f-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="98a0f-110">Requirements</span></span>  
 <span data-ttu-id="98a0f-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98a0f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98a0f-112">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="98a0f-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="98a0f-113">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98a0f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98a0f-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="98a0f-114">See Also</span></span>  
 [<span data-ttu-id="98a0f-115">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="98a0f-115">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="98a0f-116">Interface IInstallReferenceItem</span><span class="sxs-lookup"><span data-stu-id="98a0f-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)
