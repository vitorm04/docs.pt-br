---
title: Estrutura IDENTITY_ATTRIBUTE
ms.date: 03/30/2017
api_name:
- IDENTITY_ATTRIBUTE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDENTITY_ATTRIBUTE
helpviewer_keywords:
- IDENTITY_ATTRIBUTE structure [.NET Framework fusion]
ms.assetid: 1ee7c434-9681-4fa8-badd-652cb1a9742b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e26a90b6725d53774053293c04842b761da6ab12
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717669"
---
# <a name="identityattribute-structure"></a><span data-ttu-id="09882-102">Estrutura IDENTITY_ATTRIBUTE</span><span class="sxs-lookup"><span data-stu-id="09882-102">IDENTITY_ATTRIBUTE Structure</span></span>
<span data-ttu-id="09882-103">Contém informações de atributo de metadados sobre um [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instância.</span><span class="sxs-lookup"><span data-stu-id="09882-103">Contains metadata attribute information about an [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09882-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="09882-104">Syntax</span></span>  
  
```  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a><span data-ttu-id="09882-105">Membros</span><span class="sxs-lookup"><span data-stu-id="09882-105">Members</span></span>  
  
|<span data-ttu-id="09882-106">Membro</span><span class="sxs-lookup"><span data-stu-id="09882-106">Member</span></span>|<span data-ttu-id="09882-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="09882-107">Description</span></span>|  
|------------|-----------------|  
|`pszNamespace`|<span data-ttu-id="09882-108">Um ponteiro para uma cadeia de caracteres terminada em nulo que contém o namespace que o atributo está em.</span><span class="sxs-lookup"><span data-stu-id="09882-108">A pointer to a null-terminated character string that contains the namespace the attribute is in.</span></span>|  
|`pszName`|<span data-ttu-id="09882-109">Um ponteiro para uma cadeia de caracteres terminada em nulo que contém o nome do atributo.</span><span class="sxs-lookup"><span data-stu-id="09882-109">A pointer to a null-terminated character string that contains the name of the attribute.</span></span>|  
|`pszValue`|<span data-ttu-id="09882-110">Um ponteiro para uma cadeia de caracteres terminada em nulo que contém o valor do atributo.</span><span class="sxs-lookup"><span data-stu-id="09882-110">A pointer to a null-terminated character string that contains the value of the attribute.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09882-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="09882-111">Remarks</span></span>  
 <span data-ttu-id="09882-112">O `IDENTITY_ATTRIBUTE` estrutura contém três ponteiros para cadeias de caracteres terminada em nulo.</span><span class="sxs-lookup"><span data-stu-id="09882-112">The `IDENTITY_ATTRIBUTE` structure contains three pointers to null-terminated character strings.</span></span> <span data-ttu-id="09882-113">Essas três cadeias de caracteres descrevem um atributo.</span><span class="sxs-lookup"><span data-stu-id="09882-113">These three strings describe one attribute.</span></span>  
  
 <span data-ttu-id="09882-114">Uma instância de um `IDENTITY_ATTRIBUTE` estrutura está associada uma instância de um [IDENTITY_ATTRIBUTE_BLOB](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md) estrutura.</span><span class="sxs-lookup"><span data-stu-id="09882-114">An instance of an `IDENTITY_ATTRIBUTE` structure is associated with an instance of an [IDENTITY_ATTRIBUTE_BLOB](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md) structure.</span></span> <span data-ttu-id="09882-115">O `IDENTITY_ATTRIBUTE` estrutura contém as cadeias de caracteres reais e correspondente `IDENTITY_ATTRIBUTE_BLOB` estrutura lista os deslocamentos de três cadeias de caracteres listadas no `IDENTITY_ATTRIBUTE` estrutura.</span><span class="sxs-lookup"><span data-stu-id="09882-115">The `IDENTITY_ATTRIBUTE` structure contains the actual strings, and the corresponding `IDENTITY_ATTRIBUTE_BLOB` structure lists the offsets to the three strings listed in the `IDENTITY_ATTRIBUTE` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09882-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="09882-116">Requirements</span></span>  
 <span data-ttu-id="09882-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09882-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09882-118">**Cabeçalho:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="09882-118">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="09882-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09882-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09882-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="09882-120">See also</span></span>
- [<span data-ttu-id="09882-121">Interface IDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="09882-121">IDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)
- [<span data-ttu-id="09882-122">Estrutura IDENTITY_ATTRIBUTE_BLOB</span><span class="sxs-lookup"><span data-stu-id="09882-122">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md)
- [<span data-ttu-id="09882-123">Estruturas de fusão</span><span class="sxs-lookup"><span data-stu-id="09882-123">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
