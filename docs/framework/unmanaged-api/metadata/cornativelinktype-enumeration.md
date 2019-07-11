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
ms.openlocfilehash: 944c641c39ddef7add0e9f382dc7d35068668455
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781725"
---
# <a name="cornativelinktype-enumeration"></a><span data-ttu-id="12021-102">Enumeração CorNativeLinkType</span><span class="sxs-lookup"><span data-stu-id="12021-102">CorNativeLinkType Enumeration</span></span>
<span data-ttu-id="12021-103">Fornece valores que indicam o tipo vinculado no código nativo.</span><span class="sxs-lookup"><span data-stu-id="12021-103">Provides values that indicate the type linked in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12021-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="12021-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="12021-105">Membros</span><span class="sxs-lookup"><span data-stu-id="12021-105">Members</span></span>  
  
|<span data-ttu-id="12021-106">Membro</span><span class="sxs-lookup"><span data-stu-id="12021-106">Member</span></span>|<span data-ttu-id="12021-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="12021-107">Description</span></span>|  
|------------|-----------------|  
|`nltNone`|<span data-ttu-id="12021-108">Indica que nenhuma das palavras-chave são especificadas.</span><span class="sxs-lookup"><span data-stu-id="12021-108">Indicates that none of the keywords are specified.</span></span>|  
|`nltAnsi`|<span data-ttu-id="12021-109">Indica que uma palavra-chave ANSI é especificada.</span><span class="sxs-lookup"><span data-stu-id="12021-109">Indicates that an ANSI keyword is specified.</span></span>|  
|`nltUnicode`|<span data-ttu-id="12021-110">Indica que uma palavra-chave Unicode foi especificada</span><span class="sxs-lookup"><span data-stu-id="12021-110">Indicates that a Unicode keyword is specified</span></span>|  
|`nltAuto`|<span data-ttu-id="12021-111">Indica que uma palavra-chave auto é especificada.</span><span class="sxs-lookup"><span data-stu-id="12021-111">Indicates that an auto keyword is specified.</span></span>|  
|`nltOle`|<span data-ttu-id="12021-112">Indica que uma palavra-chave OLE é especificada.</span><span class="sxs-lookup"><span data-stu-id="12021-112">Indicates that an OLE keyword is specified.</span></span>|  
|`nltMaxValue`|<span data-ttu-id="12021-113">Não usado.</span><span class="sxs-lookup"><span data-stu-id="12021-113">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="12021-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="12021-114">Requirements</span></span>  
 <span data-ttu-id="12021-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12021-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12021-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="12021-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="12021-117">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="12021-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="12021-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12021-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12021-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="12021-119">See also</span></span>

- [<span data-ttu-id="12021-120">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="12021-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
