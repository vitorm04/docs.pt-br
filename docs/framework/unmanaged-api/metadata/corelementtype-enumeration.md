---
title: Enumeração CorElementType
ms.date: 03/30/2017
api_name:
- CorElementType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorElementType
helpviewer_keywords:
- CorElementType enumeration [.NET Framework metadata]
ms.assetid: c3809c8f-1737-4f0f-9442-0c01ee689871
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6057bd48ff4fe3f852f82de2bab972d95fef138c
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68868561"
---
# <a name="corelementtype-enumeration"></a><span data-ttu-id="b8a75-102">Enumeração CorElementType</span><span class="sxs-lookup"><span data-stu-id="b8a75-102">CorElementType Enumeration</span></span>

<span data-ttu-id="b8a75-103">Especifica um Common Language Runtime <xref:System.Type>, um modificador de tipo ou informações sobre um tipo em uma assinatura de tipo de metadados.</span><span class="sxs-lookup"><span data-stu-id="b8a75-103">Specifies a common language runtime <xref:System.Type>, a type modifier, or information about a type in a metadata type signature.</span></span>

## <a name="syntax"></a><span data-ttu-id="b8a75-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b8a75-104">Syntax</span></span>

```cpp
typedef enum CorElementType {
    ELEMENT_TYPE_END            = 0x0,
    ELEMENT_TYPE_VOID           = 0x1,
    ELEMENT_TYPE_BOOLEAN        = 0x2,
    ELEMENT_TYPE_CHAR           = 0x3,
    ELEMENT_TYPE_I1             = 0x4,
    ELEMENT_TYPE_U1             = 0x5,
    ELEMENT_TYPE_I2             = 0x6,
    ELEMENT_TYPE_U2             = 0x7,
    ELEMENT_TYPE_I4             = 0x8,
    ELEMENT_TYPE_U4             = 0x9,
    ELEMENT_TYPE_I8             = 0xa,
    ELEMENT_TYPE_U8             = 0xb,
    ELEMENT_TYPE_R4             = 0xc,
    ELEMENT_TYPE_R8             = 0xd,
    ELEMENT_TYPE_STRING         = 0xe,

    ELEMENT_TYPE_PTR            = 0xf,
    ELEMENT_TYPE_BYREF          = 0x10,

    ELEMENT_TYPE_VALUETYPE      = 0x11,
    ELEMENT_TYPE_CLASS          = 0x12,
    ELEMENT_TYPE_VAR            = 0x13,
    ELEMENT_TYPE_ARRAY          = 0x14,
    ELEMENT_TYPE_GENERICINST    = 0x15,
    ELEMENT_TYPE_TYPEDBYREF     = 0x16,

    ELEMENT_TYPE_I              = 0x18,
    ELEMENT_TYPE_U              = 0x19,
    ELEMENT_TYPE_FNPTR          = 0x1B,
    ELEMENT_TYPE_OBJECT         = 0x1C,
    ELEMENT_TYPE_SZARRAY        = 0x1D,
    ELEMENT_TYPE_MVAR           = 0x1e,

    ELEMENT_TYPE_CMOD_REQD      = 0x1F,
    ELEMENT_TYPE_CMOD_OPT       = 0x20,

    ELEMENT_TYPE_INTERNAL       = 0x21,
    ELEMENT_TYPE_MAX            = 0x22,

    ELEMENT_TYPE_MODIFIER       = 0x40,
    ELEMENT_TYPE_SENTINEL       = 0x01 | ELEMENT_TYPE_MODIFIER,
    ELEMENT_TYPE_PINNED         = 0x05 | ELEMENT_TYPE_MODIFIER

} CorElementType;
```

## <a name="members"></a><span data-ttu-id="b8a75-105">Membros</span><span class="sxs-lookup"><span data-stu-id="b8a75-105">Members</span></span>

