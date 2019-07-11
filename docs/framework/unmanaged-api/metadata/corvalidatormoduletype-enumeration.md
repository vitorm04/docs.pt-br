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
ms.openlocfilehash: 04bed418d96658e29328cf2ce6bba445639b437f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750763"
---
# <a name="corvalidatormoduletype-enumeration"></a><span data-ttu-id="c9d42-102">Enumeração CorValidatorModuleType</span><span class="sxs-lookup"><span data-stu-id="c9d42-102">CorValidatorModuleType Enumeration</span></span>
<span data-ttu-id="c9d42-103">Especifica o tipo de um módulo.</span><span class="sxs-lookup"><span data-stu-id="c9d42-103">Specifies the type of a module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9d42-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c9d42-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="c9d42-105">Membros</span><span class="sxs-lookup"><span data-stu-id="c9d42-105">Members</span></span>  
  
|<span data-ttu-id="c9d42-106">Membro</span><span class="sxs-lookup"><span data-stu-id="c9d42-106">Member</span></span>|<span data-ttu-id="c9d42-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9d42-107">Description</span></span>|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|<span data-ttu-id="c9d42-108">O módulo é um tipo inválido.</span><span class="sxs-lookup"><span data-stu-id="c9d42-108">The module is an invalid type.</span></span>|  
|`ValidatorModuleTypeMin`|<span data-ttu-id="c9d42-109">O valor mínimo do `CorValidatorModuleType` enum.</span><span class="sxs-lookup"><span data-stu-id="c9d42-109">The minimum value of the `CorValidatorModuleType` enum.</span></span>|  
|`ValidatorModuleTypePE`|<span data-ttu-id="c9d42-110">O módulo é um arquivo executável portátil (PE).</span><span class="sxs-lookup"><span data-stu-id="c9d42-110">The module is a portable executable (PE) file.</span></span>|  
|`ValidatorModuleTypeObj`|<span data-ttu-id="c9d42-111">O módulo é um arquivo. obj.</span><span class="sxs-lookup"><span data-stu-id="c9d42-111">The module is a .obj file.</span></span>|  
|`ValidatorModuleTypeEnc`|<span data-ttu-id="c9d42-112">O módulo é uma sessão do depurador de editar e continuar.</span><span class="sxs-lookup"><span data-stu-id="c9d42-112">The module is an edit-and-continue debugger session.</span></span>|  
|`ValidatorModuleTypeIncr`|<span data-ttu-id="c9d42-113">O módulo é aquele que foi compilado incrementalmente.</span><span class="sxs-lookup"><span data-stu-id="c9d42-113">The module is one that has been incrementally built.</span></span>|  
|`ValidatorModuleTypeMax`|<span data-ttu-id="c9d42-114">O valor máximo da `CorValidatorModuleType` enum.</span><span class="sxs-lookup"><span data-stu-id="c9d42-114">The maximum value of the `CorValidatorModuleType` enum.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c9d42-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c9d42-115">Requirements</span></span>  
 <span data-ttu-id="c9d42-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9d42-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9d42-117">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c9d42-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c9d42-118">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="c9d42-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c9d42-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9d42-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9d42-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9d42-120">See also</span></span>

- [<span data-ttu-id="c9d42-121">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="c9d42-121">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
