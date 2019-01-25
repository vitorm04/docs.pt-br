---
title: Enumeração CorNativeLinkType
ms.date: 03/30/2017
api_name:
- CorNativeLinkType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeLinkType
helpviewer_keywords:
- CorNativeLinkType enumeration [.NET Framework metadata]
ms.assetid: 4f86ff37-2dab-4e64-819a-76b3bfe828ff
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0f946179fc31adebc8e8fc67c394e0b55a876f49
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54641324"
---
# <a name="cornativelinktype-enumeration"></a><span data-ttu-id="9572c-102">Enumeração CorNativeLinkType</span><span class="sxs-lookup"><span data-stu-id="9572c-102">CorNativeLinkType Enumeration</span></span>
<span data-ttu-id="9572c-103">Fornece valores que indicam o tipo vinculado no código nativo.</span><span class="sxs-lookup"><span data-stu-id="9572c-103">Provides values that indicate the type linked in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9572c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9572c-104">Syntax</span></span>  
  
```  
typedef enum   
{  
    nltNone       = 1,  
    nltAnsi       = 2,  
    nltUnicode    = 3,  
    nltAuto       = 4,  
    nltOle        = 5,  
    nltMaxValue   = 7  
} CorNativeLinkType;  
```  
  
## <a name="members"></a><span data-ttu-id="9572c-105">Membros</span><span class="sxs-lookup"><span data-stu-id="9572c-105">Members</span></span>  
  
|<span data-ttu-id="9572c-106">Membro</span><span class="sxs-lookup"><span data-stu-id="9572c-106">Member</span></span>|<span data-ttu-id="9572c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9572c-107">Description</span></span>|  
|------------|-----------------|  
|`nltNone`|<span data-ttu-id="9572c-108">Indica que nenhuma das palavras-chave são especificadas.</span><span class="sxs-lookup"><span data-stu-id="9572c-108">Indicates that none of the keywords are specified.</span></span>|  
|`nltAnsi`|<span data-ttu-id="9572c-109">Indica que uma palavra-chave ANSI é especificada.</span><span class="sxs-lookup"><span data-stu-id="9572c-109">Indicates that an ANSI keyword is specified.</span></span>|  
|`nltUnicode`|<span data-ttu-id="9572c-110">Indica que uma palavra-chave Unicode foi especificada</span><span class="sxs-lookup"><span data-stu-id="9572c-110">Indicates that a Unicode keyword is specified</span></span>|  
|`nltAuto`|<span data-ttu-id="9572c-111">Indica que uma palavra-chave auto é especificada.</span><span class="sxs-lookup"><span data-stu-id="9572c-111">Indicates that an auto keyword is specified.</span></span>|  
|`nltOle`|<span data-ttu-id="9572c-112">Indica que uma palavra-chave OLE é especificada.</span><span class="sxs-lookup"><span data-stu-id="9572c-112">Indicates that an OLE keyword is specified.</span></span>|  
|`nltMaxValue`|<span data-ttu-id="9572c-113">Não usado.</span><span class="sxs-lookup"><span data-stu-id="9572c-113">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9572c-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9572c-114">Requirements</span></span>  
 <span data-ttu-id="9572c-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9572c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9572c-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9572c-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9572c-117">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="9572c-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9572c-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9572c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9572c-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9572c-119">See also</span></span>
- [<span data-ttu-id="9572c-120">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="9572c-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
