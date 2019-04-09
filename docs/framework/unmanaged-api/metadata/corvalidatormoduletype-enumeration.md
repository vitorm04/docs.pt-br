---
title: Enumeração CorValidatorModuleType
ms.date: 03/30/2017
api_name:
- CorValidatorModuleType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorValidatorModuleType
helpviewer_keywords:
- CorValidatorModuleType enumeration [.NET Framework metadata]
ms.assetid: 748f1ab2-fbcb-4f55-89ec-8d23d81ebc80
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 14eee096c25967d321e4693b260501827d944a80
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59154174"
---
# <a name="corvalidatormoduletype-enumeration"></a><span data-ttu-id="dfab7-102">Enumeração CorValidatorModuleType</span><span class="sxs-lookup"><span data-stu-id="dfab7-102">CorValidatorModuleType Enumeration</span></span>
<span data-ttu-id="dfab7-103">Especifica o tipo de um módulo.</span><span class="sxs-lookup"><span data-stu-id="dfab7-103">Specifies the type of a module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfab7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dfab7-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="dfab7-105">Membros</span><span class="sxs-lookup"><span data-stu-id="dfab7-105">Members</span></span>  
  
|<span data-ttu-id="dfab7-106">Membro</span><span class="sxs-lookup"><span data-stu-id="dfab7-106">Member</span></span>|<span data-ttu-id="dfab7-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="dfab7-107">Description</span></span>|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|<span data-ttu-id="dfab7-108">O módulo é um tipo inválido.</span><span class="sxs-lookup"><span data-stu-id="dfab7-108">The module is an invalid type.</span></span>|  
|`ValidatorModuleTypeMin`|<span data-ttu-id="dfab7-109">O valor mínimo do `CorValidatorModuleType` enum.</span><span class="sxs-lookup"><span data-stu-id="dfab7-109">The minimum value of the `CorValidatorModuleType` enum.</span></span>|  
|`ValidatorModuleTypePE`|<span data-ttu-id="dfab7-110">O módulo é um arquivo executável portátil (PE).</span><span class="sxs-lookup"><span data-stu-id="dfab7-110">The module is a portable executable (PE) file.</span></span>|  
|`ValidatorModuleTypeObj`|<span data-ttu-id="dfab7-111">O módulo é um arquivo. obj.</span><span class="sxs-lookup"><span data-stu-id="dfab7-111">The module is a .obj file.</span></span>|  
|`ValidatorModuleTypeEnc`|<span data-ttu-id="dfab7-112">O módulo é uma sessão do depurador de editar e continuar.</span><span class="sxs-lookup"><span data-stu-id="dfab7-112">The module is an edit-and-continue debugger session.</span></span>|  
|`ValidatorModuleTypeIncr`|<span data-ttu-id="dfab7-113">O módulo é aquele que foi compilado incrementalmente.</span><span class="sxs-lookup"><span data-stu-id="dfab7-113">The module is one that has been incrementally built.</span></span>|  
|`ValidatorModuleTypeMax`|<span data-ttu-id="dfab7-114">O valor máximo da `CorValidatorModuleType` enum.</span><span class="sxs-lookup"><span data-stu-id="dfab7-114">The maximum value of the `CorValidatorModuleType` enum.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dfab7-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dfab7-115">Requirements</span></span>  
 <span data-ttu-id="dfab7-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfab7-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfab7-117">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dfab7-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dfab7-118">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="dfab7-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="dfab7-119">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="dfab7-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="dfab7-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dfab7-120">See also</span></span>

- [<span data-ttu-id="dfab7-121">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="dfab7-121">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
