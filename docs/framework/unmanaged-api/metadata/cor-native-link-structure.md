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
ms.openlocfilehash: 812b70a594b5aa933f52d36f32d96d712267ecf4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177953"
---
# <a name="cor_native_link-structure"></a><span data-ttu-id="40127-102">Estrutura COR_NATIVE_LINK</span><span class="sxs-lookup"><span data-stu-id="40127-102">COR_NATIVE_LINK Structure</span></span>
<span data-ttu-id="40127-103">Contém informações usadas para vincular código nativo.</span><span class="sxs-lookup"><span data-stu-id="40127-103">Contains information that is used to link native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40127-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="40127-104">Syntax</span></span>  
  
```cpp  
typedef struct
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a><span data-ttu-id="40127-105">Membros</span><span class="sxs-lookup"><span data-stu-id="40127-105">Members</span></span>  
  
|<span data-ttu-id="40127-106">Membro</span><span class="sxs-lookup"><span data-stu-id="40127-106">Member</span></span>|<span data-ttu-id="40127-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="40127-107">Description</span></span>|  
|------------|-----------------|  
|`m_linkType`|<span data-ttu-id="40127-108">O tipo a ser ligado em código nativo.</span><span class="sxs-lookup"><span data-stu-id="40127-108">The type to be linked in native code.</span></span> <span data-ttu-id="40127-109">Esse valor é um dos valores [cornativeLinkType.](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="40127-109">This value is one of the [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) values.</span></span>|  
|`m_flags`|<span data-ttu-id="40127-110">Sinalizadores usados pelo linker ao vincular código nativo.</span><span class="sxs-lookup"><span data-stu-id="40127-110">Flags used by the linker when linking native code.</span></span> <span data-ttu-id="40127-111">Esse valor é um dos valores [do CorNativeLinkFlags.](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="40127-111">This value is one of the [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) values.</span></span>|  
|`m_entryPoint`|<span data-ttu-id="40127-112">O token de metadados MemberRef que representa o ponto de entrada.</span><span class="sxs-lookup"><span data-stu-id="40127-112">The MemberRef metadata token that represents the entry point.</span></span> <span data-ttu-id="40127-113">O formato é `lib:entrypoint`.</span><span class="sxs-lookup"><span data-stu-id="40127-113">The format is `lib:entrypoint`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="40127-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="40127-114">Requirements</span></span>  
 <span data-ttu-id="40127-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40127-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40127-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="40127-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="40127-117">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="40127-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="40127-118">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40127-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40127-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="40127-119">See also</span></span>

- [<span data-ttu-id="40127-120">Estruturas de metadados</span><span class="sxs-lookup"><span data-stu-id="40127-120">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="40127-121">Enumeração CorNativeLinkType</span><span class="sxs-lookup"><span data-stu-id="40127-121">CorNativeLinkType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)
- [<span data-ttu-id="40127-122">Enumeração CorNativeLinkFlags</span><span class="sxs-lookup"><span data-stu-id="40127-122">CorNativeLinkFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)
