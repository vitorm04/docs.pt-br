---
title: "Enumeração CorNativeType"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorNativeType
api_location: mscoree.dll
api_type: COM
f1_keywords: CorNativeType
helpviewer_keywords: CorNativeType enumeration [.NET Framework metadata]
ms.assetid: e47a72f1-9609-48ed-bb34-97170d7f6890
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1c17abfc501b0d44981d2ed6cf7d69d60d9948b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="cornativetype-enumeration"></a><span data-ttu-id="f495f-102">Enumeração CorNativeType</span><span class="sxs-lookup"><span data-stu-id="f495f-102">CorNativeType Enumeration</span></span>
<span data-ttu-id="f495f-103">Contém valores que descrevem os tipos nativos de não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="f495f-103">Contains values that describe native unmanaged types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f495f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f495f-104">Syntax</span></span>  
  
```  
typedef enum CorNativeType {  
  
    NATIVE_TYPE_END                  = 0x0,  
    NATIVE_TYPE_VOID                 = 0x1,  
    NATIVE_TYPE_BOOLEAN              = 0x2,  
    NATIVE_TYPE_I1                   = 0x3,  
    NATIVE_TYPE_U1                   = 0x4,  
    NATIVE_TYPE_I2                   = 0x5,  
    NATIVE_TYPE_U2                   = 0x6,  
    NATIVE_TYPE_I4                   = 0x7,  
    NATIVE_TYPE_U4                   = 0x8,  
    NATIVE_TYPE_I8                   = 0x9,  
    NATIVE_TYPE_U8                   = 0xa,  
    NATIVE_TYPE_R4                   = 0xb,  
    NATIVE_TYPE_R8                   = 0xc,  
    NATIVE_TYPE_SYSCHAR              = 0xd,  
    NATIVE_TYPE_VARIANT              = 0xe,  
    NATIVE_TYPE_CURRENCY             = 0xf,  
    NATIVE_TYPE_PTR                  = 0x10,  
  
    NATIVE_TYPE_DECIMAL              = 0x11,  
    NATIVE_TYPE_DATE                 = 0x12,  
    NATIVE_TYPE_BSTR                 = 0x13,  
    NATIVE_TYPE_LPSTR                = 0x14,  
    NATIVE_TYPE_LPWSTR               = 0x15,  
    NATIVE_TYPE_LPTSTR               = 0x16,  
    NATIVE_TYPE_FIXEDSYSSTRING       = 0x17,  
    NATIVE_TYPE_OBJECTREF            = 0x18,  
    NATIVE_TYPE_IUNKNOWN             = 0x19,  
    NATIVE_TYPE_IDISPATCH            = 0x1a,  
    NATIVE_TYPE_STRUCT               = 0x1b,  
    NATIVE_TYPE_INTF                 = 0x1c,  
    NATIVE_TYPE_SAFEARRAY            = 0x1d,  
    NATIVE_TYPE_FIXEDARRAY           = 0x1e,  
    NATIVE_TYPE_INT                  = 0x1f,  
    NATIVE_TYPE_UINT                 = 0x20,  
  
    NATIVE_TYPE_NESTEDSTRUCT         = 0x21,  
    NATIVE_TYPE_BYVALSTR             = 0x22,  
    NATIVE_TYPE_ANSIBSTR             = 0x23,  
    NATIVE_TYPE_TBSTR                = 0x24,  
    NATIVE_TYPE_VARIANTBOOL          = 0x25,  
    NATIVE_TYPE_FUNC                 = 0x26,  
  
    NATIVE_TYPE_ASANY                = 0x28,  
    NATIVE_TYPE_ARRAY                = 0x2a,  
    NATIVE_TYPE_LPSTRUCT             = 0x2b,  
    NATIVE_TYPE_CUSTOMMARSHALER      = 0x2c,  
    NATIVE_TYPE_IINSPECTABLE         = 0x2e,  
    NATIVE_TYPE_HSTRING              = 0x2f,  
  
    NATIVE_TYPE_ERROR                = 0x2d,   
  
    NATIVE_TYPE_MAX                  = 0x50  
  
} CorNativeType;  
```  
  
