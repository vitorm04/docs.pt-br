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
ms.openlocfilehash: 97f62b082db11a5f0bb930e33cb47acef76e7a04
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59092052"
---
# <a name="corparamattr-enumeration"></a><span data-ttu-id="a93ba-102">Enumeração CorParamAttr</span><span class="sxs-lookup"><span data-stu-id="a93ba-102">CorParamAttr Enumeration</span></span>
<span data-ttu-id="a93ba-103">Contém valores que descrevem os metadados de um parâmetro de método.</span><span class="sxs-lookup"><span data-stu-id="a93ba-103">Contains values that describe the metadata of a method parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a93ba-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a93ba-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="a93ba-105">Membros</span><span class="sxs-lookup"><span data-stu-id="a93ba-105">Members</span></span>  
  
|<span data-ttu-id="a93ba-106">Membro</span><span class="sxs-lookup"><span data-stu-id="a93ba-106">Member</span></span>|<span data-ttu-id="a93ba-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a93ba-107">Description</span></span>|  
|------------|-----------------|  
|`pdIn`|<span data-ttu-id="a93ba-108">Especifica que o parâmetro é passado para a chamada de método.</span><span class="sxs-lookup"><span data-stu-id="a93ba-108">Specifies that the parameter is passed into the method call.</span></span>|  
|`pdOut`|<span data-ttu-id="a93ba-109">Especifica se o parâmetro é passado do método de retorno.</span><span class="sxs-lookup"><span data-stu-id="a93ba-109">Specifies that the parameter is passed from the method return.</span></span>|  
|`pdOptional`|<span data-ttu-id="a93ba-110">Especifica que o parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="a93ba-110">Specifies that the parameter is optional.</span></span>|  
|`pdReservedMask`|<span data-ttu-id="a93ba-111">Reservado para uso interno pelo common language runtime.</span><span class="sxs-lookup"><span data-stu-id="a93ba-111">Reserved for internal use by the common language runtime.</span></span>|  
|`pdHasDefault`|<span data-ttu-id="a93ba-112">Especifica que o parâmetro tem um valor padrão.</span><span class="sxs-lookup"><span data-stu-id="a93ba-112">Specifies that the parameter has a default value.</span></span>|  
|`pdHasFieldMarshal`|<span data-ttu-id="a93ba-113">Especifica que o parâmetro tem informações de marshaling.</span><span class="sxs-lookup"><span data-stu-id="a93ba-113">Specifies that the parameter has marshaling information.</span></span>|  
|`pdUnused`|<span data-ttu-id="a93ba-114">Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="a93ba-114">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a93ba-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a93ba-115">Requirements</span></span>  
 <span data-ttu-id="a93ba-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a93ba-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a93ba-117">**Cabeçalho:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="a93ba-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="a93ba-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a93ba-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a93ba-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a93ba-119">See also</span></span>

- [<span data-ttu-id="a93ba-120">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="a93ba-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
