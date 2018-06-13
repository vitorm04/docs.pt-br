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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4959d595030df476f5554841c2ae3c73a86a2c31
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446653"
---
# <a name="corserializationtype-enumeration"></a><span data-ttu-id="08846-102">Enumeração CorSerializationType</span><span class="sxs-lookup"><span data-stu-id="08846-102">CorSerializationType Enumeration</span></span>
<span data-ttu-id="08846-103">Especifica como um objeto é serializado pelo common language runtime.</span><span class="sxs-lookup"><span data-stu-id="08846-103">Specifies how an object is serialized by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08846-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="08846-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="08846-105">Membros</span><span class="sxs-lookup"><span data-stu-id="08846-105">Members</span></span>  
  
|<span data-ttu-id="08846-106">Membro</span><span class="sxs-lookup"><span data-stu-id="08846-106">Member</span></span>|<span data-ttu-id="08846-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="08846-107">Description</span></span>|  
|------------|-----------------|  
|`SERIALIZATION_TYPE_UNDEFINED`|<span data-ttu-id="08846-108">A serialização do objeto é indefinida.</span><span class="sxs-lookup"><span data-stu-id="08846-108">Serialization of the object is undefined.</span></span>|  
|`SERIALIZATION_TYPE_BOOLEAN`|<span data-ttu-id="08846-109">O objeto é serializado como um tipo Boolean</span><span class="sxs-lookup"><span data-stu-id="08846-109">Object is serialized as a Boolean type</span></span>|  
|`SERIALIZATION_TYPE_CHAR`|<span data-ttu-id="08846-110">O objeto é serializado como um tipo de caractere.</span><span class="sxs-lookup"><span data-stu-id="08846-110">Object is serialized as a character type.</span></span>|  
|`SERIALIZATION_TYPE_I1`|<span data-ttu-id="08846-111">O objeto é serializado como um inteiro de 1 byte.</span><span class="sxs-lookup"><span data-stu-id="08846-111">Object is serialized as a signed 1-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U1`|<span data-ttu-id="08846-112">O objeto é serializado como um inteiro de 1 byte sem sinal.</span><span class="sxs-lookup"><span data-stu-id="08846-112">Object is serialized as an unsigned 1-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I2`|<span data-ttu-id="08846-113">O objeto é serializado como um inteiro de 2 bytes.</span><span class="sxs-lookup"><span data-stu-id="08846-113">Object is serialized as a signed 2-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U2`|<span data-ttu-id="08846-114">O objeto é serializado como um inteiro de 2 bytes sem sinal.</span><span class="sxs-lookup"><span data-stu-id="08846-114">Object is serialized as an unsigned 2-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I4`|<span data-ttu-id="08846-115">O objeto é serializado como um inteiro de 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="08846-115">Object is serialized as a signed 4-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U4`|<span data-ttu-id="08846-116">O objeto é serializado como um inteiro sem sinal de 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="08846-116">Object is serialized as an unsigned 4-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I8`|<span data-ttu-id="08846-117">O objeto é serializado como um inteiro assinado de 8 bytes.</span><span class="sxs-lookup"><span data-stu-id="08846-117">Object is serialized as a signed 8-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U8`|<span data-ttu-id="08846-118">O objeto é serializado como um inteiro não assinado de 8 bytes.</span><span class="sxs-lookup"><span data-stu-id="08846-118">Object is serialized as an unsigned 8-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_R4`|<span data-ttu-id="08846-119">O objeto é serializado como um ponto flutuante de 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="08846-119">Object is serialized as a 4-byte floating point.</span></span>|  
|`SERIALIZATION_TYPE_R8`|<span data-ttu-id="08846-120">O objeto é serializado como um ponto flutuante de 8 bytes.</span><span class="sxs-lookup"><span data-stu-id="08846-120">Object is serialized as an 8-byte floating point.</span></span>|  
|`SERIALIZATION_TYPE_STRING`|<span data-ttu-id="08846-121">O objeto é serializado como um tipo System. String.</span><span class="sxs-lookup"><span data-stu-id="08846-121">Object is serialized as a System.String type.</span></span>|  
|`SERIALIZATION_TYPE_SZARRAY`|<span data-ttu-id="08846-122">O objeto é serializado como uma única dimensão, nenhuma matriz de limite inferior.</span><span class="sxs-lookup"><span data-stu-id="08846-122">Object is serialized as a single-dimensional, zero lower-bound array.</span></span>|  
|`SERIALIZATION_TYPE_TYPE`|<span data-ttu-id="08846-123">O objeto é serializado como um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="08846-123">Object is serialized as a generic type.</span></span>|  
|`SERIALIZATION_TYPE_TAGGED_OBJECT`|<span data-ttu-id="08846-124">O objeto é serializado como um objeto marcado.</span><span class="sxs-lookup"><span data-stu-id="08846-124">Object is serialized as a tagged object.</span></span>|  
|`SERIALIZATION_TYPE_FIELD`|<span data-ttu-id="08846-125">O objeto é serializado como um campo.</span><span class="sxs-lookup"><span data-stu-id="08846-125">Object is serialized as a field.</span></span>|  
|`SERIALIZATION_TYPE_PROPERTY`|<span data-ttu-id="08846-126">O objeto é serializado como uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="08846-126">Object is serialized as a property.</span></span>|  
|`SERIALIZATION_TYPE_ENUM`|<span data-ttu-id="08846-127">O objeto é serializado como uma enumeração.</span><span class="sxs-lookup"><span data-stu-id="08846-127">Object is serialized as an enumeration.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="08846-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="08846-128">Requirements</span></span>  
 <span data-ttu-id="08846-129">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08846-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08846-130">**Cabeçalho:** Corhdr</span><span class="sxs-lookup"><span data-stu-id="08846-130">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="08846-131">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08846-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08846-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="08846-132">See Also</span></span>  
 [<span data-ttu-id="08846-133">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="08846-133">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
