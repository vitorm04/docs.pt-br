---
title: Estrutura COR_NATIVE_LINK
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_NATIVE_LINK
api_location: mscoree.dll
api_type: COM
f1_keywords: COR_NATIVE_LINK
helpviewer_keywords: COR_NATIVE_LINK structure [.NET Framework metadata]
ms.assetid: 6ef78d3c-1c69-4141-b687-dcb065b7a74d
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e27b66fce8a78ef0feb7ed10e77cc51fc1fe83c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="cornativelink-structure"></a><span data-ttu-id="07aef-102">Estrutura COR_NATIVE_LINK</span><span class="sxs-lookup"><span data-stu-id="07aef-102">COR_NATIVE_LINK Structure</span></span>
<span data-ttu-id="07aef-103">Contém informações que são usadas para vincular o código nativo.</span><span class="sxs-lookup"><span data-stu-id="07aef-103">Contains information that is used to link native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07aef-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="07aef-104">Syntax</span></span>  
  
```  
typedef struct   
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a><span data-ttu-id="07aef-105">Membros</span><span class="sxs-lookup"><span data-stu-id="07aef-105">Members</span></span>  
  
|<span data-ttu-id="07aef-106">Membro</span><span class="sxs-lookup"><span data-stu-id="07aef-106">Member</span></span>|<span data-ttu-id="07aef-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="07aef-107">Description</span></span>|  
|------------|-----------------|  
|`m_linkType`|<span data-ttu-id="07aef-108">O tipo a ser vinculado em código nativo.</span><span class="sxs-lookup"><span data-stu-id="07aef-108">The type to be linked in native code.</span></span> <span data-ttu-id="07aef-109">Esse valor é uma da [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) valores.</span><span class="sxs-lookup"><span data-stu-id="07aef-109">This value is one of the [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) values.</span></span>|  
|`m_flags`|<span data-ttu-id="07aef-110">Sinalizadores usados pelo vinculador ao vincular o código nativo.</span><span class="sxs-lookup"><span data-stu-id="07aef-110">Flags used by the linker when linking native code.</span></span> <span data-ttu-id="07aef-111">Esse valor é uma da [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) valores.</span><span class="sxs-lookup"><span data-stu-id="07aef-111">This value is one of the [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) values.</span></span>|  
|`m_entryPoint`|<span data-ttu-id="07aef-112">O token de metadados de MemberRef que representa o ponto de entrada.</span><span class="sxs-lookup"><span data-stu-id="07aef-112">The MemberRef metadata token that represents the entry point.</span></span> <span data-ttu-id="07aef-113">O formato é `lib:entrypoint`.</span><span class="sxs-lookup"><span data-stu-id="07aef-113">The format is `lib:entrypoint`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="07aef-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="07aef-114">Requirements</span></span>  
 <span data-ttu-id="07aef-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07aef-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07aef-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="07aef-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="07aef-117">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="07aef-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="07aef-118">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07aef-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07aef-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="07aef-119">See Also</span></span>  
 [<span data-ttu-id="07aef-120">Estruturas de metadados</span><span class="sxs-lookup"><span data-stu-id="07aef-120">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [<span data-ttu-id="07aef-121">Enumeração CorNativeLinkType</span><span class="sxs-lookup"><span data-stu-id="07aef-121">CorNativeLinkType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)  
 [<span data-ttu-id="07aef-122">Enumeração CorNativeLinkFlags</span><span class="sxs-lookup"><span data-stu-id="07aef-122">CorNativeLinkFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)
