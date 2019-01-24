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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0a072e124343641c9f75fb9f924a6409efc8e1d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54719931"
---
# <a name="corlinkeroptions-enumeration"></a><span data-ttu-id="5ede6-102">Enumeração CorLinkerOptions</span><span class="sxs-lookup"><span data-stu-id="5ede6-102">CorLinkerOptions Enumeration</span></span>
<span data-ttu-id="5ede6-103">Especifica os sinalizadores para selecionar opções para o vinculador de metadados.</span><span class="sxs-lookup"><span data-stu-id="5ede6-103">Specifies flags to select options for the metadata linker.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ede6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5ede6-104">Syntax</span></span>  
  
```  
typedef enum CorLinkerOptions {  
    MDAssembly          = 0x00000000,  
    MDNetModule         = 0x00000001,  
} CorLinkerOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="5ede6-105">Membros</span><span class="sxs-lookup"><span data-stu-id="5ede6-105">Members</span></span>  
  
|<span data-ttu-id="5ede6-106">Membro</span><span class="sxs-lookup"><span data-stu-id="5ede6-106">Member</span></span>|<span data-ttu-id="5ede6-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ede6-107">Description</span></span>|  
|------------|-----------------|  
|`MDAssembly`|<span data-ttu-id="5ede6-108">As funções globais e tipos privados não são preservadas.</span><span class="sxs-lookup"><span data-stu-id="5ede6-108">The private types and global functions are not preserved.</span></span>|  
|`MDNetModule`|<span data-ttu-id="5ede6-109">As funções globais e tipos privados são preservadas.</span><span class="sxs-lookup"><span data-stu-id="5ede6-109">The private types and global functions are preserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5ede6-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5ede6-110">Requirements</span></span>  
 <span data-ttu-id="5ede6-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ede6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ede6-112">**Cabeçalho:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="5ede6-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="5ede6-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ede6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ede6-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5ede6-114">See also</span></span>
- [<span data-ttu-id="5ede6-115">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="5ede6-115">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
