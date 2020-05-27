---
title: Enumeração CorSerializationType
ms.date: 03/30/2017
api_name:
- CorSerializationType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSerializationType
helpviewer_keywords:
- CorSerializationType enumeration [.NET Framework metadata]
ms.assetid: 6b1fcd11-c7fb-4be2-8910-abc862d4caf4
topic_type:
- apiref
ms.openlocfilehash: 649a9159f99afa64615c40c23a98a80318ae0d7f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009165"
---
# <a name="corserializationtype-enumeration"></a><span data-ttu-id="dfeb0-102">Enumeração CorSerializationType</span><span class="sxs-lookup"><span data-stu-id="dfeb0-102">CorSerializationType Enumeration</span></span>
<span data-ttu-id="dfeb0-103">Especifica como um objeto é serializado pelo Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="dfeb0-103">Specifies how an object is serialized by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfeb0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dfeb0-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSerializationType {  
  
    SERIALIZATION_TYPE_UNDEFINED     = 0,  
    SERIALIZATION_TYPE_BOOLEAN       = ELEMENT_TYPE_BOOLEAN,  
    SERIALIZATION_TYPE_CHAR          = ELEMENT_TYPE_CHAR,  
    SERIALIZATION_TYPE_I1            = ELEMENT_TYPE_I1,  
    SERIALIZATION_TYPE_U1            = ELEMENT_TYPE_U1,  
    SERIALIZATION_TYPE_I2            = ELEMENT_TYPE_I2,  
    SERIALIZATION_TYPE_U2            = ELEMENT_TYPE_U2,  
    SERIALIZATION_TYPE_I4            = ELEMENT_TYPE_I4,  
    SERIALIZATION_TYPE_U4            = ELEMENT_TYPE_U4,  
    SERIALIZATION_TYPE_I8            = ELEMENT_TYPE_I8,  
    SERIALIZATION_TYPE_U8            = ELEMENT_TYPE_U8,  
    SERIALIZATION_TYPE_R4            = ELEMENT_TYPE_R4,  
    SERIALIZATION_TYPE_R8            = ELEMENT_TYPE_R8,  
    SERIALIZATION_TYPE_STRING        = ELEMENT_TYPE_STRING,  
    SERIALIZATION_TYPE_SZARRAY       = ELEMENT_TYPE_SZARRAY,  
    SERIALIZATION_TYPE_TYPE          = 0x50,  
    SERIALIZATION_TYPE_TAGGED_OBJECT = 0x51,  
    SERIALIZATION_TYPE_FIELD         = 0x53,  
    SERIALIZATION_TYPE_PROPERTY      = 0x54,  
    SERIALIZATION_TYPE_ENUM          = 0x55  
  
} CorSerializationType;  
```  
  
## <a name="members"></a><span data-ttu-id="dfeb0-105">Membros</span><span class="sxs-lookup"><span data-stu-id="dfeb0-105">Members</span></span>  
  
|<span data-ttu-id="dfeb0-106">Membro</span><span class="sxs-lookup"><span data-stu-id="dfeb0-106">Member</span></span>|<span data-ttu-id="dfeb0-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="dfeb0-107">Description</span></span>|  
|------------|-----------------|  
|`SERIALIZATION_TYPE_UNDEFINED`|<span data-ttu-id="dfeb0-108">A serialização do objeto está indefinida.</span><span class="sxs-lookup"><span data-stu-id="dfeb0-108">Serialization of the object is undefined.</span></span>|  
|`SERIALIZATION_TYPE_BOOLEAN`|<span data-ttu-id="dfeb0-109">O objeto é serializado como um tipo booliano</span><span class="sxs-lookup"><span data-stu-id="dfeb0-109">Object is serialized as a Boolean type</span></span>|  
|`SERIALIZATION_TYPE_CHAR`|<span data-ttu-id="dfeb0-110">O objeto é serializado como um tipo de caractere.</span><span class="sxs-lookup"><span data-stu-id="dfeb0-110">Object is serialized as a character type.</span></span>|  
|`SERIALIZATION_TYPE_I1`|<span data-ttu-id="dfeb0-111">O objeto é serializado como um inteiro de 1 byte assinado.</span><span class="sxs-lookup"><span data-stu-id="dfeb0-111">Object is serialized as a signed 1-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U1`|<span data-ttu-id="dfeb0-112">O objeto é serializado como um inteiro de 1 byte não assinado.</span><span class="sxs-lookup"><span data-stu-id="dfeb0-112">Object is serialized as an unsigned 1-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I2`|<span data-ttu-id="dfeb0-113">O objeto é serializado como um inteiro de 2 bytes assinado.</span><span class="sxs-lookup"><span data-stu-id="dfeb0-113">Object is serialized as a signed 2-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U2`|<span data-ttu-id="dfeb0-114">O objeto é serializado como um inteiro de 2 bytes não assinado.</span><span class="sxs-lookup"><span data-stu-id="dfeb0-114">Object is serialized as an unsigned 2-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I4`|<span data-ttu-id="dfeb0-115">O objeto é serializado como um inteiro de 4 bytes assinado.</span><span class="sxs-lookup"><span data-stu-id="dfeb0-115">Object is serialized as a signed 4-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U4`|<span data-ttu-id="dfeb0-116">O objeto é serializado como um inteiro de 4 bytes não assinado.</span><span class="sxs-lookup"><span data-stu-id="dfeb0-116">Object is serialized as an unsigned 4-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I8`|<span data-ttu-id="dfeb0-117">O objeto é serializado como um inteiro de 8 bytes assinado.</span><span class="sxs-lookup"><span data-stu-id="dfeb0-117">Object is serialized as a signed 8-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U8`|<span data-ttu-id="dfeb0-118">O objeto é serializado como um inteiro de 8 bytes não assinado.</span><span class="sxs-lookup"><span data-stu-id="dfeb0-118">Object is serialized as an unsigned 8-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_R4`|<span data-ttu-id="dfeb0-119">O objeto é serializado como um ponto flutuante de 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="dfeb0-119">Object is serialized as a 4-byte floating point.</span></span>|  
|`SERIALIZATION_TYPE_R8`|<span data-ttu-id="dfeb0-120">O objeto é serializado como um ponto flutuante de 8 bytes.</span><span class="sxs-lookup"><span data-stu-id="dfeb0-120">Object is serialized as an 8-byte floating point.</span></span>|  
|`SERIALIZATION_TYPE_STRING`|<span data-ttu-id="dfeb0-121">O objeto é serializado como um tipo System. String.</span><span class="sxs-lookup"><span data-stu-id="dfeb0-121">Object is serialized as a System.String type.</span></span>|  
|`SERIALIZATION_TYPE_SZARRAY`|<span data-ttu-id="dfeb0-122">O objeto é serializado como uma matriz unidimensional de limite inferior de zero.</span><span class="sxs-lookup"><span data-stu-id="dfeb0-122">Object is serialized as a single-dimensional, zero lower-bound array.</span></span>|  
|`SERIALIZATION_TYPE_TYPE`|<span data-ttu-id="dfeb0-123">O objeto é serializado como um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="dfeb0-123">Object is serialized as a generic type.</span></span>|  
|`SERIALIZATION_TYPE_TAGGED_OBJECT`|<span data-ttu-id="dfeb0-124">O objeto é serializado como um objeto marcado.</span><span class="sxs-lookup"><span data-stu-id="dfeb0-124">Object is serialized as a tagged object.</span></span>|  
|`SERIALIZATION_TYPE_FIELD`|<span data-ttu-id="dfeb0-125">O objeto é serializado como um campo.</span><span class="sxs-lookup"><span data-stu-id="dfeb0-125">Object is serialized as a field.</span></span>|  
|`SERIALIZATION_TYPE_PROPERTY`|<span data-ttu-id="dfeb0-126">O objeto é serializado como uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="dfeb0-126">Object is serialized as a property.</span></span>|  
|`SERIALIZATION_TYPE_ENUM`|<span data-ttu-id="dfeb0-127">O objeto é serializado como uma enumeração.</span><span class="sxs-lookup"><span data-stu-id="dfeb0-127">Object is serialized as an enumeration.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dfeb0-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dfeb0-128">Requirements</span></span>  
 <span data-ttu-id="dfeb0-129">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfeb0-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfeb0-130">**Cabeçalho:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="dfeb0-130">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="dfeb0-131">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfeb0-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfeb0-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="dfeb0-132">See also</span></span>

- [<span data-ttu-id="dfeb0-133">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="dfeb0-133">Metadata Enumerations</span></span>](metadata-enumerations.md)
