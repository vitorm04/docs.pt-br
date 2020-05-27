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
ms.openlocfilehash: fe5ffbab93df7168015e2a31d6e32ec45dce0960
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007683"
---
# <a name="corlinkeroptions-enumeration"></a><span data-ttu-id="a8057-102">Enumeração CorLinkerOptions</span><span class="sxs-lookup"><span data-stu-id="a8057-102">CorLinkerOptions Enumeration</span></span>
<span data-ttu-id="a8057-103">Especifica sinalizadores para selecionar opções para o vinculador de metadados.</span><span class="sxs-lookup"><span data-stu-id="a8057-103">Specifies flags to select options for the metadata linker.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8057-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a8057-104">Syntax</span></span>  
  
```cpp  
typedef enum CorLinkerOptions {  
    MDAssembly          = 0x00000000,  
    MDNetModule         = 0x00000001,  
} CorLinkerOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="a8057-105">Membros</span><span class="sxs-lookup"><span data-stu-id="a8057-105">Members</span></span>  
  
|<span data-ttu-id="a8057-106">Membro</span><span class="sxs-lookup"><span data-stu-id="a8057-106">Member</span></span>|<span data-ttu-id="a8057-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8057-107">Description</span></span>|  
|------------|-----------------|  
|`MDAssembly`|<span data-ttu-id="a8057-108">Os tipos privados e as funções globais não são preservadas.</span><span class="sxs-lookup"><span data-stu-id="a8057-108">The private types and global functions are not preserved.</span></span>|  
|`MDNetModule`|<span data-ttu-id="a8057-109">Os tipos privados e as funções globais são preservados.</span><span class="sxs-lookup"><span data-stu-id="a8057-109">The private types and global functions are preserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a8057-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a8057-110">Requirements</span></span>  
 <span data-ttu-id="a8057-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8057-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8057-112">**Cabeçalho:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="a8057-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="a8057-113">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8057-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8057-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="a8057-114">See also</span></span>

- [<span data-ttu-id="a8057-115">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="a8057-115">Metadata Enumerations</span></span>](metadata-enumerations.md)