|<span data-ttu-id="b8a75-106">Membro</span><span class="sxs-lookup"><span data-stu-id="b8a75-106">Member</span></span>|<span data-ttu-id="b8a75-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b8a75-107">Description</span></span>|
|------------|-----------------|
|`ELEMENT_TYPE_END`|<span data-ttu-id="b8a75-108">Usado internamente.</span><span class="sxs-lookup"><span data-stu-id="b8a75-108">Used internally.</span></span>|
|`ELEMENT_TYPE_VOID`|<span data-ttu-id="b8a75-109">Um tipo void.</span><span class="sxs-lookup"><span data-stu-id="b8a75-109">A void type.</span></span>|
|`ELEMENT_TYPE_BOOLEAN`|<span data-ttu-id="b8a75-110">Um tipo booliano</span><span class="sxs-lookup"><span data-stu-id="b8a75-110">A Boolean type</span></span>|
|`ELEMENT_TYPE_CHAR`|<span data-ttu-id="b8a75-111">Um tipo de caractere.</span><span class="sxs-lookup"><span data-stu-id="b8a75-111">A character type.</span></span>|
|`ELEMENT_TYPE_I1`|<span data-ttu-id="b8a75-112">Um inteiro de 1 byte assinado.</span><span class="sxs-lookup"><span data-stu-id="b8a75-112">A signed 1-byte integer.</span></span>|
|`ELEMENT_TYPE_U1`|<span data-ttu-id="b8a75-113">Um inteiro de 1 byte sem sinal.</span><span class="sxs-lookup"><span data-stu-id="b8a75-113">An unsigned 1-byte integer.</span></span>|
|`ELEMENT_TYPE_I2`|<span data-ttu-id="b8a75-114">Um inteiro de 2 bytes assinado.</span><span class="sxs-lookup"><span data-stu-id="b8a75-114">A signed 2-byte integer.</span></span>|
|`ELEMENT_TYPE_U2`|<span data-ttu-id="b8a75-115">Um inteiro sem sinal de 2 bytes.</span><span class="sxs-lookup"><span data-stu-id="b8a75-115">An unsigned 2-byte integer.</span></span>|
|`ELEMENT_TYPE_I4`|<span data-ttu-id="b8a75-116">Um inteiro de 4 bytes assinado.</span><span class="sxs-lookup"><span data-stu-id="b8a75-116">A signed 4-byte integer.</span></span>|
|`ELEMENT_TYPE_U4`|<span data-ttu-id="b8a75-117">Um inteiro de 4 bytes sem sinal.</span><span class="sxs-lookup"><span data-stu-id="b8a75-117">An unsigned 4-byte integer.</span></span>|
|`ELEMENT_TYPE_I8`|<span data-ttu-id="b8a75-118">Um inteiro de 8 bytes assinado.</span><span class="sxs-lookup"><span data-stu-id="b8a75-118">A signed 8-byte integer.</span></span>|
|`ELEMENT_TYPE_U8`|<span data-ttu-id="b8a75-119">Um inteiro de 8 bytes sem sinal.</span><span class="sxs-lookup"><span data-stu-id="b8a75-119">An unsigned 8-byte integer.</span></span>|
|`ELEMENT_TYPE_R4`|<span data-ttu-id="b8a75-120">Um ponto flutuante de 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="b8a75-120">A 4-byte floating point.</span></span>|
|`ELEMENT_TYPE_R8`|<span data-ttu-id="b8a75-121">Um ponto flutuante de 8 bytes.</span><span class="sxs-lookup"><span data-stu-id="b8a75-121">An 8-byte floating point.</span></span>|
|`ELEMENT_TYPE_STRING`|<span data-ttu-id="b8a75-122">Um tipo System. String.</span><span class="sxs-lookup"><span data-stu-id="b8a75-122">A System.String type.</span></span>|
|`ELEMENT_TYPE_PTR`|<span data-ttu-id="b8a75-123">Um modificador de tipo de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="b8a75-123">A pointer type modifier.</span></span>|
|`ELEMENT_TYPE_BYREF`|<span data-ttu-id="b8a75-124">Um modificador de tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="b8a75-124">A reference type modifier.</span></span>|
|`ELEMENT_TYPE_VALUETYPE`|<span data-ttu-id="b8a75-125">Um modificador de tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="b8a75-125">A value type modifier.</span></span>|
|`ELEMENT_TYPE_CLASS`|<span data-ttu-id="b8a75-126">Um modificador de tipo de classe.</span><span class="sxs-lookup"><span data-stu-id="b8a75-126">A class type modifier.</span></span>|
|`ELEMENT_TYPE_VAR`|<span data-ttu-id="b8a75-127">Um modificador de tipo de variável de classe.</span><span class="sxs-lookup"><span data-stu-id="b8a75-127">A class variable type modifier.</span></span>|
|`ELEMENT_TYPE_ARRAY`|<span data-ttu-id="b8a75-128">Um modificador de tipo de matriz multidimensional.</span><span class="sxs-lookup"><span data-stu-id="b8a75-128">A multi-dimensional array type modifier.</span></span>|
|`ELEMENT_TYPE_GENERICINST`|<span data-ttu-id="b8a75-129">Um modificador de tipo para tipos genéricos.</span><span class="sxs-lookup"><span data-stu-id="b8a75-129">A type modifier for generic types.</span></span>|
|`ELEMENT_TYPE_TYPEDBYREF`|<span data-ttu-id="b8a75-130">Uma referência com tipo.</span><span class="sxs-lookup"><span data-stu-id="b8a75-130">A typed reference.</span></span>|
|`ELEMENT_TYPE_I`|<span data-ttu-id="b8a75-131">Tamanho de um inteiro nativo.</span><span class="sxs-lookup"><span data-stu-id="b8a75-131">Size of a native integer.</span></span>|
|`ELEMENT_TYPE_U`|<span data-ttu-id="b8a75-132">Tamanho de um inteiro nativo não assinado.</span><span class="sxs-lookup"><span data-stu-id="b8a75-132">Size of an unsigned native integer.</span></span>|
|`ELEMENT_TYPE_FNPTR`|<span data-ttu-id="b8a75-133">Um ponteiro para uma função.</span><span class="sxs-lookup"><span data-stu-id="b8a75-133">A pointer to a function.</span></span>|
|`ELEMENT_TYPE_OBJECT`|<span data-ttu-id="b8a75-134">Um tipo System. Object.</span><span class="sxs-lookup"><span data-stu-id="b8a75-134">A System.Object type.</span></span>|
|`ELEMENT_TYPE_SZARRAY`|<span data-ttu-id="b8a75-135">Um modificador de tipo de matriz de limite inferior de zero unidimensional.</span><span class="sxs-lookup"><span data-stu-id="b8a75-135">A single-dimensional, zero lower-bound array type modifier.</span></span>|
|`ELEMENT_TYPE_MVAR`|<span data-ttu-id="b8a75-136">Um modificador de tipo de variável de método.</span><span class="sxs-lookup"><span data-stu-id="b8a75-136">A method variable type modifier.</span></span>|
|`ELEMENT_TYPE_CMOD_REQD`|<span data-ttu-id="b8a75-137">Um modificador necessário de linguagem C.</span><span class="sxs-lookup"><span data-stu-id="b8a75-137">A C language required modifier.</span></span>|
|`ELEMENT_TYPE_CMOD_OPT`|<span data-ttu-id="b8a75-138">Um modificador opcional de linguagem C.</span><span class="sxs-lookup"><span data-stu-id="b8a75-138">A C language optional modifier.</span></span>|
|`ELEMENT_TYPE_INTERNAL`|<span data-ttu-id="b8a75-139">Usado internamente.</span><span class="sxs-lookup"><span data-stu-id="b8a75-139">Used internally.</span></span>|
|`ELEMENT_TYPE_MAX`|<span data-ttu-id="b8a75-140">Um tipo inválido.</span><span class="sxs-lookup"><span data-stu-id="b8a75-140">An invalid type.</span></span>|
|`ELEMENT_TYPE_MODIFIER`|<span data-ttu-id="b8a75-141">Usado internamente.</span><span class="sxs-lookup"><span data-stu-id="b8a75-141">Used internally.</span></span>|
|`ELEMENT_TYPE_SENTINEL`|<span data-ttu-id="b8a75-142">Um modificador de tipo que é um sentinela para uma lista de um número variável de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="b8a75-142">A type modifier that is a sentinel for a list of a variable number of parameters.</span></span>|
|`ELEMENT_TYPE_PINNED`|<span data-ttu-id="b8a75-143">Usado internamente.</span><span class="sxs-lookup"><span data-stu-id="b8a75-143">Used internally.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b8a75-144">Comentários</span><span class="sxs-lookup"><span data-stu-id="b8a75-144">Remarks</span></span>

