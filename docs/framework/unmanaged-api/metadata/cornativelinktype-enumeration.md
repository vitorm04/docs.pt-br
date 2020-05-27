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
ms.openlocfilehash: 29f2401e2e3faccae05ca5249fcd7d9e89aacb46
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007605"
---
# <a name="cornativelinktype-enumeration"></a><span data-ttu-id="77fff-102">Enumeração CorNativeLinkType</span><span class="sxs-lookup"><span data-stu-id="77fff-102">CorNativeLinkType Enumeration</span></span>
<span data-ttu-id="77fff-103">Fornece valores que indicam o tipo vinculado em código nativo.</span><span class="sxs-lookup"><span data-stu-id="77fff-103">Provides values that indicate the type linked in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77fff-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="77fff-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="77fff-105">Membros</span><span class="sxs-lookup"><span data-stu-id="77fff-105">Members</span></span>  
  
|<span data-ttu-id="77fff-106">Membro</span><span class="sxs-lookup"><span data-stu-id="77fff-106">Member</span></span>|<span data-ttu-id="77fff-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="77fff-107">Description</span></span>|  
|------------|-----------------|  
|`nltNone`|<span data-ttu-id="77fff-108">Indica que nenhuma das palavras-chave está especificada.</span><span class="sxs-lookup"><span data-stu-id="77fff-108">Indicates that none of the keywords are specified.</span></span>|  
|`nltAnsi`|<span data-ttu-id="77fff-109">Indica que uma palavra-chave ANSI está especificada.</span><span class="sxs-lookup"><span data-stu-id="77fff-109">Indicates that an ANSI keyword is specified.</span></span>|  
|`nltUnicode`|<span data-ttu-id="77fff-110">Indica que uma palavra-chave Unicode está especificada</span><span class="sxs-lookup"><span data-stu-id="77fff-110">Indicates that a Unicode keyword is specified</span></span>|  
|`nltAuto`|<span data-ttu-id="77fff-111">Indica que uma palavra-chave auto está especificada.</span><span class="sxs-lookup"><span data-stu-id="77fff-111">Indicates that an auto keyword is specified.</span></span>|  
|`nltOle`|<span data-ttu-id="77fff-112">Indica que uma palavra-chave OLE está especificada.</span><span class="sxs-lookup"><span data-stu-id="77fff-112">Indicates that an OLE keyword is specified.</span></span>|  
|`nltMaxValue`|<span data-ttu-id="77fff-113">Não usado.</span><span class="sxs-lookup"><span data-stu-id="77fff-113">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="77fff-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="77fff-114">Requirements</span></span>  
 <span data-ttu-id="77fff-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77fff-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77fff-116">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="77fff-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="77fff-117">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="77fff-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="77fff-118">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77fff-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77fff-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="77fff-119">See also</span></span>

- [<span data-ttu-id="77fff-120">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="77fff-120">Metadata Enumerations</span></span>](metadata-enumerations.md)
