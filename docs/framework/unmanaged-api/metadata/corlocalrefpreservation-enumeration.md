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
ms.openlocfilehash: ee808ba403a513b897134420b45ebe8cd3537571
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442238"
---
# <a name="corlocalrefpreservation-enumeration"></a><span data-ttu-id="fe816-102">Enumeração CorLocalRefPreservation</span><span class="sxs-lookup"><span data-stu-id="fe816-102">CorLocalRefPreservation Enumeration</span></span>
<span data-ttu-id="fe816-103">Contém valores de sinalizador para o tratamento de referências de locais.</span><span class="sxs-lookup"><span data-stu-id="fe816-103">Contains flag values for the treatment of local references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe816-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fe816-104">Syntax</span></span>  
  
```  
typedef enum CorLocalRefPreservation  
{  
    MDPreserveLocalRefsNone     =   0x00000000,  
    MDPreserveLocalTypeRef      =   0x00000001,  
    MDPreserveLocalMemberRef    =   0x00000002  
} CorLocalRefPreservation;  
```  
  
## <a name="members"></a><span data-ttu-id="fe816-105">Membros</span><span class="sxs-lookup"><span data-stu-id="fe816-105">Members</span></span>  
  
|<span data-ttu-id="fe816-106">Membro</span><span class="sxs-lookup"><span data-stu-id="fe816-106">Member</span></span>|<span data-ttu-id="fe816-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="fe816-107">Description</span></span>|  
|------------|-----------------|  
|`MDPreserveLocalRefsNone`|<span data-ttu-id="fe816-108">Não preserve nenhuma referência de local.</span><span class="sxs-lookup"><span data-stu-id="fe816-108">Preserve no local references.</span></span>|  
|`MDPreserveLocalTypeRef`|<span data-ttu-id="fe816-109">Preserve as referências de tipo local.</span><span class="sxs-lookup"><span data-stu-id="fe816-109">Preserve local type references.</span></span>|  
|`MDPreserveLocalMemberRef`|<span data-ttu-id="fe816-110">Preserve referências de membro local.</span><span class="sxs-lookup"><span data-stu-id="fe816-110">Preserve local member references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fe816-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fe816-111">Requirements</span></span>  
 <span data-ttu-id="fe816-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe816-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe816-113">**Cabeçalho:** Corhdr</span><span class="sxs-lookup"><span data-stu-id="fe816-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="fe816-114">**Versões do .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe816-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe816-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fe816-115">See Also</span></span>  
 [<span data-ttu-id="fe816-116">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="fe816-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