<span data-ttu-id="b8a75-145">Os modificadores de tipo formam a base para representar tipos mais complexos.</span><span class="sxs-lookup"><span data-stu-id="b8a75-145">The type modifiers form the basis for representing more complex types.</span></span> <span data-ttu-id="b8a75-146">Um `CorElementType` valor de modificador de tipo é aplicado ao valor que imediatamente o segue na assinatura de tipo.</span><span class="sxs-lookup"><span data-stu-id="b8a75-146">A `CorElementType` type modifier value is applied to the value that immediately follows it in the type signature.</span></span> <span data-ttu-id="b8a75-147">O valor que segue o `CorElementType` valor do modificador de tipo `CorElementType` pode ser um valor de tipo simples, um token de metadados ou outro valor, conforme especificado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="b8a75-147">The value that follows the `CorElementType` type modifier value can be a `CorElementType` simple type value, a metadata token, or other value, as specified in the following table.</span></span>

> [!NOTE]
> <span data-ttu-id="b8a75-148">Todos os números (*número*, *contagem de argumentos*, token de *metadados*, *classificação*, *contagem*e *associado*) são armazenados como inteiros compactados.</span><span class="sxs-lookup"><span data-stu-id="b8a75-148">All numbers (*number*, *argument Count*, *metadata token*, *rank*, *count*, and *bound*) are stored as compressed integers.</span></span> <span data-ttu-id="b8a75-149">Consulte [Standard ECMA-335-Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=116487) no site da ECMA para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="b8a75-149">See [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=116487) on the ECMA Web site for details.</span></span>

