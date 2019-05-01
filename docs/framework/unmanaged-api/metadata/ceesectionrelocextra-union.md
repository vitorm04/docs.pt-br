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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62043284"
---
# <a name="ceesectionrelocextra-union"></a><span data-ttu-id="e51cd-102">CeeSectionRelocExtra União</span><span class="sxs-lookup"><span data-stu-id="e51cd-102">CeeSectionRelocExtra Union</span></span>
<span data-ttu-id="e51cd-103">Representa um deslocamento de endereço que é usado pelas [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface para realocar uma seção.</span><span class="sxs-lookup"><span data-stu-id="e51cd-103">Represents an address offset that is used by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface to relocate a section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e51cd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e51cd-104">Syntax</span></span>  
  
```  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a><span data-ttu-id="e51cd-105">Membros</span><span class="sxs-lookup"><span data-stu-id="e51cd-105">Members</span></span>  
  
|<span data-ttu-id="e51cd-106">Membro</span><span class="sxs-lookup"><span data-stu-id="e51cd-106">Member</span></span>|<span data-ttu-id="e51cd-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e51cd-107">Description</span></span>|  
|------------|-----------------|  
|`highAdj`|<span data-ttu-id="e51cd-108">O ajuste de endereço superior para a seção.</span><span class="sxs-lookup"><span data-stu-id="e51cd-108">The upper address adjustment for the section.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e51cd-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e51cd-109">Requirements</span></span>  
 <span data-ttu-id="e51cd-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e51cd-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e51cd-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e51cd-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e51cd-112">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="e51cd-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e51cd-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e51cd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e51cd-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e51cd-114">See also</span></span>

- [<span data-ttu-id="e51cd-115">Uniões de metadados</span><span class="sxs-lookup"><span data-stu-id="e51cd-115">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
