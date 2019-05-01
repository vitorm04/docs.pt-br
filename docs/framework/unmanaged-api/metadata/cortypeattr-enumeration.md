---
title: Enumeração CorTypeAttr
ms.date: 03/30/2017
api_name:
- CorTypeAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorTypeAttr
helpviewer_keywords:
- CorTypeAttr enumeration [.NET Framework metadata]
ms.assetid: 9bede0ec-5fdf-42a2-b5b7-bee64056acb6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 43e7c973ee22350f26b4f86bcc8b4c4c727291ef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62045182"
---
# <a name="cortypeattr-enumeration"></a><span data-ttu-id="9881f-102">Enumeração CorTypeAttr</span><span class="sxs-lookup"><span data-stu-id="9881f-102">CorTypeAttr Enumeration</span></span>
<span data-ttu-id="9881f-103">Contém valores que indicam o tipo de metadados.</span><span class="sxs-lookup"><span data-stu-id="9881f-103">Contains values that indicate type metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9881f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9881f-104">Syntax</span></span>  
  
```  
typedef enum CorTypeAttr {  
  
    tdVisibilityMask        =   0x00000007,  
    tdNotPublic             =   0x00000000,  
    tdPublic                =   0x00000001,  
    tdNestedPublic          =   0x00000002,  
    tdNestedPrivate         =   0x00000003,  
    tdNestedFamily          =   0x00000004,  
    tdNestedAssembly        =   0x00000005,  
    tdNestedFamANDAssem     =   0x00000006,  
    tdNestedFamORAssem      =   0x00000007,  
  
    tdLayoutMask            =   0x00000018,  
    tdAutoLayout            =   0x00000000,  
    tdSequentialLayout      =   0x00000008,  
    tdExplicitLayout        =   0x00000010,  
  
    tdClassSemanticsMask    =   0x00000020,  
    tdClass                 =   0x00000000,  
    tdInterface             =   0x00000020,  
  
    tdAbstract              =   0x00000080,  
    tdSealed                =   0x00000100,  
    tdSpecialName           =   0x00000400,  
  
    tdImport                =   0x00001000,  
    tdSerializable          =   0x00002000,  
    tdWindowsRuntime        =   0x00004000,  
  
    tdStringFormatMask      =   0x00030000,  
    tdAnsiClass             =   0x00000000,  
    tdUnicodeClass          =   0x00010000,  
    tdAutoClass             =   0x00020000,  
    tdCustomFormatClass     =   0x00030000,  
    tdCustomFormatMask      =   0x00C00000,  
  
    tdBeforeFieldInit       =   0x00100000,  
    tdForwarder             =   0x00200000,  
  
    tdReservedMask          =   0x00040800,  
    tdRTSpecialName         =   0x00000800,  
    tdHasSecurity           =   0x00040000,  
  
} CorTypeAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="9881f-105">Membros</span><span class="sxs-lookup"><span data-stu-id="9881f-105">Members</span></span>  
  
|<span data-ttu-id="9881f-106">Membro</span><span class="sxs-lookup"><span data-stu-id="9881f-106">Member</span></span>|<span data-ttu-id="9881f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9881f-107">Description</span></span>|  
|------------|-----------------|  
|`tdVisibilityMask`|<span data-ttu-id="9881f-108">Usado para obter informações de visibilidade de tipo.</span><span class="sxs-lookup"><span data-stu-id="9881f-108">Used for type visibility information.</span></span>|  
|`tdNotPublic`|<span data-ttu-id="9881f-109">Especifica que o tipo não está no escopo público.</span><span class="sxs-lookup"><span data-stu-id="9881f-109">Specifies that the type is not in public scope.</span></span>|  
|`tdPublic`|<span data-ttu-id="9881f-110">Especifica que o tipo está no escopo público.</span><span class="sxs-lookup"><span data-stu-id="9881f-110">Specifies that the type is in public scope.</span></span>|  
|`tdNestedPublic`|<span data-ttu-id="9881f-111">Especifica que o tipo está aninhado com visibilidade pública.</span><span class="sxs-lookup"><span data-stu-id="9881f-111">Specifies that the type is nested with public visibility.</span></span>|  
|`tdNestedPrivate`|<span data-ttu-id="9881f-112">Especifica que o tipo está aninhado com visibilidade privada.</span><span class="sxs-lookup"><span data-stu-id="9881f-112">Specifies that the type is nested with private visibility.</span></span>|  
|`tdNestedFamily`|<span data-ttu-id="9881f-113">Especifica que o tipo está aninhado com visibilidade de família.</span><span class="sxs-lookup"><span data-stu-id="9881f-113">Specifies that the type is nested with family visibility.</span></span>|  
|`tdNestedAssembly`|<span data-ttu-id="9881f-114">Especifica que o tipo está aninhado com visibilidade do assembly.</span><span class="sxs-lookup"><span data-stu-id="9881f-114">Specifies that the type is nested with assembly visibility.</span></span>|  
|`tdNestedFamANDAssem`|<span data-ttu-id="9881f-115">Especifica que o tipo está aninhado com visibilidade de família e assembly.</span><span class="sxs-lookup"><span data-stu-id="9881f-115">Specifies that the type is nested with family and assembly visibility.</span></span>|  
|`tdNestedFamORAssem`|<span data-ttu-id="9881f-116">Especifica que o tipo está aninhado com visibilidade de família ou assembly.</span><span class="sxs-lookup"><span data-stu-id="9881f-116">Specifies that the type is nested with family or assembly visibility.</span></span>|  
|`tdLayoutMask`|<span data-ttu-id="9881f-117">Obtém informações de layout para o tipo.</span><span class="sxs-lookup"><span data-stu-id="9881f-117">Gets layout information for the type.</span></span>|  
|`tdAutoLayout`|<span data-ttu-id="9881f-118">Especifica que os campos desse tipo são dispostos automaticamente.</span><span class="sxs-lookup"><span data-stu-id="9881f-118">Specifies that the fields of this type are laid out automatically.</span></span>|  
|`tdSequentialLayout`|<span data-ttu-id="9881f-119">Especifica que os campos desse tipo são dispostos sequencialmente.</span><span class="sxs-lookup"><span data-stu-id="9881f-119">Specifies that the fields of this type are laid out sequentially.</span></span>|  
|`tdExplicitLayout`|<span data-ttu-id="9881f-120">Especifica que o layout campo for fornecido explicitamente.</span><span class="sxs-lookup"><span data-stu-id="9881f-120">Specifies that field layout is supplied explicitly.</span></span>|  
|`tdClassSemanticsMask`|<span data-ttu-id="9881f-121">Obtém informações semânticas sobre o tipo.</span><span class="sxs-lookup"><span data-stu-id="9881f-121">Gets semantic information about the type.</span></span>|  
|`tdClass`|<span data-ttu-id="9881f-122">Especifica que o tipo é uma classe.</span><span class="sxs-lookup"><span data-stu-id="9881f-122">Specifies that the type is a class.</span></span>|  
|`tdInterface`|<span data-ttu-id="9881f-123">Especifica que o tipo é uma interface.</span><span class="sxs-lookup"><span data-stu-id="9881f-123">Specifies that the type is an interface.</span></span>|  
|`tdAbstract`|<span data-ttu-id="9881f-124">Especifica que o tipo é abstrato.</span><span class="sxs-lookup"><span data-stu-id="9881f-124">Specifies that the type is abstract.</span></span>|  
|`tdSealed`|<span data-ttu-id="9881f-125">Especifica que o tipo não pode ser estendido.</span><span class="sxs-lookup"><span data-stu-id="9881f-125">Specifies that the type cannot be extended.</span></span>|  
|`tdSpecialName`|<span data-ttu-id="9881f-126">Especifica que o nome da classe é especial.</span><span class="sxs-lookup"><span data-stu-id="9881f-126">Specifies that the class name is special.</span></span> <span data-ttu-id="9881f-127">Descreve seu nome como.</span><span class="sxs-lookup"><span data-stu-id="9881f-127">Its name describes how.</span></span>|  
|`tdImport`|<span data-ttu-id="9881f-128">Especifica que o tipo é importado.</span><span class="sxs-lookup"><span data-stu-id="9881f-128">Specifies that the type is imported.</span></span>|  
|`tdSerializable`|<span data-ttu-id="9881f-129">Especifica que o tipo é serializável.</span><span class="sxs-lookup"><span data-stu-id="9881f-129">Specifies that the type is serializable.</span></span>|  
|`tdWindowsRuntime`|<span data-ttu-id="9881f-130">Especifica que esse tipo é um [!INCLUDE[wrt](../../../../includes/wrt-md.md)] tipo.</span><span class="sxs-lookup"><span data-stu-id="9881f-130">Specifies that this type is a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] type.</span></span>|  
|`tdStringFormatMask`|<span data-ttu-id="9881f-131">Obtém informações sobre como as cadeias de caracteres são codificadas e formatadas.</span><span class="sxs-lookup"><span data-stu-id="9881f-131">Gets information about how strings are encoded and formatted.</span></span>|  
|`tdAnsiClass`|<span data-ttu-id="9881f-132">Especifica que esse tipo interpreta um LPTSTR como ANSI.</span><span class="sxs-lookup"><span data-stu-id="9881f-132">Specifies that this type interprets an LPTSTR as ANSI.</span></span>|  
|`tdUnicodeClass`|<span data-ttu-id="9881f-133">Especifica que esse tipo interpreta um LPTSTR como Unicode.</span><span class="sxs-lookup"><span data-stu-id="9881f-133">Specifies that this type interprets an LPTSTR as Unicode.</span></span>|  
|`tdAutoClass`|<span data-ttu-id="9881f-134">Especifica que esse tipo interpreta um LPTSTR automaticamente.</span><span class="sxs-lookup"><span data-stu-id="9881f-134">Specifies that this type interprets an LPTSTR automatically.</span></span>|  
|`tdCustomFormatClass`|<span data-ttu-id="9881f-135">Especifica que o tipo tem uma codificação não padrão, conforme especificado por `CustomFormatMask`.</span><span class="sxs-lookup"><span data-stu-id="9881f-135">Specifies that the type has a non-standard encoding, as specified by `CustomFormatMask`.</span></span>|  
|`tdCustomFormatMask`|<span data-ttu-id="9881f-136">Use essa máscara para obter informações de codifica não padrão para interoperabilidade nativa.</span><span class="sxs-lookup"><span data-stu-id="9881f-136">Use this mask to get non-standard encoding information for native interop.</span></span> <span data-ttu-id="9881f-137">O significado dos valores desses dois bits não está especificado.</span><span class="sxs-lookup"><span data-stu-id="9881f-137">The meaning of the values of these two bits is unspecified.</span></span>|  
|`tdBeforeFieldInit`|<span data-ttu-id="9881f-138">Especifica que o tipo deve ser inicializado antes da primeira tentativa de acessar um campo estático.</span><span class="sxs-lookup"><span data-stu-id="9881f-138">Specifies that the type must be initialized before the first attempt to access a static field.</span></span>|  
|`tdForwarder`|<span data-ttu-id="9881f-139">Especifica que o tipo é exportado e um encaminhador de tipo.</span><span class="sxs-lookup"><span data-stu-id="9881f-139">Specifies that the type is exported, and a type forwarder.</span></span>|  
|`tdReservedMask`|<span data-ttu-id="9881f-140">Este sinalizador e os sinalizadores a seguir são usados internamente pelo common language runtime.</span><span class="sxs-lookup"><span data-stu-id="9881f-140">This flag and the flags below are used internally by the common language runtime.</span></span>|  
|`tdRTSpecialName`|<span data-ttu-id="9881f-141">Especifica que o common language runtime deve verificar a codificação de nome.</span><span class="sxs-lookup"><span data-stu-id="9881f-141">Specifies that the common language runtime should check the name encoding.</span></span>|  
|`tdHasSecurity`|<span data-ttu-id="9881f-142">Especifica que o tipo tem segurança associada a ele.</span><span class="sxs-lookup"><span data-stu-id="9881f-142">Specifies that the type has security associated with it.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9881f-143">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9881f-143">Requirements</span></span>  
 <span data-ttu-id="9881f-144">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9881f-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9881f-145">**Cabeçalho:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="9881f-145">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="9881f-146">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9881f-146">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9881f-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9881f-147">See also</span></span>

- [<span data-ttu-id="9881f-148">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="9881f-148">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
