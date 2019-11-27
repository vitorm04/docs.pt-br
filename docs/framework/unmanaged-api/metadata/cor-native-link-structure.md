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
ms.openlocfilehash: d03c22c455f0e44ce32d4593d9eee50ceef94a22
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443950"
---
# <a name="cor_native_link-structure"></a><span data-ttu-id="cc179-102">Estrutura COR_NATIVE_LINK</span><span class="sxs-lookup"><span data-stu-id="cc179-102">COR_NATIVE_LINK Structure</span></span>
<span data-ttu-id="cc179-103">Contém informações que são usadas para vincular código nativo.</span><span class="sxs-lookup"><span data-stu-id="cc179-103">Contains information that is used to link native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc179-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cc179-104">Syntax</span></span>  
  
```cpp  
typedef struct   
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a><span data-ttu-id="cc179-105">Membros</span><span class="sxs-lookup"><span data-stu-id="cc179-105">Members</span></span>  
  
|<span data-ttu-id="cc179-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="cc179-106">Member</span></span>|<span data-ttu-id="cc179-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="cc179-107">Description</span></span>|  
|------------|-----------------|  
|`m_linkType`|<span data-ttu-id="cc179-108">O tipo a ser vinculado em código nativo.</span><span class="sxs-lookup"><span data-stu-id="cc179-108">The type to be linked in native code.</span></span> <span data-ttu-id="cc179-109">Esse valor é um dos valores de [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="cc179-109">This value is one of the [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) values.</span></span>|  
|`m_flags`|<span data-ttu-id="cc179-110">Sinalizadores usados pelo vinculador ao vincular código nativo.</span><span class="sxs-lookup"><span data-stu-id="cc179-110">Flags used by the linker when linking native code.</span></span> <span data-ttu-id="cc179-111">Esse valor é um dos valores de [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="cc179-111">This value is one of the [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) values.</span></span>|  
|`m_entryPoint`|<span data-ttu-id="cc179-112">O token de metadados de MemberRef que representa o ponto de entrada.</span><span class="sxs-lookup"><span data-stu-id="cc179-112">The MemberRef metadata token that represents the entry point.</span></span> <span data-ttu-id="cc179-113">O formato é `lib:entrypoint`.</span><span class="sxs-lookup"><span data-stu-id="cc179-113">The format is `lib:entrypoint`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cc179-114">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="cc179-114">Requirements</span></span>  
 <span data-ttu-id="cc179-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc179-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc179-116">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="cc179-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cc179-117">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cc179-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cc179-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc179-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc179-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cc179-119">See also</span></span>

- [<span data-ttu-id="cc179-120">Estruturas de metadados</span><span class="sxs-lookup"><span data-stu-id="cc179-120">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="cc179-121">Enumeração CorNativeLinkType</span><span class="sxs-lookup"><span data-stu-id="cc179-121">CorNativeLinkType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)
- [<span data-ttu-id="cc179-122">Enumeração CorNativeLinkFlags</span><span class="sxs-lookup"><span data-stu-id="cc179-122">CorNativeLinkFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)
