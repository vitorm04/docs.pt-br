---
title: CeeSectionRelocExtra União
ms.date: 03/30/2017
api_name:
- CeeSectionRelocExtra Union
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionRelocExtra
helpviewer_keywords:
- CeeSectionRelocExtra union [.NET Framework metadata]
ms.assetid: d9568cf6-7f98-4cd6-ab36-0a2bd509afcc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8a78a4b82d0b2064c90c938a8614b0c7594f7856
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182267"
---
# <a name="ceesectionrelocextra-union"></a><span data-ttu-id="305f4-102">CeeSectionRelocExtra União</span><span class="sxs-lookup"><span data-stu-id="305f4-102">CeeSectionRelocExtra Union</span></span>
<span data-ttu-id="305f4-103">Representa um deslocamento de endereço que é usado pelas [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface para realocar uma seção.</span><span class="sxs-lookup"><span data-stu-id="305f4-103">Represents an address offset that is used by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface to relocate a section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="305f4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="305f4-104">Syntax</span></span>  
  
```  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a><span data-ttu-id="305f4-105">Membros</span><span class="sxs-lookup"><span data-stu-id="305f4-105">Members</span></span>  
  
|<span data-ttu-id="305f4-106">Membro</span><span class="sxs-lookup"><span data-stu-id="305f4-106">Member</span></span>|<span data-ttu-id="305f4-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="305f4-107">Description</span></span>|  
|------------|-----------------|  
|`highAdj`|<span data-ttu-id="305f4-108">O ajuste de endereço superior para a seção.</span><span class="sxs-lookup"><span data-stu-id="305f4-108">The upper address adjustment for the section.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="305f4-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="305f4-109">Requirements</span></span>  
 <span data-ttu-id="305f4-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="305f4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="305f4-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="305f4-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="305f4-112">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="305f4-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="305f4-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="305f4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="305f4-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="305f4-114">See also</span></span>

- [<span data-ttu-id="305f4-115">Uniões de metadados</span><span class="sxs-lookup"><span data-stu-id="305f4-115">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
