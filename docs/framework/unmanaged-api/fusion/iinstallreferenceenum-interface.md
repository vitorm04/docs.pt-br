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
ms.openlocfilehash: cac9f9db0b7527a80671c825a4435e8ea2d135b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429654"
---
# <a name="iinstallreferenceenum-interface"></a><span data-ttu-id="6d1ba-102">Interface IInstallReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="6d1ba-102">IInstallReferenceEnum Interface</span></span>
<span data-ttu-id="6d1ba-103">Representa um enumerador para os assemblies referenciados instalados no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="6d1ba-103">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d1ba-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6d1ba-104">Syntax</span></span>  
  
```  
interface IInstallReferenceEnum : IUnknown {  
    HRESULT GetNextInstallReferenceItem (  
        [out] IInstallReferenceItem **ppRefItem,  
        [in]  DWORD dwFlags,  
        [in]  LPVOID pvReserved  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="6d1ba-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="6d1ba-105">Methods</span></span>  
  
|<span data-ttu-id="6d1ba-106">Método</span><span class="sxs-lookup"><span data-stu-id="6d1ba-106">Method</span></span>|<span data-ttu-id="6d1ba-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d1ba-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6d1ba-108">Método GetNextInstallReferenceItem</span><span class="sxs-lookup"><span data-stu-id="6d1ba-108">GetNextInstallReferenceItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-getnextinstallreferenceitem-method.md)|<span data-ttu-id="6d1ba-109">Obtém um ponteiro para o próximo `IInstallReferenceItem` contidos neste `IInstallReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="6d1ba-109">Gets a pointer to the next `IInstallReferenceItem` contained in this `IInstallReferenceEnum`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6d1ba-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6d1ba-110">Requirements</span></span>  
 <span data-ttu-id="6d1ba-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d1ba-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d1ba-112">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="6d1ba-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="6d1ba-113">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d1ba-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d1ba-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6d1ba-114">See Also</span></span>  
 [<span data-ttu-id="6d1ba-115">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="6d1ba-115">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="6d1ba-116">Interface IInstallReferenceItem</span><span class="sxs-lookup"><span data-stu-id="6d1ba-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)
