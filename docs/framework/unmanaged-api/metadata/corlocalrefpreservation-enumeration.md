---
title: Enumeração CorLocalRefPreservation
ms.date: 03/30/2017
api_name:
- CorLocalRefPreservation
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorLocalRefPreservation
helpviewer_keywords:
- CorLocalRefPreservation enumeration [.NET Framework metadata]
ms.assetid: 44757163-1228-4213-a4c4-d4de503cc75d
topic_type:
- apiref
ms.openlocfilehash: 706ea37101f9f961e92d8cef2cf508c1dd0d56c1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450247"
---
# <a name="corlocalrefpreservation-enumeration"></a><span data-ttu-id="1c081-102">Enumeração CorLocalRefPreservation</span><span class="sxs-lookup"><span data-stu-id="1c081-102">CorLocalRefPreservation Enumeration</span></span>
<span data-ttu-id="1c081-103">Contém valores de sinalizador para o tratamento de referências locais.</span><span class="sxs-lookup"><span data-stu-id="1c081-103">Contains flag values for the treatment of local references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c081-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1c081-104">Syntax</span></span>  
  
```cpp  
typedef enum CorLocalRefPreservation  
{  
    MDPreserveLocalRefsNone     =   0x00000000,  
    MDPreserveLocalTypeRef      =   0x00000001,  
    MDPreserveLocalMemberRef    =   0x00000002  
} CorLocalRefPreservation;  
```  
  
## <a name="members"></a><span data-ttu-id="1c081-105">Membros</span><span class="sxs-lookup"><span data-stu-id="1c081-105">Members</span></span>  
  
|<span data-ttu-id="1c081-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="1c081-106">Member</span></span>|<span data-ttu-id="1c081-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c081-107">Description</span></span>|  
|------------|-----------------|  
|`MDPreserveLocalRefsNone`|<span data-ttu-id="1c081-108">Não preservar referências locais.</span><span class="sxs-lookup"><span data-stu-id="1c081-108">Preserve no local references.</span></span>|  
|`MDPreserveLocalTypeRef`|<span data-ttu-id="1c081-109">Preserve referências de tipo local.</span><span class="sxs-lookup"><span data-stu-id="1c081-109">Preserve local type references.</span></span>|  
|`MDPreserveLocalMemberRef`|<span data-ttu-id="1c081-110">Preserve referências de membro local.</span><span class="sxs-lookup"><span data-stu-id="1c081-110">Preserve local member references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1c081-111">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="1c081-111">Requirements</span></span>  
 <span data-ttu-id="1c081-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c081-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c081-113">**Cabeçalho:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="1c081-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="1c081-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c081-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c081-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1c081-115">See also</span></span>

- [<span data-ttu-id="1c081-116">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="1c081-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