## <a name="members"></a><span data-ttu-id="f495f-105">Membros</span><span class="sxs-lookup"><span data-stu-id="f495f-105">Members</span></span>  
  
|<span data-ttu-id="f495f-106">Membro</span><span class="sxs-lookup"><span data-stu-id="f495f-106">Member</span></span>|<span data-ttu-id="f495f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f495f-107">Description</span></span>|  
|------------|-----------------|  
|`NATIVE_TYPE_END`|<span data-ttu-id="f495f-108">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="f495f-108">Obsolete.</span></span>|  
|`NATIVE_TYPE_VOID`|<span data-ttu-id="f495f-109">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="f495f-109">Obsolete.</span></span>|  
|`NATIVE_TYPE_BOOLEAN`|<span data-ttu-id="f495f-110">Um valor booliano de 4 bytes, onde TRUE é diferente de zero e FALSE é zero.</span><span class="sxs-lookup"><span data-stu-id="f495f-110">A 4-byte Boolean value, where TRUE is non-zero and FALSE is zero.</span></span>|  
|`NATIVE_TYPE_I1`|<span data-ttu-id="f495f-111">Um valor inteiro assinado de 8 bits.</span><span class="sxs-lookup"><span data-stu-id="f495f-111">A signed 8-bit integer value.</span></span>|  
|`NATIVE_TYPE_U1`|<span data-ttu-id="f495f-112">Um valor inteiro não assinado de 8 bits.</span><span class="sxs-lookup"><span data-stu-id="f495f-112">An unsigned 8-bit integer value.</span></span>|  
|`NATIVE_TYPE_I2`|<span data-ttu-id="f495f-113">Um valor inteiro de 16 bits com sinal.</span><span class="sxs-lookup"><span data-stu-id="f495f-113">A signed 16-bit integer value.</span></span>|  
|`NATIVE_TYPE_U2`|<span data-ttu-id="f495f-114">Um valor inteiro de 16 bits sem sinal.</span><span class="sxs-lookup"><span data-stu-id="f495f-114">An unsigned 16-bit integer value.</span></span>|  
|`NATIVE_TYPE_I4`|<span data-ttu-id="f495f-115">Um valor inteiro de 32 bits com sinal.</span><span class="sxs-lookup"><span data-stu-id="f495f-115">A signed 32-bit integer value.</span></span>|  
|`NATIVE_TYPE_U4`|<span data-ttu-id="f495f-116">Um valor inteiro de 32 bits sem sinal.</span><span class="sxs-lookup"><span data-stu-id="f495f-116">An unsigned 32-bit integer value.</span></span>|  
|`NATIVE_TYPE_I8`|<span data-ttu-id="f495f-117">Um valor inteiro com sinal de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="f495f-117">A signed 64-bit integer value.</span></span>|  
|`NATIVE_TYPE_U8`|<span data-ttu-id="f495f-118">Um valor inteiro não assinado de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="f495f-118">An unsigned 64-bit integer value.</span></span>|  
|`NATIVE_TYPE_R4`|<span data-ttu-id="f495f-119">Um valor numérico ponto flutuante de 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="f495f-119">A 4-byte floating-point numeric value.</span></span>|  
|`NATIVE_TYPE_R8`|<span data-ttu-id="f495f-120">Um valor numérico ponto flutuante de 8 bytes.</span><span class="sxs-lookup"><span data-stu-id="f495f-120">An 8-byte floating-point numeric value.</span></span>|  
|`NATIVE_TYPE_SYSCHAR`|<span data-ttu-id="f495f-121">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="f495f-121">Obsolete.</span></span>|  
|`NATIVE_TYPE_VARIANT`|<span data-ttu-id="f495f-122">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="f495f-122">Obsolete.</span></span>|  
|`NATIVE_TYPE_CURRENCY`|<span data-ttu-id="f495f-123">Um tipo numérico COM que corresponde ao gerenciado <xref:System.Decimal> tipo.</span><span class="sxs-lookup"><span data-stu-id="f495f-123">A numeric COM type that corresponds to the managed <xref:System.Decimal> type.</span></span>|  
|`NATIVE_TYPE_PTR`|<span data-ttu-id="f495f-124">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="f495f-124">Obsolete.</span></span>|  
|`NATIVE_TYPE_DECIMAL`|<span data-ttu-id="f495f-125">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="f495f-125">Obsolete.</span></span>|  
|`NATIVE_TYPE_DATE`|<span data-ttu-id="f495f-126">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="f495f-126">Obsolete.</span></span>|  
|`NATIVE_TYPE_BSTR`|<span data-ttu-id="f495f-127">Interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="f495f-127">COM Interop.</span></span>|  
|`NATIVE_TYPE_LPSTR`|<span data-ttu-id="f495f-128">Um valor de cadeia de caracteres LPSTR.</span><span class="sxs-lookup"><span data-stu-id="f495f-128">An LPSTR string value.</span></span>|  
|`NATIVE_TYPE_LPWSTR`|<span data-ttu-id="f495f-129">Um valor de cadeia de caracteres LPWSTR.</span><span class="sxs-lookup"><span data-stu-id="f495f-129">An LPWSTR string value.</span></span>|  
|`NATIVE_TYPE_LPTSTR`|<span data-ttu-id="f495f-130">Um valor de cadeia de caracteres LPTSTR.</span><span class="sxs-lookup"><span data-stu-id="f495f-130">An LPTSTR string value.</span></span>|  
|`NATIVE_TYPE_FIXEDSYSSTRING`|<span data-ttu-id="f495f-131">Um valor de cadeia de caracteres fixa, definido pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="f495f-131">A fixed, system-defined string value.</span></span>|  
|`NATIVE_TYPE_OBJECTREF`|<span data-ttu-id="f495f-132">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="f495f-132">Obsolete.</span></span>|  
|`NATIVE_TYPE_IUNKNOWN`|<span data-ttu-id="f495f-133">Interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="f495f-133">COM Interop.</span></span>|  
|`NATIVE_TYPE_IDISPATCH`|<span data-ttu-id="f495f-134">Interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="f495f-134">COM Interop.</span></span>|  
|`NATIVE_TYPE_STRUCT`|<span data-ttu-id="f495f-135">Um valor de estrutura nativa.</span><span class="sxs-lookup"><span data-stu-id="f495f-135">A native structure value.</span></span>|  
|`NATIVE_TYPE_INTF`|<span data-ttu-id="f495f-136">Interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="f495f-136">COM Interop.</span></span>|  
|`NATIVE_TYPE_SAFEARRAY`|<span data-ttu-id="f495f-137">Interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="f495f-137">COM Interop.</span></span>|  
|`NATIVE_TYPE_FIXEDARRAY`|<span data-ttu-id="f495f-138">Um valor de matriz de comprimento fixo.</span><span class="sxs-lookup"><span data-stu-id="f495f-138">A fixed-length array value.</span></span>|  
|`NATIVE_TYPE_INT`|<span data-ttu-id="f495f-139">Um valor inteiro assinado de 16 bits nativo.</span><span class="sxs-lookup"><span data-stu-id="f495f-139">A native 16-bit signed integer value.</span></span>|  
|`NATIVE_TYPE_UINT`|<span data-ttu-id="f495f-140">Um valor inteiro não assinado de 16 bits nativo.</span><span class="sxs-lookup"><span data-stu-id="f495f-140">A native 16-bit unsigned integer value.</span></span>|  
|`NATIVE_TYPE_NESTEDSTRUCT`|<span data-ttu-id="f495f-141">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="f495f-141">Obsolete.</span></span><br /><br /> <span data-ttu-id="f495f-142">Use NATIVE_TYPE_STRUCT.</span><span class="sxs-lookup"><span data-stu-id="f495f-142">Use NATIVE_TYPE_STRUCT.</span></span>|  
|`NATIVE_TYPE_BYVALSTR`|<span data-ttu-id="f495f-143">Interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="f495f-143">COM Interop.</span></span>|  
|`NATIVE_TYPE_ANSIBSTR`|<span data-ttu-id="f495f-144">Interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="f495f-144">COM Interop.</span></span>|  
|`NATIVE_TYPE_TBSTR`|<span data-ttu-id="f495f-145">Interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="f495f-145">COM Interop.</span></span><br /><br /> <span data-ttu-id="f495f-146">Selecione BSTR ou ANSIBSTR dependendo da plataforma.</span><span class="sxs-lookup"><span data-stu-id="f495f-146">Select BSTR or ANSIBSTR depending on the platform.</span></span>|  
|`NATIVE_TYPE_VARIANTBOOL`|<span data-ttu-id="f495f-147">Um 2 bytes valor booliano, onde TRUE é -1 e FALSE é zero.</span><span class="sxs-lookup"><span data-stu-id="f495f-147">A 2-byte Boolean value, where TRUE is -1 and FALSE is zero.</span></span>|  
|`NATIVE_TYPE_FUNC`|<span data-ttu-id="f495f-148">Um ponteiro de função.</span><span class="sxs-lookup"><span data-stu-id="f495f-148">A function pointer.</span></span>|  
|`NATIVE_TYPE_ASANY`|<span data-ttu-id="f495f-149">Uma referência a qualquer tipo nativo.</span><span class="sxs-lookup"><span data-stu-id="f495f-149">A reference to any native type.</span></span>|  
|`NATIVE_TYPE_ARRAY`|<span data-ttu-id="f495f-150">Uma referência a uma matriz com membros de um tipo não especificado.</span><span class="sxs-lookup"><span data-stu-id="f495f-150">A reference to an array with members of an unspecified type.</span></span>|  
|`NATIVE_TYPE_LPSTRUCT`|<span data-ttu-id="f495f-151">Um ponteiro de inteiro de 32 bits para uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="f495f-151">A 32-bit integer pointer to a structure.</span></span>|  
|`NATIVE_TYPE_CUSTOMMARSHALER`|<span data-ttu-id="f495f-152">Um tipo nativo do marshaler personalizado.</span><span class="sxs-lookup"><span data-stu-id="f495f-152">A custom marshaler native type.</span></span><br /><br /> <span data-ttu-id="f495f-153">Isso deve ser seguido por uma cadeia de caracteres de formato a seguir: "empacotador de nome/0Custom tipo nativo de tipo de cookie de nome/0Optional/0" ou "{nativo digite GUID} 0Custom marshaler cookie de nome/0Optional/0 do tipo"</span><span class="sxs-lookup"><span data-stu-id="f495f-153">This must be followed by a string of the following format: "Native type name/0Custom marshaler type name/0Optional cookie/0" or "{Native type GUID}/0Custom marshaler type name/0Optional cookie/0"</span></span>|  
|`NATIVE_TYPE_ERROR`|<span data-ttu-id="f495f-154">Interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="f495f-154">COM Interop.</span></span><br /><br /> <span data-ttu-id="f495f-155">Com ELEMENT_TYPE_I4 esse tipo é mapeado para VT_HRESULT.</span><span class="sxs-lookup"><span data-stu-id="f495f-155">With ELEMENT_TYPE_I4 this type maps to VT_HRESULT.</span></span>|  
|`NATIVE_TYPE_IINSPECTABLE`|<span data-ttu-id="f495f-156">Um nativo `IInspectable` tipo.</span><span class="sxs-lookup"><span data-stu-id="f495f-156">A native `IInspectable` type.</span></span>|  
|`NATIVE_TYPE_HSTRING`|<span data-ttu-id="f495f-157">Um nativo `HString`.</span><span class="sxs-lookup"><span data-stu-id="f495f-157">A native `HString`.</span></span>|  
|`NATIVE_TYPE_MAX`|<span data-ttu-id="f495f-158">Um valor inválido.</span><span class="sxs-lookup"><span data-stu-id="f495f-158">An invalid value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f495f-159">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f495f-159">Requirements</span></span>  
 <span data-ttu-id="f495f-160">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f495f-160">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f495f-161">**Cabeçalho:** Corhdr</span><span class="sxs-lookup"><span data-stu-id="f495f-161">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="f495f-162">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f495f-162">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f495f-163">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f495f-163">See Also</span></span>  
 <xref:System.Runtime.InteropServices.UnmanagedType>  
 [<span data-ttu-id="f495f-164">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="f495f-164">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
