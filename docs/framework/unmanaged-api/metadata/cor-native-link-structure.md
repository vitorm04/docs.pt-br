---
title: Estrutura COR_NATIVE_LINK
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7024140ed9b870b5db38dba7e9b13321dd37386a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157580"
---
# <a name="cornativelink-structure"></a><span data-ttu-id="344b0-102">Estrutura COR_NATIVE_LINK</span><span class="sxs-lookup"><span data-stu-id="344b0-102">COR_NATIVE_LINK Structure</span></span>
<span data-ttu-id="344b0-103">Contém informações que são usadas para vincular o código nativo.</span><span class="sxs-lookup"><span data-stu-id="344b0-103">Contains information that is used to link native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="344b0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="344b0-104">Syntax</span></span>  
  
```  
typedef struct   
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a><span data-ttu-id="344b0-105">Membros</span><span class="sxs-lookup"><span data-stu-id="344b0-105">Members</span></span>  
  
|<span data-ttu-id="344b0-106">Membro</span><span class="sxs-lookup"><span data-stu-id="344b0-106">Member</span></span>|<span data-ttu-id="344b0-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="344b0-107">Description</span></span>|  
|------------|-----------------|  
|`m_linkType`|<span data-ttu-id="344b0-108">O tipo a ser vinculado no código nativo.</span><span class="sxs-lookup"><span data-stu-id="344b0-108">The type to be linked in native code.</span></span> <span data-ttu-id="344b0-109">Esse valor é um dos [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) valores.</span><span class="sxs-lookup"><span data-stu-id="344b0-109">This value is one of the [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) values.</span></span>|  
|`m_flags`|<span data-ttu-id="344b0-110">Sinalizadores usados pelo vinculador ao vincular o código nativo.</span><span class="sxs-lookup"><span data-stu-id="344b0-110">Flags used by the linker when linking native code.</span></span> <span data-ttu-id="344b0-111">Esse valor é um dos [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) valores.</span><span class="sxs-lookup"><span data-stu-id="344b0-111">This value is one of the [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) values.</span></span>|  
|`m_entryPoint`|<span data-ttu-id="344b0-112">O token de metadados de MemberRef que representa o ponto de entrada.</span><span class="sxs-lookup"><span data-stu-id="344b0-112">The MemberRef metadata token that represents the entry point.</span></span> <span data-ttu-id="344b0-113">O formato é `lib:entrypoint`.</span><span class="sxs-lookup"><span data-stu-id="344b0-113">The format is `lib:entrypoint`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="344b0-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="344b0-114">Requirements</span></span>  
 <span data-ttu-id="344b0-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="344b0-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="344b0-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="344b0-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="344b0-117">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="344b0-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="344b0-118">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="344b0-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="344b0-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="344b0-119">See also</span></span>

- [<span data-ttu-id="344b0-120">Estruturas de metadados</span><span class="sxs-lookup"><span data-stu-id="344b0-120">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="344b0-121">Enumeração CorNativeLinkType</span><span class="sxs-lookup"><span data-stu-id="344b0-121">CorNativeLinkType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)
- [<span data-ttu-id="344b0-122">Enumeração CorNativeLinkFlags</span><span class="sxs-lookup"><span data-stu-id="344b0-122">CorNativeLinkFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)
