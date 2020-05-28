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
ms.openlocfilehash: d11fefe220fdb00457cc48a6cd166673350be049
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006019"
---
# <a name="ceesectionrelocextra-union"></a><span data-ttu-id="adc94-102">CeeSectionRelocExtra União</span><span class="sxs-lookup"><span data-stu-id="adc94-102">CeeSectionRelocExtra Union</span></span>
<span data-ttu-id="adc94-103">Representa um deslocamento de endereço que é usado pela interface [ICeeGen](iceegen-interface.md) para realocar uma seção.</span><span class="sxs-lookup"><span data-stu-id="adc94-103">Represents an address offset that is used by the [ICeeGen](iceegen-interface.md) interface to relocate a section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adc94-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="adc94-104">Syntax</span></span>  
  
```cpp  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a><span data-ttu-id="adc94-105">Membros</span><span class="sxs-lookup"><span data-stu-id="adc94-105">Members</span></span>  
  
|<span data-ttu-id="adc94-106">Membro</span><span class="sxs-lookup"><span data-stu-id="adc94-106">Member</span></span>|<span data-ttu-id="adc94-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="adc94-107">Description</span></span>|  
|------------|-----------------|  
|`highAdj`|<span data-ttu-id="adc94-108">O ajuste de endereço superior para a seção.</span><span class="sxs-lookup"><span data-stu-id="adc94-108">The upper address adjustment for the section.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="adc94-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="adc94-109">Requirements</span></span>  
 <span data-ttu-id="adc94-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="adc94-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="adc94-111">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="adc94-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="adc94-112">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="adc94-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="adc94-113">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="adc94-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adc94-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="adc94-114">See also</span></span>

- [<span data-ttu-id="adc94-115">Uniões de metadados</span><span class="sxs-lookup"><span data-stu-id="adc94-115">Metadata Unions</span></span>](metadata-unions.md)
