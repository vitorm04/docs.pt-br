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
ms.openlocfilehash: e8afcb972cab9757458c7032c3678d45c6418fac
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007566"
---
# <a name="corparamattr-enumeration"></a><span data-ttu-id="ffdce-102">Enumeração CorParamAttr</span><span class="sxs-lookup"><span data-stu-id="ffdce-102">CorParamAttr Enumeration</span></span>
<span data-ttu-id="ffdce-103">Contém valores que descrevem os metadados de um parâmetro de método.</span><span class="sxs-lookup"><span data-stu-id="ffdce-103">Contains values that describe the metadata of a method parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffdce-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ffdce-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="ffdce-105">Membros</span><span class="sxs-lookup"><span data-stu-id="ffdce-105">Members</span></span>  
  
|<span data-ttu-id="ffdce-106">Membro</span><span class="sxs-lookup"><span data-stu-id="ffdce-106">Member</span></span>|<span data-ttu-id="ffdce-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="ffdce-107">Description</span></span>|  
|------------|-----------------|  
|`pdIn`|<span data-ttu-id="ffdce-108">Especifica que o parâmetro é passado para a chamada de método.</span><span class="sxs-lookup"><span data-stu-id="ffdce-108">Specifies that the parameter is passed into the method call.</span></span>|  
|`pdOut`|<span data-ttu-id="ffdce-109">Especifica que o parâmetro é passado do retorno do método.</span><span class="sxs-lookup"><span data-stu-id="ffdce-109">Specifies that the parameter is passed from the method return.</span></span>|  
|`pdOptional`|<span data-ttu-id="ffdce-110">Especifica que o parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="ffdce-110">Specifies that the parameter is optional.</span></span>|  
|`pdReservedMask`|<span data-ttu-id="ffdce-111">Reservado para uso interno pelo Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="ffdce-111">Reserved for internal use by the common language runtime.</span></span>|  
|`pdHasDefault`|<span data-ttu-id="ffdce-112">Especifica que o parâmetro tem um valor padrão.</span><span class="sxs-lookup"><span data-stu-id="ffdce-112">Specifies that the parameter has a default value.</span></span>|  
|`pdHasFieldMarshal`|<span data-ttu-id="ffdce-113">Especifica que o parâmetro tem informações de marshaling.</span><span class="sxs-lookup"><span data-stu-id="ffdce-113">Specifies that the parameter has marshaling information.</span></span>|  
|`pdUnused`|<span data-ttu-id="ffdce-114">Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="ffdce-114">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ffdce-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ffdce-115">Requirements</span></span>  
 <span data-ttu-id="ffdce-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffdce-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffdce-117">**Cabeçalho:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="ffdce-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="ffdce-118">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffdce-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffdce-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="ffdce-119">See also</span></span>

- [<span data-ttu-id="ffdce-120">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="ffdce-120">Metadata Enumerations</span></span>](metadata-enumerations.md)
