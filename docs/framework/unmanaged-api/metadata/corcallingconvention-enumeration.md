---
title: Enumeração CorCallingConvention
ms.date: 03/30/2017
api_name:
- CorCallingConvention
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCallingConvention
helpviewer_keywords:
- CorCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 69156fbf-7219-43bf-b4b8-b13f1a2fcb86
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 44a4b5903cec2249eb1e176381fe3d8e600dd5e6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62046105"
---
# <a name="corcallingconvention-enumeration"></a><span data-ttu-id="a595a-102">Enumeração CorCallingConvention</span><span class="sxs-lookup"><span data-stu-id="a595a-102">CorCallingConvention Enumeration</span></span>
<span data-ttu-id="a595a-103">Contém valores que descrevem os tipos de convenções de chamada que são feitas no código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a595a-103">Contains values that describe the types of calling conventions that are made in managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a595a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a595a-104">Syntax</span></span>  
  
```  
typedef enum CorCallingConvention  
{  
    IMAGE_CEE_CS_CALLCONV_DEFAULT       = 0x0,  
  
    IMAGE_CEE_CS_CALLCONV_VARARG        = 0x5,  
    IMAGE_CEE_CS_CALLCONV_FIELD         = 0x6,  
    IMAGE_CEE_CS_CALLCONV_LOCAL_SIG     = 0x7,  
    IMAGE_CEE_CS_CALLCONV_PROPERTY      = 0x8,  
    IMAGE_CEE_CS_CALLCONV_UNMGD         = 0x9,  
    IMAGE_CEE_CS_CALLCONV_GENERICINST   = 0xa,  
    IMAGE_CEE_CS_CALLCONV_NATIVEVARARG  = 0xb,  
    IMAGE_CEE_CS_CALLCONV_MAX           = 0xc,  
  
    IMAGE_CEE_CS_CALLCONV_MASK          = 0x0f,  
    IMAGE_CEE_CS_CALLCONV_HASTHIS       = 0x20,  
    IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS  = 0x40,  
    IMAGE_CEE_CS_CALLCONV_GENERIC       = 0x10  
  
} CorCallingConvention;  
```  
  
## <a name="members"></a><span data-ttu-id="a595a-105">Membros</span><span class="sxs-lookup"><span data-stu-id="a595a-105">Members</span></span>  
  
|<span data-ttu-id="a595a-106">Membro</span><span class="sxs-lookup"><span data-stu-id="a595a-106">Member</span></span>|<span data-ttu-id="a595a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a595a-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_CS_CALLCONV_DEFAULT`|<span data-ttu-id="a595a-108">Indica uma convenção de chamada padrão.</span><span class="sxs-lookup"><span data-stu-id="a595a-108">Indicates a default calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_VARARG`|<span data-ttu-id="a595a-109">Indica que o método utiliza um número variável de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="a595a-109">Indicates that the method takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FIELD`|<span data-ttu-id="a595a-110">Indica que a chamada é para um campo.</span><span class="sxs-lookup"><span data-stu-id="a595a-110">Indicates that the call is to a field.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_LOCAL_SIG`|<span data-ttu-id="a595a-111">Indica que a chamada é para um método de local.</span><span class="sxs-lookup"><span data-stu-id="a595a-111">Indicates that the call is to a local method.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_PROPERTY`|<span data-ttu-id="a595a-112">Indica que a chamada é para uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="a595a-112">Indicates that the call is to a property.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_UNMGD`|<span data-ttu-id="a595a-113">Indica que a chamada não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="a595a-113">Indicates that the call is unmanaged.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERICINST`|<span data-ttu-id="a595a-114">Indica uma instanciação de método genérico.</span><span class="sxs-lookup"><span data-stu-id="a595a-114">Indicates a generic method instantiation.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_NATIVEVARARG`|<span data-ttu-id="a595a-115">Indica uma chamada de PInvoke de 64 bits para um método que usa um número variável de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="a595a-115">Indicates a 64-bit PInvoke call to a method that takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MAX`|<span data-ttu-id="a595a-116">Descreve um valor inválido de 4 bits.</span><span class="sxs-lookup"><span data-stu-id="a595a-116">Describes an invalid 4-bit value.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MASK`|<span data-ttu-id="a595a-117">Indica que a convenção de chamada é descrita pelos bits inferior a quatro.</span><span class="sxs-lookup"><span data-stu-id="a595a-117">Indicates that the calling convention is described by the bottom four bits.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_HASTHIS`|<span data-ttu-id="a595a-118">Indica que o bit superior descreve um `this` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="a595a-118">Indicates that the top bit describes a `this` parameter.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS`|<span data-ttu-id="a595a-119">Indica que um `this` parâmetro é descrito explicitamente na assinatura.</span><span class="sxs-lookup"><span data-stu-id="a595a-119">Indicates that a `this` parameter is explicitly described in the signature.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERIC`|<span data-ttu-id="a595a-120">Indica uma assinatura de método genérico com um número explícito de argumentos de tipo.</span><span class="sxs-lookup"><span data-stu-id="a595a-120">Indicates a generic method signature with an explicit number of type arguments.</span></span> <span data-ttu-id="a595a-121">Isso precede uma contagem de parâmetros comuns.</span><span class="sxs-lookup"><span data-stu-id="a595a-121">This precedes an ordinary parameter count.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a595a-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a595a-122">Requirements</span></span>  
 <span data-ttu-id="a595a-123">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a595a-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a595a-124">**Cabeçalho:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="a595a-124">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="a595a-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a595a-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a595a-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a595a-126">See also</span></span>

- [<span data-ttu-id="a595a-127">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="a595a-127">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
