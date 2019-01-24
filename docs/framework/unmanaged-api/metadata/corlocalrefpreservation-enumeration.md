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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e9ed3cdac726fbdbf9ee2b33f42565d8594bc36e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54669673"
---
# <a name="corlocalrefpreservation-enumeration"></a><span data-ttu-id="d326b-102">Enumeração CorLocalRefPreservation</span><span class="sxs-lookup"><span data-stu-id="d326b-102">CorLocalRefPreservation Enumeration</span></span>
<span data-ttu-id="d326b-103">Contém valores de sinalizador para o tratamento das referências locais.</span><span class="sxs-lookup"><span data-stu-id="d326b-103">Contains flag values for the treatment of local references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d326b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d326b-104">Syntax</span></span>  
  
```  
typedef enum CorLocalRefPreservation  
{  
    MDPreserveLocalRefsNone     =   0x00000000,  
    MDPreserveLocalTypeRef      =   0x00000001,  
    MDPreserveLocalMemberRef    =   0x00000002  
} CorLocalRefPreservation;  
```  
  
## <a name="members"></a><span data-ttu-id="d326b-105">Membros</span><span class="sxs-lookup"><span data-stu-id="d326b-105">Members</span></span>  
  
|<span data-ttu-id="d326b-106">Membro</span><span class="sxs-lookup"><span data-stu-id="d326b-106">Member</span></span>|<span data-ttu-id="d326b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d326b-107">Description</span></span>|  
|------------|-----------------|  
|`MDPreserveLocalRefsNone`|<span data-ttu-id="d326b-108">Não preserve nenhuma referência local.</span><span class="sxs-lookup"><span data-stu-id="d326b-108">Preserve no local references.</span></span>|  
|`MDPreserveLocalTypeRef`|<span data-ttu-id="d326b-109">Preserve as referências de tipo local.</span><span class="sxs-lookup"><span data-stu-id="d326b-109">Preserve local type references.</span></span>|  
|`MDPreserveLocalMemberRef`|<span data-ttu-id="d326b-110">Preserve as referências de membro local.</span><span class="sxs-lookup"><span data-stu-id="d326b-110">Preserve local member references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d326b-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d326b-111">Requirements</span></span>  
 <span data-ttu-id="d326b-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d326b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d326b-113">**Cabeçalho:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="d326b-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="d326b-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d326b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d326b-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d326b-115">See also</span></span>
- [<span data-ttu-id="d326b-116">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="d326b-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
