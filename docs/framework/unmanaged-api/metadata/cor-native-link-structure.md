---
title: Estrutura COR_NATIVE_LINK
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- COR_NATIVE_LINK
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_NATIVE_LINK
helpviewer_keywords:
- COR_NATIVE_LINK structure [.NET Framework metadata]
ms.assetid: 6ef78d3c-1c69-4141-b687-dcb065b7a74d
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 63e5946e98e7c862a2502a71a02e605a38086618
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="cornativelink-structure"></a><span data-ttu-id="0c95b-102">Estrutura COR_NATIVE_LINK</span><span class="sxs-lookup"><span data-stu-id="0c95b-102">COR_NATIVE_LINK Structure</span></span>
<span data-ttu-id="0c95b-103">Contém informações que são usadas para vincular o código nativo.</span><span class="sxs-lookup"><span data-stu-id="0c95b-103">Contains information that is used to link native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c95b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0c95b-104">Syntax</span></span>  
  
```  
typedef struct   
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a><span data-ttu-id="0c95b-105">Membros</span><span class="sxs-lookup"><span data-stu-id="0c95b-105">Members</span></span>  
  
|<span data-ttu-id="0c95b-106">Membro</span><span class="sxs-lookup"><span data-stu-id="0c95b-106">Member</span></span>|<span data-ttu-id="0c95b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="0c95b-107">Description</span></span>|  
|------------|-----------------|  
|`m_linkType`|<span data-ttu-id="0c95b-108">O tipo a ser vinculado em código nativo.</span><span class="sxs-lookup"><span data-stu-id="0c95b-108">The type to be linked in native code.</span></span> <span data-ttu-id="0c95b-109">Esse valor é uma da [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) valores.</span><span class="sxs-lookup"><span data-stu-id="0c95b-109">This value is one of the [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) values.</span></span>|  
|`m_flags`|<span data-ttu-id="0c95b-110">Sinalizadores usados pelo vinculador ao vincular o código nativo.</span><span class="sxs-lookup"><span data-stu-id="0c95b-110">Flags used by the linker when linking native code.</span></span> <span data-ttu-id="0c95b-111">Esse valor é uma da [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) valores.</span><span class="sxs-lookup"><span data-stu-id="0c95b-111">This value is one of the [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) values.</span></span>|  
|`m_entryPoint`|<span data-ttu-id="0c95b-112">O token de metadados de MemberRef que representa o ponto de entrada.</span><span class="sxs-lookup"><span data-stu-id="0c95b-112">The MemberRef metadata token that represents the entry point.</span></span> <span data-ttu-id="0c95b-113">O formato é `lib:entrypoint`.</span><span class="sxs-lookup"><span data-stu-id="0c95b-113">The format is `lib:entrypoint`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0c95b-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0c95b-114">Requirements</span></span>  
 <span data-ttu-id="0c95b-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c95b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c95b-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0c95b-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0c95b-117">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="0c95b-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0c95b-118">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c95b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c95b-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0c95b-119">See Also</span></span>  
 [<span data-ttu-id="0c95b-120">Estruturas de metadados</span><span class="sxs-lookup"><span data-stu-id="0c95b-120">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [<span data-ttu-id="0c95b-121">Enumeração CorNativeLinkType</span><span class="sxs-lookup"><span data-stu-id="0c95b-121">CorNativeLinkType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)  
 [<span data-ttu-id="0c95b-122">Enumeração CorNativeLinkFlags</span><span class="sxs-lookup"><span data-stu-id="0c95b-122">CorNativeLinkFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)
