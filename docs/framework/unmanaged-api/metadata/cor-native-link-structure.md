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
ms.openlocfilehash: a11b7d5939c4c20504b1ff3dfb4613f85bca0db4
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007969"
---
# <a name="cor_native_link-structure"></a><span data-ttu-id="971b1-102">Estrutura COR_NATIVE_LINK</span><span class="sxs-lookup"><span data-stu-id="971b1-102">COR_NATIVE_LINK Structure</span></span>
<span data-ttu-id="971b1-103">Contém informações que são usadas para vincular código nativo.</span><span class="sxs-lookup"><span data-stu-id="971b1-103">Contains information that is used to link native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="971b1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="971b1-104">Syntax</span></span>  
  
```cpp  
typedef struct
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a><span data-ttu-id="971b1-105">Membros</span><span class="sxs-lookup"><span data-stu-id="971b1-105">Members</span></span>  
  
|<span data-ttu-id="971b1-106">Membro</span><span class="sxs-lookup"><span data-stu-id="971b1-106">Member</span></span>|<span data-ttu-id="971b1-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="971b1-107">Description</span></span>|  
|------------|-----------------|  
|`m_linkType`|<span data-ttu-id="971b1-108">O tipo a ser vinculado em código nativo.</span><span class="sxs-lookup"><span data-stu-id="971b1-108">The type to be linked in native code.</span></span> <span data-ttu-id="971b1-109">Esse valor é um dos valores de [CorNativeLinkType](cornativelinktype-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="971b1-109">This value is one of the [CorNativeLinkType](cornativelinktype-enumeration.md) values.</span></span>|  
|`m_flags`|<span data-ttu-id="971b1-110">Sinalizadores usados pelo vinculador ao vincular código nativo.</span><span class="sxs-lookup"><span data-stu-id="971b1-110">Flags used by the linker when linking native code.</span></span> <span data-ttu-id="971b1-111">Esse valor é um dos valores de [CorNativeLinkFlags](cornativelinkflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="971b1-111">This value is one of the [CorNativeLinkFlags](cornativelinkflags-enumeration.md) values.</span></span>|  
|`m_entryPoint`|<span data-ttu-id="971b1-112">O token de metadados de MemberRef que representa o ponto de entrada.</span><span class="sxs-lookup"><span data-stu-id="971b1-112">The MemberRef metadata token that represents the entry point.</span></span> <span data-ttu-id="971b1-113">O formato é `lib:entrypoint`.</span><span class="sxs-lookup"><span data-stu-id="971b1-113">The format is `lib:entrypoint`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="971b1-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="971b1-114">Requirements</span></span>  
 <span data-ttu-id="971b1-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="971b1-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="971b1-116">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="971b1-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="971b1-117">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="971b1-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="971b1-118">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="971b1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="971b1-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="971b1-119">See also</span></span>

- [<span data-ttu-id="971b1-120">Estruturas de metadados</span><span class="sxs-lookup"><span data-stu-id="971b1-120">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="971b1-121">Enumeração CorNativeLinkType</span><span class="sxs-lookup"><span data-stu-id="971b1-121">CorNativeLinkType Enumeration</span></span>](cornativelinktype-enumeration.md)
- [<span data-ttu-id="971b1-122">Enumeração CorNativeLinkFlags</span><span class="sxs-lookup"><span data-stu-id="971b1-122">CorNativeLinkFlags Enumeration</span></span>](cornativelinkflags-enumeration.md)
