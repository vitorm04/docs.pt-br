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
ms.openlocfilehash: 0b613ebacdff82a29fdbc3f4caa0f2b8bb5d3f6a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176156"
---
# <a name="cornativelinktype-enumeration"></a><span data-ttu-id="dd13d-102">Enumeração CorNativeLinkType</span><span class="sxs-lookup"><span data-stu-id="dd13d-102">CorNativeLinkType Enumeration</span></span>
<span data-ttu-id="dd13d-103">Fornece valores que indicam o tipo vinculado em código nativo.</span><span class="sxs-lookup"><span data-stu-id="dd13d-103">Provides values that indicate the type linked in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd13d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dd13d-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="dd13d-105">Membros</span><span class="sxs-lookup"><span data-stu-id="dd13d-105">Members</span></span>  
  
|<span data-ttu-id="dd13d-106">Membro</span><span class="sxs-lookup"><span data-stu-id="dd13d-106">Member</span></span>|<span data-ttu-id="dd13d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="dd13d-107">Description</span></span>|  
|------------|-----------------|  
|`nltNone`|<span data-ttu-id="dd13d-108">Indica que nenhuma das palavras-chave está especificada.</span><span class="sxs-lookup"><span data-stu-id="dd13d-108">Indicates that none of the keywords are specified.</span></span>|  
|`nltAnsi`|<span data-ttu-id="dd13d-109">Indica que uma palavra-chave ANSI é especificada.</span><span class="sxs-lookup"><span data-stu-id="dd13d-109">Indicates that an ANSI keyword is specified.</span></span>|  
|`nltUnicode`|<span data-ttu-id="dd13d-110">Indica que uma palavra-chave Unicode é especificada</span><span class="sxs-lookup"><span data-stu-id="dd13d-110">Indicates that a Unicode keyword is specified</span></span>|  
|`nltAuto`|<span data-ttu-id="dd13d-111">Indica que uma palavra-chave automática é especificada.</span><span class="sxs-lookup"><span data-stu-id="dd13d-111">Indicates that an auto keyword is specified.</span></span>|  
|`nltOle`|<span data-ttu-id="dd13d-112">Indica que uma palavra-chave OLE é especificada.</span><span class="sxs-lookup"><span data-stu-id="dd13d-112">Indicates that an OLE keyword is specified.</span></span>|  
|`nltMaxValue`|<span data-ttu-id="dd13d-113">Não usado.</span><span class="sxs-lookup"><span data-stu-id="dd13d-113">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dd13d-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dd13d-114">Requirements</span></span>  
 <span data-ttu-id="dd13d-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd13d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd13d-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dd13d-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dd13d-117">**Biblioteca:** Incluído como um recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dd13d-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dd13d-118">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd13d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd13d-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="dd13d-119">See also</span></span>

- [<span data-ttu-id="dd13d-120">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="dd13d-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
