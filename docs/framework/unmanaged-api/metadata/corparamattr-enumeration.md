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
ms.openlocfilehash: 1d58c8c0413346536c3e61e67ca0077c08c2b387
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436493"
---
# <a name="corparamattr-enumeration"></a><span data-ttu-id="dcb11-102">Enumeração CorParamAttr</span><span class="sxs-lookup"><span data-stu-id="dcb11-102">CorParamAttr Enumeration</span></span>
<span data-ttu-id="dcb11-103">Contém valores que descrevem os metadados de um parâmetro de método.</span><span class="sxs-lookup"><span data-stu-id="dcb11-103">Contains values that describe the metadata of a method parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcb11-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dcb11-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="dcb11-105">Membros</span><span class="sxs-lookup"><span data-stu-id="dcb11-105">Members</span></span>  
  
|<span data-ttu-id="dcb11-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="dcb11-106">Member</span></span>|<span data-ttu-id="dcb11-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="dcb11-107">Description</span></span>|  
|------------|-----------------|  
|`pdIn`|<span data-ttu-id="dcb11-108">Especifica que o parâmetro é passado para a chamada de método.</span><span class="sxs-lookup"><span data-stu-id="dcb11-108">Specifies that the parameter is passed into the method call.</span></span>|  
|`pdOut`|<span data-ttu-id="dcb11-109">Especifica que o parâmetro é passado do retorno do método.</span><span class="sxs-lookup"><span data-stu-id="dcb11-109">Specifies that the parameter is passed from the method return.</span></span>|  
|`pdOptional`|<span data-ttu-id="dcb11-110">Especifica que o parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="dcb11-110">Specifies that the parameter is optional.</span></span>|  
|`pdReservedMask`|<span data-ttu-id="dcb11-111">Reservado para uso interno pelo Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="dcb11-111">Reserved for internal use by the common language runtime.</span></span>|  
|`pdHasDefault`|<span data-ttu-id="dcb11-112">Especifica que o parâmetro tem um valor padrão.</span><span class="sxs-lookup"><span data-stu-id="dcb11-112">Specifies that the parameter has a default value.</span></span>|  
|`pdHasFieldMarshal`|<span data-ttu-id="dcb11-113">Especifica que o parâmetro tem informações de marshaling.</span><span class="sxs-lookup"><span data-stu-id="dcb11-113">Specifies that the parameter has marshaling information.</span></span>|  
|`pdUnused`|<span data-ttu-id="dcb11-114">Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="dcb11-114">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dcb11-115">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="dcb11-115">Requirements</span></span>  
 <span data-ttu-id="dcb11-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcb11-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcb11-117">**Cabeçalho:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="dcb11-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="dcb11-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcb11-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcb11-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dcb11-119">See also</span></span>

- [<span data-ttu-id="dcb11-120">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="dcb11-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
