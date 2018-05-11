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
ms.openlocfilehash: c7634ec801a30aa7ba07954c1df0c3d37ec279eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="ceesectionrelocextra-union"></a><span data-ttu-id="61bd5-102">CeeSectionRelocExtra União</span><span class="sxs-lookup"><span data-stu-id="61bd5-102">CeeSectionRelocExtra Union</span></span>
<span data-ttu-id="61bd5-103">Representa um deslocamento de endereço que é usado pelo [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface para realocar uma seção.</span><span class="sxs-lookup"><span data-stu-id="61bd5-103">Represents an address offset that is used by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface to relocate a section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61bd5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="61bd5-104">Syntax</span></span>  
  
```  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a><span data-ttu-id="61bd5-105">Membros</span><span class="sxs-lookup"><span data-stu-id="61bd5-105">Members</span></span>  
  
|<span data-ttu-id="61bd5-106">Membro</span><span class="sxs-lookup"><span data-stu-id="61bd5-106">Member</span></span>|<span data-ttu-id="61bd5-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="61bd5-107">Description</span></span>|  
|------------|-----------------|  
|`highAdj`|<span data-ttu-id="61bd5-108">O ajuste de endereço superior da seção.</span><span class="sxs-lookup"><span data-stu-id="61bd5-108">The upper address adjustment for the section.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="61bd5-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="61bd5-109">Requirements</span></span>  
 <span data-ttu-id="61bd5-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61bd5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61bd5-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="61bd5-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="61bd5-112">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="61bd5-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="61bd5-113">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61bd5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61bd5-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61bd5-114">See Also</span></span>  
 [<span data-ttu-id="61bd5-115">Uniões de metadados</span><span class="sxs-lookup"><span data-stu-id="61bd5-115">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
