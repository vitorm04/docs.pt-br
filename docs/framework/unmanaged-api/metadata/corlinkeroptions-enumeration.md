---
title: Enumeração CorLinkerOptions
ms.date: 03/30/2017
api_name:
- CorLinkerOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorLinkerOptions
helpviewer_keywords:
- CorLinkerOptions enumeration [.NET Framework metadata]
ms.assetid: a656aad6-cc7e-4994-8251-004a6a45e18f
topic_type:
- apiref
ms.openlocfilehash: 086e17185df9caa823b44b51cf027f95d635c48d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450263"
---
# <a name="corlinkeroptions-enumeration"></a><span data-ttu-id="949fc-102">Enumeração CorLinkerOptions</span><span class="sxs-lookup"><span data-stu-id="949fc-102">CorLinkerOptions Enumeration</span></span>
<span data-ttu-id="949fc-103">Especifica sinalizadores para selecionar opções para o vinculador de metadados.</span><span class="sxs-lookup"><span data-stu-id="949fc-103">Specifies flags to select options for the metadata linker.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="949fc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="949fc-104">Syntax</span></span>  
  
```cpp  
typedef enum CorLinkerOptions {  
    MDAssembly          = 0x00000000,  
    MDNetModule         = 0x00000001,  
} CorLinkerOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="949fc-105">Membros</span><span class="sxs-lookup"><span data-stu-id="949fc-105">Members</span></span>  
  
|<span data-ttu-id="949fc-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="949fc-106">Member</span></span>|<span data-ttu-id="949fc-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="949fc-107">Description</span></span>|  
|------------|-----------------|  
|`MDAssembly`|<span data-ttu-id="949fc-108">Os tipos privados e as funções globais não são preservadas.</span><span class="sxs-lookup"><span data-stu-id="949fc-108">The private types and global functions are not preserved.</span></span>|  
|`MDNetModule`|<span data-ttu-id="949fc-109">Os tipos privados e as funções globais são preservados.</span><span class="sxs-lookup"><span data-stu-id="949fc-109">The private types and global functions are preserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="949fc-110">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="949fc-110">Requirements</span></span>  
 <span data-ttu-id="949fc-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="949fc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="949fc-112">**Cabeçalho:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="949fc-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="949fc-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="949fc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="949fc-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="949fc-114">See also</span></span>

- [<span data-ttu-id="949fc-115">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="949fc-115">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
