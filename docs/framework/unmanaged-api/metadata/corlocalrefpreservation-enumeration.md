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
ms.openlocfilehash: 6338034d6714e8770e06ff61994fdf4433eb1684
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781785"
---
# <a name="corlocalrefpreservation-enumeration"></a><span data-ttu-id="0e7e7-102">Enumeração CorLocalRefPreservation</span><span class="sxs-lookup"><span data-stu-id="0e7e7-102">CorLocalRefPreservation Enumeration</span></span>
<span data-ttu-id="0e7e7-103">Contém valores de sinalizador para o tratamento das referências locais.</span><span class="sxs-lookup"><span data-stu-id="0e7e7-103">Contains flag values for the treatment of local references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e7e7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0e7e7-104">Syntax</span></span>  
  
```cpp  
typedef enum CorLocalRefPreservation  
{  
    MDPreserveLocalRefsNone     =   0x00000000,  
    MDPreserveLocalTypeRef      =   0x00000001,  
    MDPreserveLocalMemberRef    =   0x00000002  
} CorLocalRefPreservation;  
```  
  
## <a name="members"></a><span data-ttu-id="0e7e7-105">Membros</span><span class="sxs-lookup"><span data-stu-id="0e7e7-105">Members</span></span>  
  
|<span data-ttu-id="0e7e7-106">Membro</span><span class="sxs-lookup"><span data-stu-id="0e7e7-106">Member</span></span>|<span data-ttu-id="0e7e7-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="0e7e7-107">Description</span></span>|  
|------------|-----------------|  
|`MDPreserveLocalRefsNone`|<span data-ttu-id="0e7e7-108">Não preserve nenhuma referência local.</span><span class="sxs-lookup"><span data-stu-id="0e7e7-108">Preserve no local references.</span></span>|  
|`MDPreserveLocalTypeRef`|<span data-ttu-id="0e7e7-109">Preserve as referências de tipo local.</span><span class="sxs-lookup"><span data-stu-id="0e7e7-109">Preserve local type references.</span></span>|  
|`MDPreserveLocalMemberRef`|<span data-ttu-id="0e7e7-110">Preserve as referências de membro local.</span><span class="sxs-lookup"><span data-stu-id="0e7e7-110">Preserve local member references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0e7e7-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0e7e7-111">Requirements</span></span>  
 <span data-ttu-id="0e7e7-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e7e7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e7e7-113">**Cabeçalho:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="0e7e7-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="0e7e7-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e7e7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e7e7-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0e7e7-115">See also</span></span>

- [<span data-ttu-id="0e7e7-116">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="0e7e7-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