|<span data-ttu-id="b8a75-150">Modificador de tipo</span><span class="sxs-lookup"><span data-stu-id="b8a75-150">Type modifier</span></span>|<span data-ttu-id="b8a75-151">Formatar</span><span class="sxs-lookup"><span data-stu-id="b8a75-151">Format</span></span>|
|-------------------|------------|
|`ELEMENT_TYPE_PTR`|<span data-ttu-id="b8a75-152">ELEMENT_TYPE_PTR \< um`CorElementType` valor ></span><span class="sxs-lookup"><span data-stu-id="b8a75-152">ELEMENT_TYPE_PTR \<a `CorElementType` value></span></span>|
|`ELEMENT_TYPE_BYREF`|<span data-ttu-id="b8a75-153">ELEMENT_TYPE_BYREF \< um`CorElementType` valor ></span><span class="sxs-lookup"><span data-stu-id="b8a75-153">ELEMENT_TYPE_BYREF \<a `CorElementType` value></span></span>|
|`ELEMENT_TYPE_VALUETYPE`|<span data-ttu-id="b8a75-154">ELEMENT_TYPE_VALUETYPE \<um `mdTypeDef` token de metadados ></span><span class="sxs-lookup"><span data-stu-id="b8a75-154">ELEMENT_TYPE_VALUETYPE \<an `mdTypeDef` metadata token></span></span>|
|`ELEMENT_TYPE_CLASS`|<span data-ttu-id="b8a75-155">ELEMENT_TYPE_CLASS \<um `mdTypeDef` token de metadados ></span><span class="sxs-lookup"><span data-stu-id="b8a75-155">ELEMENT_TYPE_CLASS \<an `mdTypeDef` metadata token></span></span>|
|`ELEMENT_TYPE_VAR`|<span data-ttu-id="b8a75-156">Número \<de ELEMENT_TYPE_VAR ></span><span class="sxs-lookup"><span data-stu-id="b8a75-156">ELEMENT_TYPE_VAR \<number></span></span>|
|`ELEMENT_TYPE_ARRAY`|<span data-ttu-id="b8a75-157">ELEMENT_TYPE_ARRAY \<um `CorElementType` valor > \<Rank > \<count1 >\<bound1 >... \<contagem >\<> associadas</span><span class="sxs-lookup"><span data-stu-id="b8a75-157">ELEMENT_TYPE_ARRAY \<a `CorElementType` value> \<rank> \<count1> \<bound1> ... \<countN> \<boundN></span></span>|
|`ELEMENT_TYPE_GENERICINST`|<span data-ttu-id="b8a75-158">ELEMENT_TYPE_GENERICINST \<um `mdTypeDef` token de metadados \<> contagem de \<argumentos > arg1 >... \<> argN</span><span class="sxs-lookup"><span data-stu-id="b8a75-158">ELEMENT_TYPE_GENERICINST \<an `mdTypeDef` metadata token> \<argument Count> \<arg1> ... \<argN></span></span>|
|`ELEMENT_TYPE_FNPTR`|<span data-ttu-id="b8a75-159">ELEMENT_TYPE_FNPTR \<a assinatura completa para a função, incluindo a Convenção de chamada ></span><span class="sxs-lookup"><span data-stu-id="b8a75-159">ELEMENT_TYPE_FNPTR \<complete signature for the function, including calling convention></span></span>|
|`ELEMENT_TYPE_SZARRAY`|<span data-ttu-id="b8a75-160">ELEMENT_TYPE_SZARRAY \< um`CorElementType` valor ></span><span class="sxs-lookup"><span data-stu-id="b8a75-160">ELEMENT_TYPE_SZARRAY \<a `CorElementType` value></span></span>|
|`ELEMENT_TYPE_MVAR`|<span data-ttu-id="b8a75-161">Número \<de ELEMENT_TYPE_MVAR ></span><span class="sxs-lookup"><span data-stu-id="b8a75-161">ELEMENT_TYPE_MVAR \<number></span></span>|
|`ELEMENT_TYPE_CMOD_REQD`|<span data-ttu-id="b8a75-162">ELEMENT_TYPE_\<um `mdTypeRef` token `mdTypeDef` de metadados ou ></span><span class="sxs-lookup"><span data-stu-id="b8a75-162">ELEMENT_TYPE_\<a `mdTypeRef` or `mdTypeDef` metadata token></span></span>|
|`ELEMENT_TYPE_CMOD_OPT`|<span data-ttu-id="b8a75-163">E_T_CMOD_OPT \<um `mdTypeRef` token `mdTypeDef` de metadados ou ></span><span class="sxs-lookup"><span data-stu-id="b8a75-163">E_T_CMOD_OPT \<a `mdTypeRef` or `mdTypeDef` metadata token></span></span>|

## <a name="requirements"></a><span data-ttu-id="b8a75-164">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b8a75-164">Requirements</span></span>

<span data-ttu-id="b8a75-165">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8a75-165">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="b8a75-166">**Cabeçalho:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="b8a75-166">**Header:** CorHdr.h</span></span>

<span data-ttu-id="b8a75-167">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8a75-167">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="b8a75-168">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8a75-168">See also</span></span>

- [<span data-ttu-id="b8a75-169">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="b8a75-169">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
