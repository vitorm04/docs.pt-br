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
ms.openlocfilehash: 66d650adb39a9c7dade0936ec671ae5a8b4aeecd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62045453"
---
# <a name="cornativelinktype-enumeration"></a><span data-ttu-id="dc208-102">Enumeração CorNativeLinkType</span><span class="sxs-lookup"><span data-stu-id="dc208-102">CorNativeLinkType Enumeration</span></span>
<span data-ttu-id="dc208-103">Fornece valores que indicam o tipo vinculado no código nativo.</span><span class="sxs-lookup"><span data-stu-id="dc208-103">Provides values that indicate the type linked in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc208-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dc208-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="dc208-105">Membros</span><span class="sxs-lookup"><span data-stu-id="dc208-105">Members</span></span>  
  
|<span data-ttu-id="dc208-106">Membro</span><span class="sxs-lookup"><span data-stu-id="dc208-106">Member</span></span>|<span data-ttu-id="dc208-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="dc208-107">Description</span></span>|  
|------------|-----------------|  
|`nltNone`|<span data-ttu-id="dc208-108">Indica que nenhuma das palavras-chave são especificadas.</span><span class="sxs-lookup"><span data-stu-id="dc208-108">Indicates that none of the keywords are specified.</span></span>|  
|`nltAnsi`|<span data-ttu-id="dc208-109">Indica que uma palavra-chave ANSI é especificada.</span><span class="sxs-lookup"><span data-stu-id="dc208-109">Indicates that an ANSI keyword is specified.</span></span>|  
|`nltUnicode`|<span data-ttu-id="dc208-110">Indica que uma palavra-chave Unicode foi especificada</span><span class="sxs-lookup"><span data-stu-id="dc208-110">Indicates that a Unicode keyword is specified</span></span>|  
|`nltAuto`|<span data-ttu-id="dc208-111">Indica que uma palavra-chave auto é especificada.</span><span class="sxs-lookup"><span data-stu-id="dc208-111">Indicates that an auto keyword is specified.</span></span>|  
|`nltOle`|<span data-ttu-id="dc208-112">Indica que uma palavra-chave OLE é especificada.</span><span class="sxs-lookup"><span data-stu-id="dc208-112">Indicates that an OLE keyword is specified.</span></span>|  
|`nltMaxValue`|<span data-ttu-id="dc208-113">Não usado.</span><span class="sxs-lookup"><span data-stu-id="dc208-113">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dc208-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dc208-114">Requirements</span></span>  
 <span data-ttu-id="dc208-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc208-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc208-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dc208-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dc208-117">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="dc208-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dc208-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc208-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc208-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dc208-119">See also</span></span>

- [<span data-ttu-id="dc208-120">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="dc208-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
