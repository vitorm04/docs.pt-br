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
ms.openlocfilehash: 9d6a5673c2aaf287131274b0c590f00a69c64fed
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517143"
---
# <a name="ceesectionrelocextra-union"></a><span data-ttu-id="999be-102">CeeSectionRelocExtra União</span><span class="sxs-lookup"><span data-stu-id="999be-102">CeeSectionRelocExtra Union</span></span>
<span data-ttu-id="999be-103">Representa um deslocamento de endereço que é usado pelas [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface para realocar uma seção.</span><span class="sxs-lookup"><span data-stu-id="999be-103">Represents an address offset that is used by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface to relocate a section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="999be-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="999be-104">Syntax</span></span>  
  
```  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a><span data-ttu-id="999be-105">Membros</span><span class="sxs-lookup"><span data-stu-id="999be-105">Members</span></span>  
  
|<span data-ttu-id="999be-106">Membro</span><span class="sxs-lookup"><span data-stu-id="999be-106">Member</span></span>|<span data-ttu-id="999be-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="999be-107">Description</span></span>|  
|------------|-----------------|  
|`highAdj`|<span data-ttu-id="999be-108">O ajuste de endereço superior para a seção.</span><span class="sxs-lookup"><span data-stu-id="999be-108">The upper address adjustment for the section.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="999be-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="999be-109">Requirements</span></span>  
 <span data-ttu-id="999be-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="999be-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="999be-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="999be-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="999be-112">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="999be-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="999be-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="999be-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="999be-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="999be-114">See also</span></span>
- [<span data-ttu-id="999be-115">Uniões de metadados</span><span class="sxs-lookup"><span data-stu-id="999be-115">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
