---
title: "Enumeração CorValidatorModuleType"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorValidatorModuleType
api_location: mscoree.dll
api_type: COM
f1_keywords: CorValidatorModuleType
helpviewer_keywords: CorValidatorModuleType enumeration [.NET Framework metadata]
ms.assetid: 748f1ab2-fbcb-4f55-89ec-8d23d81ebc80
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: fa7ca08398358dcf00a986c356de365e9caafc4f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="corvalidatormoduletype-enumeration"></a><span data-ttu-id="d18f4-102">Enumeração CorValidatorModuleType</span><span class="sxs-lookup"><span data-stu-id="d18f4-102">CorValidatorModuleType Enumeration</span></span>
<span data-ttu-id="d18f4-103">Especifica o tipo de um módulo.</span><span class="sxs-lookup"><span data-stu-id="d18f4-103">Specifies the type of a module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d18f4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d18f4-104">Syntax</span></span>  
  
```  
typedef enum  
{  
    ValidatorModuleTypeInvalid  = 0x0,  
    ValidatorModuleTypeMin      = 0x00000001,  
    ValidatorModuleTypePE       = 0x00000001,  
    ValidatorModuleTypeObj      = 0x00000002,  
    ValidatorModuleTypeEnc      = 0x00000003,  
    ValidatorModuleTypeIncr     = 0x00000004,  
    ValidatorModuleTypeMax      = 0x00000004  
} CorValidatorModuleType;  
```  
  
## <a name="members"></a><span data-ttu-id="d18f4-105">Membros</span><span class="sxs-lookup"><span data-stu-id="d18f4-105">Members</span></span>  
  
|<span data-ttu-id="d18f4-106">Membro</span><span class="sxs-lookup"><span data-stu-id="d18f4-106">Member</span></span>|<span data-ttu-id="d18f4-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d18f4-107">Description</span></span>|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|<span data-ttu-id="d18f4-108">O módulo é um tipo inválido.</span><span class="sxs-lookup"><span data-stu-id="d18f4-108">The module is an invalid type.</span></span>|  
|`ValidatorModuleTypeMin`|<span data-ttu-id="d18f4-109">O valor mínimo do `CorValidatorModuleType` enum.</span><span class="sxs-lookup"><span data-stu-id="d18f4-109">The minimum value of the `CorValidatorModuleType` enum.</span></span>|  
|`ValidatorModuleTypePE`|<span data-ttu-id="d18f4-110">O módulo é um arquivo PE (executável portátil).</span><span class="sxs-lookup"><span data-stu-id="d18f4-110">The module is a portable executable (PE) file.</span></span>|  
|`ValidatorModuleTypeObj`|<span data-ttu-id="d18f4-111">O módulo é um arquivo. obj.</span><span class="sxs-lookup"><span data-stu-id="d18f4-111">The module is a .obj file.</span></span>|  
|`ValidatorModuleTypeEnc`|<span data-ttu-id="d18f4-112">O módulo é uma sessão do depurador edit-and-continue.</span><span class="sxs-lookup"><span data-stu-id="d18f4-112">The module is an edit-and-continue debugger session.</span></span>|  
|`ValidatorModuleTypeIncr`|<span data-ttu-id="d18f4-113">O módulo é aquele que foi criado incrementalmente.</span><span class="sxs-lookup"><span data-stu-id="d18f4-113">The module is one that has been incrementally built.</span></span>|  
|`ValidatorModuleTypeMax`|<span data-ttu-id="d18f4-114">O valor máximo de `CorValidatorModuleType` enum.</span><span class="sxs-lookup"><span data-stu-id="d18f4-114">The maximum value of the `CorValidatorModuleType` enum.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d18f4-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d18f4-115">Requirements</span></span>  
 <span data-ttu-id="d18f4-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d18f4-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d18f4-117">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d18f4-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d18f4-118">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="d18f4-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d18f4-119">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d18f4-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d18f4-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d18f4-120">See Also</span></span>  
 [<span data-ttu-id="d18f4-121">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="d18f4-121">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
