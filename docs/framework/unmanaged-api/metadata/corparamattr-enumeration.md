---
title: Enumeração CorParamAttr
ms.date: 03/30/2017
api_name:
- CorParamAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorParamAttr
helpviewer_keywords:
- CorParamAttr enumeration [.NET Framework metadata]
ms.assetid: a7ff90ad-dad8-48e8-917d-4aa9a118cbc8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bfa8f1b5df76c7fdfe2f25b637b157bfa4424f7a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781663"
---
# <a name="corparamattr-enumeration"></a><span data-ttu-id="2a3bf-102">Enumeração CorParamAttr</span><span class="sxs-lookup"><span data-stu-id="2a3bf-102">CorParamAttr Enumeration</span></span>
<span data-ttu-id="2a3bf-103">Contém valores que descrevem os metadados de um parâmetro de método.</span><span class="sxs-lookup"><span data-stu-id="2a3bf-103">Contains values that describe the metadata of a method parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a3bf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2a3bf-104">Syntax</span></span>  
  
```cpp  
typedef enum CorParamAttr {  
  
    pdIn                        =   0x0001,  
    pdOut                       =   0x0002,  
    pdOptional                  =   0x0010,  
  
    pdReservedMask              =   0xf000,  
    pdHasDefault                =   0x1000,  
    pdHasFieldMarshal           =   0x2000,  
  
    pdUnused                    =   0xcfe0  
  
} CorParamAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="2a3bf-105">Membros</span><span class="sxs-lookup"><span data-stu-id="2a3bf-105">Members</span></span>  
  
|<span data-ttu-id="2a3bf-106">Membro</span><span class="sxs-lookup"><span data-stu-id="2a3bf-106">Member</span></span>|<span data-ttu-id="2a3bf-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a3bf-107">Description</span></span>|  
|------------|-----------------|  
|`pdIn`|<span data-ttu-id="2a3bf-108">Especifica que o parâmetro é passado para a chamada de método.</span><span class="sxs-lookup"><span data-stu-id="2a3bf-108">Specifies that the parameter is passed into the method call.</span></span>|  
|`pdOut`|<span data-ttu-id="2a3bf-109">Especifica se o parâmetro é passado do método de retorno.</span><span class="sxs-lookup"><span data-stu-id="2a3bf-109">Specifies that the parameter is passed from the method return.</span></span>|  
|`pdOptional`|<span data-ttu-id="2a3bf-110">Especifica que o parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="2a3bf-110">Specifies that the parameter is optional.</span></span>|  
|`pdReservedMask`|<span data-ttu-id="2a3bf-111">Reservado para uso interno pelo common language runtime.</span><span class="sxs-lookup"><span data-stu-id="2a3bf-111">Reserved for internal use by the common language runtime.</span></span>|  
|`pdHasDefault`|<span data-ttu-id="2a3bf-112">Especifica que o parâmetro tem um valor padrão.</span><span class="sxs-lookup"><span data-stu-id="2a3bf-112">Specifies that the parameter has a default value.</span></span>|  
|`pdHasFieldMarshal`|<span data-ttu-id="2a3bf-113">Especifica que o parâmetro tem informações de marshaling.</span><span class="sxs-lookup"><span data-stu-id="2a3bf-113">Specifies that the parameter has marshaling information.</span></span>|  
|`pdUnused`|<span data-ttu-id="2a3bf-114">Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2a3bf-114">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2a3bf-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2a3bf-115">Requirements</span></span>  
 <span data-ttu-id="2a3bf-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a3bf-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a3bf-117">**Cabeçalho:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="2a3bf-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="2a3bf-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a3bf-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a3bf-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a3bf-119">See also</span></span>

- [<span data-ttu-id="2a3bf-120">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="2a3bf-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
