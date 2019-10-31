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
ms.openlocfilehash: d3f7c24b4bd373924c44dbc0490c890e7f1322bd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131727"
---
# <a name="iinstallreferenceenum-interface"></a><span data-ttu-id="e6f4f-102">Interface IInstallReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="e6f4f-102">IInstallReferenceEnum Interface</span></span>
<span data-ttu-id="e6f4f-103">Representa um enumerador para os assemblies referenciados instalados no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="e6f4f-103">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6f4f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e6f4f-104">Syntax</span></span>  
  
```cpp  
interface IInstallReferenceEnum : IUnknown {  
    HRESULT GetNextInstallReferenceItem (  
        [out] IInstallReferenceItem **ppRefItem,  
        [in]  DWORD dwFlags,  
        [in]  LPVOID pvReserved  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e6f4f-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="e6f4f-105">Methods</span></span>  
  
|<span data-ttu-id="e6f4f-106">Método</span><span class="sxs-lookup"><span data-stu-id="e6f4f-106">Method</span></span>|<span data-ttu-id="e6f4f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e6f4f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e6f4f-108">Método GetNextInstallReferenceItem</span><span class="sxs-lookup"><span data-stu-id="e6f4f-108">GetNextInstallReferenceItem Method</span></span>](iinstallreferenceenum-getnextinstallreferenceitem-method.md)|<span data-ttu-id="e6f4f-109">Obtém um ponteiro para a próxima `IInstallReferenceItem` contida neste `IInstallReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="e6f4f-109">Gets a pointer to the next `IInstallReferenceItem` contained in this `IInstallReferenceEnum`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e6f4f-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e6f4f-110">Requirements</span></span>  
 <span data-ttu-id="e6f4f-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6f4f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6f4f-112">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="e6f4f-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="e6f4f-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6f4f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6f4f-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6f4f-114">See also</span></span>

- [<span data-ttu-id="e6f4f-115">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="e6f4f-115">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="e6f4f-116">Interface IInstallReferenceItem</span><span class="sxs-lookup"><span data-stu-id="e6f4f-116">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)
