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
ms.openlocfilehash: 9d4690cb6adedc77717e577d409cb52b18b1b5ca
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443838"
---
# <a name="corcallingconvention-enumeration"></a><span data-ttu-id="7b128-102">Enumeração CorCallingConvention</span><span class="sxs-lookup"><span data-stu-id="7b128-102">CorCallingConvention Enumeration</span></span>
<span data-ttu-id="7b128-103">Contém valores que descrevem os tipos de convenções de chamada que são feitas em código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="7b128-103">Contains values that describe the types of calling conventions that are made in managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b128-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7b128-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="7b128-105">Membros</span><span class="sxs-lookup"><span data-stu-id="7b128-105">Members</span></span>  
  
|<span data-ttu-id="7b128-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="7b128-106">Member</span></span>|<span data-ttu-id="7b128-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="7b128-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_CS_CALLCONV_DEFAULT`|<span data-ttu-id="7b128-108">Indica uma Convenção de chamada padrão.</span><span class="sxs-lookup"><span data-stu-id="7b128-108">Indicates a default calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_VARARG`|<span data-ttu-id="7b128-109">Indica que o método usa um número variável de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="7b128-109">Indicates that the method takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FIELD`|<span data-ttu-id="7b128-110">Indica que a chamada é para um campo.</span><span class="sxs-lookup"><span data-stu-id="7b128-110">Indicates that the call is to a field.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_LOCAL_SIG`|<span data-ttu-id="7b128-111">Indica que a chamada é para um método local.</span><span class="sxs-lookup"><span data-stu-id="7b128-111">Indicates that the call is to a local method.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_PROPERTY`|<span data-ttu-id="7b128-112">Indica que a chamada é para uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="7b128-112">Indicates that the call is to a property.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_UNMGD`|<span data-ttu-id="7b128-113">Indica que a chamada não é gerenciada.</span><span class="sxs-lookup"><span data-stu-id="7b128-113">Indicates that the call is unmanaged.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERICINST`|<span data-ttu-id="7b128-114">Indica uma instanciação de método genérico.</span><span class="sxs-lookup"><span data-stu-id="7b128-114">Indicates a generic method instantiation.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_NATIVEVARARG`|<span data-ttu-id="7b128-115">Indica uma chamada de PInvoke de 64 bits para um método que usa um número variável de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="7b128-115">Indicates a 64-bit PInvoke call to a method that takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MAX`|<span data-ttu-id="7b128-116">Descreve um valor inválido de 4 bits.</span><span class="sxs-lookup"><span data-stu-id="7b128-116">Describes an invalid 4-bit value.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MASK`|<span data-ttu-id="7b128-117">Indica que a Convenção de chamada é descrita pelos quatro bits inferiores.</span><span class="sxs-lookup"><span data-stu-id="7b128-117">Indicates that the calling convention is described by the bottom four bits.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_HASTHIS`|<span data-ttu-id="7b128-118">Indica que o bit superior descreve um parâmetro `this`.</span><span class="sxs-lookup"><span data-stu-id="7b128-118">Indicates that the top bit describes a `this` parameter.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS`|<span data-ttu-id="7b128-119">Indica que um parâmetro de `this` é descrito explicitamente na assinatura.</span><span class="sxs-lookup"><span data-stu-id="7b128-119">Indicates that a `this` parameter is explicitly described in the signature.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERIC`|<span data-ttu-id="7b128-120">Indica uma assinatura de método genérico com um número explícito de argumentos de tipo.</span><span class="sxs-lookup"><span data-stu-id="7b128-120">Indicates a generic method signature with an explicit number of type arguments.</span></span> <span data-ttu-id="7b128-121">Isso precede uma contagem de parâmetros comum.</span><span class="sxs-lookup"><span data-stu-id="7b128-121">This precedes an ordinary parameter count.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7b128-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7b128-122">Requirements</span></span>  
 <span data-ttu-id="7b128-123">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b128-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b128-124">**Cabeçalho:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="7b128-124">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="7b128-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b128-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b128-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7b128-126">See also</span></span>

- [<span data-ttu-id="7b128-127">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="7b128-127">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
