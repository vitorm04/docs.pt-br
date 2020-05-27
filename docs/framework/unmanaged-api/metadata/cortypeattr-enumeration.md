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
ms.openlocfilehash: b6936081ca3dbadb4f802a6856fafb53f6cef3fa
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008957"
---
# <a name="cortypeattr-enumeration"></a><span data-ttu-id="7d50d-102">Enumeração CorTypeAttr</span><span class="sxs-lookup"><span data-stu-id="7d50d-102">CorTypeAttr Enumeration</span></span>
<span data-ttu-id="7d50d-103">Contém valores que indicam metadados de tipo.</span><span class="sxs-lookup"><span data-stu-id="7d50d-103">Contains values that indicate type metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d50d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7d50d-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="7d50d-105">Membros</span><span class="sxs-lookup"><span data-stu-id="7d50d-105">Members</span></span>  
  
|<span data-ttu-id="7d50d-106">Membro</span><span class="sxs-lookup"><span data-stu-id="7d50d-106">Member</span></span>|<span data-ttu-id="7d50d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="7d50d-107">Description</span></span>|  
|------------|-----------------|  
|`tdVisibilityMask`|<span data-ttu-id="7d50d-108">Usado para informações de visibilidade de tipo.</span><span class="sxs-lookup"><span data-stu-id="7d50d-108">Used for type visibility information.</span></span>|  
|`tdNotPublic`|<span data-ttu-id="7d50d-109">Especifica que o tipo não está no escopo público.</span><span class="sxs-lookup"><span data-stu-id="7d50d-109">Specifies that the type is not in public scope.</span></span>|  
|`tdPublic`|<span data-ttu-id="7d50d-110">Especifica que o tipo está no escopo público.</span><span class="sxs-lookup"><span data-stu-id="7d50d-110">Specifies that the type is in public scope.</span></span>|  
|`tdNestedPublic`|<span data-ttu-id="7d50d-111">Especifica que o tipo é aninhado com visibilidade pública.</span><span class="sxs-lookup"><span data-stu-id="7d50d-111">Specifies that the type is nested with public visibility.</span></span>|  
|`tdNestedPrivate`|<span data-ttu-id="7d50d-112">Especifica que o tipo é aninhado com visibilidade privada.</span><span class="sxs-lookup"><span data-stu-id="7d50d-112">Specifies that the type is nested with private visibility.</span></span>|  
|`tdNestedFamily`|<span data-ttu-id="7d50d-113">Especifica que o tipo é aninhado com visibilidade de família.</span><span class="sxs-lookup"><span data-stu-id="7d50d-113">Specifies that the type is nested with family visibility.</span></span>|  
|`tdNestedAssembly`|<span data-ttu-id="7d50d-114">Especifica que o tipo é aninhado com visibilidade de assembly.</span><span class="sxs-lookup"><span data-stu-id="7d50d-114">Specifies that the type is nested with assembly visibility.</span></span>|  
|`tdNestedFamANDAssem`|<span data-ttu-id="7d50d-115">Especifica que o tipo é aninhado com visibilidade de família e assembly.</span><span class="sxs-lookup"><span data-stu-id="7d50d-115">Specifies that the type is nested with family and assembly visibility.</span></span>|  
|`tdNestedFamORAssem`|<span data-ttu-id="7d50d-116">Especifica que o tipo é aninhado com visibilidade de família ou assembly.</span><span class="sxs-lookup"><span data-stu-id="7d50d-116">Specifies that the type is nested with family or assembly visibility.</span></span>|  
|`tdLayoutMask`|<span data-ttu-id="7d50d-117">Obtém informações de layout para o tipo.</span><span class="sxs-lookup"><span data-stu-id="7d50d-117">Gets layout information for the type.</span></span>|  
|`tdAutoLayout`|<span data-ttu-id="7d50d-118">Especifica que os campos desse tipo são dispostos automaticamente.</span><span class="sxs-lookup"><span data-stu-id="7d50d-118">Specifies that the fields of this type are laid out automatically.</span></span>|  
|`tdSequentialLayout`|<span data-ttu-id="7d50d-119">Especifica que os campos desse tipo são dispostos em sequência.</span><span class="sxs-lookup"><span data-stu-id="7d50d-119">Specifies that the fields of this type are laid out sequentially.</span></span>|  
|`tdExplicitLayout`|<span data-ttu-id="7d50d-120">Especifica que o layout do campo é fornecido explicitamente.</span><span class="sxs-lookup"><span data-stu-id="7d50d-120">Specifies that field layout is supplied explicitly.</span></span>|  
|`tdClassSemanticsMask`|<span data-ttu-id="7d50d-121">Obtém informações semânticas sobre o tipo.</span><span class="sxs-lookup"><span data-stu-id="7d50d-121">Gets semantic information about the type.</span></span>|  
|`tdClass`|<span data-ttu-id="7d50d-122">Especifica que o tipo é uma classe.</span><span class="sxs-lookup"><span data-stu-id="7d50d-122">Specifies that the type is a class.</span></span>|  
|`tdInterface`|<span data-ttu-id="7d50d-123">Especifica que o tipo é uma interface.</span><span class="sxs-lookup"><span data-stu-id="7d50d-123">Specifies that the type is an interface.</span></span>|  
|`tdAbstract`|<span data-ttu-id="7d50d-124">Especifica que o tipo é abstrato.</span><span class="sxs-lookup"><span data-stu-id="7d50d-124">Specifies that the type is abstract.</span></span>|  
|`tdSealed`|<span data-ttu-id="7d50d-125">Especifica que o tipo não pode ser estendido.</span><span class="sxs-lookup"><span data-stu-id="7d50d-125">Specifies that the type cannot be extended.</span></span>|  
|`tdSpecialName`|<span data-ttu-id="7d50d-126">Especifica que o nome da classe é especial.</span><span class="sxs-lookup"><span data-stu-id="7d50d-126">Specifies that the class name is special.</span></span> <span data-ttu-id="7d50d-127">Seu nome descreve como.</span><span class="sxs-lookup"><span data-stu-id="7d50d-127">Its name describes how.</span></span>|  
|`tdImport`|<span data-ttu-id="7d50d-128">Especifica que o tipo é importado.</span><span class="sxs-lookup"><span data-stu-id="7d50d-128">Specifies that the type is imported.</span></span>|  
|`tdSerializable`|<span data-ttu-id="7d50d-129">Especifica que o tipo é serializável.</span><span class="sxs-lookup"><span data-stu-id="7d50d-129">Specifies that the type is serializable.</span></span>|  
|`tdWindowsRuntime`|<span data-ttu-id="7d50d-130">Especifica que esse tipo é um tipo de Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="7d50d-130">Specifies that this type is a Windows Runtime type.</span></span>|  
|`tdStringFormatMask`|<span data-ttu-id="7d50d-131">Obtém informações sobre como as cadeias de caracteres são codificadas e formatadas.</span><span class="sxs-lookup"><span data-stu-id="7d50d-131">Gets information about how strings are encoded and formatted.</span></span>|  
|`tdAnsiClass`|<span data-ttu-id="7d50d-132">Especifica que esse tipo interpreta um LPTSTR como ANSI.</span><span class="sxs-lookup"><span data-stu-id="7d50d-132">Specifies that this type interprets an LPTSTR as ANSI.</span></span>|  
|`tdUnicodeClass`|<span data-ttu-id="7d50d-133">Especifica que esse tipo interpreta um LPTSTR como Unicode.</span><span class="sxs-lookup"><span data-stu-id="7d50d-133">Specifies that this type interprets an LPTSTR as Unicode.</span></span>|  
|`tdAutoClass`|<span data-ttu-id="7d50d-134">Especifica que esse tipo interpreta automaticamente um LPTSTR.</span><span class="sxs-lookup"><span data-stu-id="7d50d-134">Specifies that this type interprets an LPTSTR automatically.</span></span>|  
|`tdCustomFormatClass`|<span data-ttu-id="7d50d-135">Especifica que o tipo tem uma codificação não padrão, conforme especificado por `CustomFormatMask` .</span><span class="sxs-lookup"><span data-stu-id="7d50d-135">Specifies that the type has a non-standard encoding, as specified by `CustomFormatMask`.</span></span>|  
|`tdCustomFormatMask`|<span data-ttu-id="7d50d-136">Use essa máscara para obter informações de codificação não padrão para a interoperabilidade nativa.</span><span class="sxs-lookup"><span data-stu-id="7d50d-136">Use this mask to get non-standard encoding information for native interop.</span></span> <span data-ttu-id="7d50d-137">O significado dos valores desses dois bits não é especificado.</span><span class="sxs-lookup"><span data-stu-id="7d50d-137">The meaning of the values of these two bits is unspecified.</span></span>|  
|`tdBeforeFieldInit`|<span data-ttu-id="7d50d-138">Especifica que o tipo deve ser inicializado antes da primeira tentativa de acessar um campo estático.</span><span class="sxs-lookup"><span data-stu-id="7d50d-138">Specifies that the type must be initialized before the first attempt to access a static field.</span></span>|  
|`tdForwarder`|<span data-ttu-id="7d50d-139">Especifica que o tipo é exportado e um encaminhador de tipo.</span><span class="sxs-lookup"><span data-stu-id="7d50d-139">Specifies that the type is exported, and a type forwarder.</span></span>|  
|`tdReservedMask`|<span data-ttu-id="7d50d-140">Esse sinalizador e os sinalizadores abaixo são usados internamente pelo Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="7d50d-140">This flag and the flags below are used internally by the common language runtime.</span></span>|  
|`tdRTSpecialName`|<span data-ttu-id="7d50d-141">Especifica que a Common Language Runtime deve verificar a codificação do nome.</span><span class="sxs-lookup"><span data-stu-id="7d50d-141">Specifies that the common language runtime should check the name encoding.</span></span>|  
|`tdHasSecurity`|<span data-ttu-id="7d50d-142">Especifica que o tipo tem segurança associada a ele.</span><span class="sxs-lookup"><span data-stu-id="7d50d-142">Specifies that the type has security associated with it.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7d50d-143">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7d50d-143">Requirements</span></span>  
 <span data-ttu-id="7d50d-144">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d50d-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d50d-145">**Cabeçalho:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="7d50d-145">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="7d50d-146">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d50d-146">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d50d-147">Confira também</span><span class="sxs-lookup"><span data-stu-id="7d50d-147">See also</span></span>

- [<span data-ttu-id="7d50d-148">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="7d50d-148">Metadata Enumerations</span></span>](metadata-enumerations.md)
