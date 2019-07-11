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
ms.openlocfilehash: c2e73caa3c69090bca30c8d4a907ddb619bd0ed4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776326"
---
# <a name="ceesectionrelocextra-union"></a><span data-ttu-id="6d89b-102">CeeSectionRelocExtra União</span><span class="sxs-lookup"><span data-stu-id="6d89b-102">CeeSectionRelocExtra Union</span></span>
<span data-ttu-id="6d89b-103">Representa um deslocamento de endereço que é usado pelas [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface para realocar uma seção.</span><span class="sxs-lookup"><span data-stu-id="6d89b-103">Represents an address offset that is used by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface to relocate a section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d89b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6d89b-104">Syntax</span></span>  
  
```cpp  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a><span data-ttu-id="6d89b-105">Membros</span><span class="sxs-lookup"><span data-stu-id="6d89b-105">Members</span></span>  
  
|<span data-ttu-id="6d89b-106">Membro</span><span class="sxs-lookup"><span data-stu-id="6d89b-106">Member</span></span>|<span data-ttu-id="6d89b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d89b-107">Description</span></span>|  
|------------|-----------------|  
|`highAdj`|<span data-ttu-id="6d89b-108">O ajuste de endereço superior para a seção.</span><span class="sxs-lookup"><span data-stu-id="6d89b-108">The upper address adjustment for the section.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6d89b-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6d89b-109">Requirements</span></span>  
 <span data-ttu-id="6d89b-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d89b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d89b-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6d89b-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6d89b-112">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="6d89b-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6d89b-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d89b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d89b-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6d89b-114">See also</span></span>

- [<span data-ttu-id="6d89b-115">Uniões de metadados</span><span class="sxs-lookup"><span data-stu-id="6d89b-115">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
