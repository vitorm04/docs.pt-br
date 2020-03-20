---
title: Método IMetaDataEmit::DefineMethod
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMethod
helpviewer_keywords:
- DefineMethod method [.NET Framework metadata]
- IMetaDataEmit::DefineMethod method [.NET Framework metadata]
ms.assetid: 3e2102c5-48b7-4c0e-b805-7e2b5e156e3d
topic_type:
- apiref
ms.openlocfilehash: d4f3c95428d6f0f8807e284c5b54582428176511
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177673"
---
# <a name="imetadataemitdefinemethod-method"></a><span data-ttu-id="d7d22-102">Método IMetaDataEmit::DefineMethod</span><span class="sxs-lookup"><span data-stu-id="d7d22-102">IMetaDataEmit::DefineMethod Method</span></span>
<span data-ttu-id="d7d22-103">Cria uma definição para um método ou função global com a assinatura especificada e retorna um token para essa definição de método.</span><span class="sxs-lookup"><span data-stu-id="d7d22-103">Creates a definition for a method or global function with the specified signature, and returns a token to that method definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7d22-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d7d22-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethod (
    [in]  mdTypeDef         td,
    [in]  LPCWSTR           szName,
    [in]  DWORD             dwMethodFlags,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [in]  ULONG             ulCodeRVA,
    [in]  DWORD             dwImplFlags,
    [out] mdMethodDef      *pmd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7d22-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="d7d22-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="d7d22-106">[em] O `mdTypedef` token da classe pai ou interface pai do método.</span><span class="sxs-lookup"><span data-stu-id="d7d22-106">[in] The `mdTypedef` token of the parent class or parent interface of the method.</span></span> <span data-ttu-id="d7d22-107">Definir `td` `mdTokenNil`para , se você estiver definindo uma função global.</span><span class="sxs-lookup"><span data-stu-id="d7d22-107">Set `td` to `mdTokenNil`, if you are defining a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="d7d22-108">[em] O nome do membro no Unicode.</span><span class="sxs-lookup"><span data-stu-id="d7d22-108">[in] The member name in Unicode.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="d7d22-109">[em] Um valor da enumeração [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) que especifica os atributos do método ou da função global.</span><span class="sxs-lookup"><span data-stu-id="d7d22-109">[in] A value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration that specifies the attributes of the method or global function.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="d7d22-110">[em] A assinatura do método.</span><span class="sxs-lookup"><span data-stu-id="d7d22-110">[in] The method signature.</span></span> <span data-ttu-id="d7d22-111">A assinatura é persistida conforme fornecido.</span><span class="sxs-lookup"><span data-stu-id="d7d22-111">The signature is persisted as supplied.</span></span> <span data-ttu-id="d7d22-112">Se você precisar especificar informações adicionais para quaisquer parâmetros, use o método [IMetaDataEmit::SetParamProps.](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md)</span><span class="sxs-lookup"><span data-stu-id="d7d22-112">If you need to specify additional information for any parameters, use the [IMetaDataEmit::SetParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="d7d22-113">[em] A contagem de `pvSigBlob`bytes em .</span><span class="sxs-lookup"><span data-stu-id="d7d22-113">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="d7d22-114">[em] O endereço do código.</span><span class="sxs-lookup"><span data-stu-id="d7d22-114">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="d7d22-115">[em] Um valor da enumeração [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) que especifica os recursos de implementação do método.</span><span class="sxs-lookup"><span data-stu-id="d7d22-115">[in] A value of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the implementation features of the method.</span></span>  
  
 `pmd`  
 <span data-ttu-id="d7d22-116">[fora] O símbolo do membro.</span><span class="sxs-lookup"><span data-stu-id="d7d22-116">[out] The member token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7d22-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="d7d22-117">Remarks</span></span>  
 <span data-ttu-id="d7d22-118">A API de metadados garante a persistência de métodos na mesma ordem que o chamador emite-os para uma determinada classe ou interface de fechamento, que é especificada no `td` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="d7d22-118">The metadata API guarantees to persist methods in the same order as the caller emits them for a given enclosing class or interface, which is specified in the `td` parameter.</span></span>  
  
 <span data-ttu-id="d7d22-119">Informações adicionais sobre `DefineMethod` o uso e configurações de parâmetros específicos são dadas abaixo.</span><span class="sxs-lookup"><span data-stu-id="d7d22-119">Additional information regarding the use of `DefineMethod` and particular parameter settings is given below.</span></span>  
  
## <a name="slots-in-the-v-table"></a><span data-ttu-id="d7d22-120">Ranhuras na tabela V</span><span class="sxs-lookup"><span data-stu-id="d7d22-120">Slots in the V-table</span></span>  
 <span data-ttu-id="d7d22-121">O tempo de execução usa definições de método para configurar slots de tabela v.</span><span class="sxs-lookup"><span data-stu-id="d7d22-121">The runtime uses method definitions to set up v-table slots.</span></span> <span data-ttu-id="d7d22-122">No caso de um ou mais slots precisarem ser pulados, como preservar a paridade com um layout de interface COM, um método manequim é definido para assumir o slot ou slots na tabela v; defina `dwMethodFlags` o `mdRTSpecialName` valor da enumeração [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) e especifique o nome como:</span><span class="sxs-lookup"><span data-stu-id="d7d22-122">In the case where one or more slots need to be skipped, such as to preserve parity with a COM interface layout, a dummy method is defined to take up the slot or slots in the v-table; set the `dwMethodFlags` to the `mdRTSpecialName` value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration and specify the name as:</span></span>  
  
 <span data-ttu-id="d7d22-123">_VtblGap\<*seqüêncianúmero*>\<\_*de números de númerosdeslots*></span><span class="sxs-lookup"><span data-stu-id="d7d22-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span></span>
  
 <span data-ttu-id="d7d22-124">onde *SequenceNumber* é o número de seqüência do método e *CountOfSlots* é o número de slots a serem pulados na tabela v.</span><span class="sxs-lookup"><span data-stu-id="d7d22-124">where *SequenceNumber* is the sequence number of the method and *CountOfSlots* is the number of slots to skip in the v-table.</span></span> <span data-ttu-id="d7d22-125">Se *CountOfSlots* for omitido, 1 é assumido.</span><span class="sxs-lookup"><span data-stu-id="d7d22-125">If *CountOfSlots* is omitted, 1 is assumed.</span></span> <span data-ttu-id="d7d22-126">Esses métodos falsos não podem ser chamados de código gerenciado ou não e qualquer tentativa de chamá-los, de código gerenciado ou não gerenciado, gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="d7d22-126">These dummy methods are not callable from either managed or unmanaged code and any attempt to call them, from either managed or unmanaged code, generates an exception.</span></span> <span data-ttu-id="d7d22-127">Seu único propósito é retomar espaço na tabela v que o tempo de execução gera para a integração COM.</span><span class="sxs-lookup"><span data-stu-id="d7d22-127">Their only purpose is to take up space in the v-table that the runtime generates for COM integration.</span></span>  
  
## <a name="duplicate-methods"></a><span data-ttu-id="d7d22-128">Métodos duplicados</span><span class="sxs-lookup"><span data-stu-id="d7d22-128">Duplicate Methods</span></span>  
 <span data-ttu-id="d7d22-129">Você não deve definir métodos duplicados.</span><span class="sxs-lookup"><span data-stu-id="d7d22-129">You should not define duplicate methods.</span></span> <span data-ttu-id="d7d22-130">Ou seja, você `DefineMethod` não deve ligar com `td`um `wzName`conjunto `pvSig` duplicado de valores nos parâmetros e parâmetros.</span><span class="sxs-lookup"><span data-stu-id="d7d22-130">That is, you should not call `DefineMethod` with a duplicate set of values in the `td`, `wzName`, and `pvSig` parameters.</span></span> <span data-ttu-id="d7d22-131">(Esses três parâmetros juntos definem exclusivamente o método.).</span><span class="sxs-lookup"><span data-stu-id="d7d22-131">(These three parameters together uniquely define the method.).</span></span> <span data-ttu-id="d7d22-132">No entanto, você pode usar uma duplicata tripla desde `mdPrivateScope` que, `dwMethodFlags` para uma das definições do método, você defina a broca no parâmetro.</span><span class="sxs-lookup"><span data-stu-id="d7d22-132">However, you can use a duplicate triple provided that, for one of the method definitions, you set the `mdPrivateScope` bit in the `dwMethodFlags` parameter.</span></span> <span data-ttu-id="d7d22-133">(O `mdPrivateScope` bit significa que o compilador não emite uma referência a essa definição de método.)</span><span class="sxs-lookup"><span data-stu-id="d7d22-133">(The `mdPrivateScope` bit means that the compiler will not emit a reference to this method definition.)</span></span>  
  
## <a name="method-implementation-information"></a><span data-ttu-id="d7d22-134">Informações de implementação do método</span><span class="sxs-lookup"><span data-stu-id="d7d22-134">Method Implementation Information</span></span>  
 <span data-ttu-id="d7d22-135">Muitas vezes não são conhecidas informações sobre a implementação do método no momento em que o método é declarado.</span><span class="sxs-lookup"><span data-stu-id="d7d22-135">Information about the method implementation is often not known at the time the method is declared.</span></span> <span data-ttu-id="d7d22-136">Portanto, você não precisa passar valores `dwImplFlags` nos `DefineMethod`parâmetros e parâmetros ao `ulCodeRVA` ligar .</span><span class="sxs-lookup"><span data-stu-id="d7d22-136">Therefore, you do not need to pass values in the `ulCodeRVA` and `dwImplFlags` parameters when calling `DefineMethod`.</span></span> <span data-ttu-id="d7d22-137">Os valores podem ser fornecidos posteriormente através do [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) ou [IMetaDataEmit::SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="d7d22-137">The values can be supplied later through [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) or [IMetaDataEmit::SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), as appropriate.</span></span>  
  
 <span data-ttu-id="d7d22-138">Em algumas situações, como a invocação da plataforma (PInvoke) ou cenários `ulCodeRVA` de interop COM, o corpo do método não será fornecido e deve ser definido como zero.</span><span class="sxs-lookup"><span data-stu-id="d7d22-138">In some situations, such as platform invocation (PInvoke) or COM interop scenarios, the method body will not be supplied, and `ulCodeRVA` should be set to zero.</span></span> <span data-ttu-id="d7d22-139">Nessas situações, o método não deve ser marcado como abstrato, pois o tempo de execução localizará a implementação.</span><span class="sxs-lookup"><span data-stu-id="d7d22-139">In these situations, the method should not be tagged as abstract, because the runtime will locate the implementation.</span></span>  
  
## <a name="defining-a-method-for-pinvoke"></a><span data-ttu-id="d7d22-140">Definindo um método para PInvoke</span><span class="sxs-lookup"><span data-stu-id="d7d22-140">Defining a Method for PInvoke</span></span>  
 <span data-ttu-id="d7d22-141">Para cada função não gerenciada a ser chamada através do PInvoke, você deve definir um método gerenciado que represente a função não gerenciada de destino.</span><span class="sxs-lookup"><span data-stu-id="d7d22-141">For each unmanaged function to be called through PInvoke, you must define a managed method that represents the target unmanaged function.</span></span> <span data-ttu-id="d7d22-142">Para definir o método `DefineMethod` gerenciado, use com alguns dos parâmetros definidos para determinados valores, dependendo da forma como o PInvoke é usado:</span><span class="sxs-lookup"><span data-stu-id="d7d22-142">To define the managed method, use `DefineMethod` with some of the parameters set to certain values, depending on the way in which PInvoke is used:</span></span>  
  
- <span data-ttu-id="d7d22-143">True PInvoke - envolve a invocação de um método externo não gerenciado que reside em um DLL não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="d7d22-143">True PInvoke - involves invocation of an external unmanaged method that resides in an unmanaged DLL.</span></span>  
  
- <span data-ttu-id="d7d22-144">PInvoke local - envolve a invocação de um método nativo não gerenciado que está incorporado no módulo gerenciado atual.</span><span class="sxs-lookup"><span data-stu-id="d7d22-144">Local PInvoke - involves invocation of a native unmanaged method that is embedded in the current managed module.</span></span>  
  
 <span data-ttu-id="d7d22-145">As configurações dos parâmetros são fornecidas na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="d7d22-145">The parameter settings are given in the following table.</span></span>  
  
|<span data-ttu-id="d7d22-146">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="d7d22-146">Parameter</span></span>|<span data-ttu-id="d7d22-147">Valores para pinvoke verdadeiro</span><span class="sxs-lookup"><span data-stu-id="d7d22-147">Values for true PInvoke</span></span>|<span data-ttu-id="d7d22-148">Valores para PInvoke local</span><span class="sxs-lookup"><span data-stu-id="d7d22-148">Values for local PInvoke</span></span>|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||<span data-ttu-id="d7d22-149">Conjunto `mdStatic`; claro `mdSynchronized` `mdAbstract`e .</span><span class="sxs-lookup"><span data-stu-id="d7d22-149">Set `mdStatic`; clear `mdSynchronized` and `mdAbstract`.</span></span>|  
|`pvSigBlob`|<span data-ttu-id="d7d22-150">Uma assinatura de método de tempo de execução de idioma comum válido (CLR) com parâmetros que são tipos gerenciados válidos.</span><span class="sxs-lookup"><span data-stu-id="d7d22-150">A valid common language runtime (CLR) method signature with parameters that are valid managed types.</span></span>|<span data-ttu-id="d7d22-151">Uma assinatura de método CLR válida com parâmetros que são tipos gerenciados válidos.</span><span class="sxs-lookup"><span data-stu-id="d7d22-151">A valid CLR method signature with parameters that are valid managed types.</span></span>|  
|`ulCodeRVA`||<span data-ttu-id="d7d22-152">0</span><span class="sxs-lookup"><span data-stu-id="d7d22-152">0</span></span>|  
|`dwImplFlags`|<span data-ttu-id="d7d22-153">Definir `miCil` e `miManaged`.</span><span class="sxs-lookup"><span data-stu-id="d7d22-153">Set `miCil` and `miManaged`.</span></span>|<span data-ttu-id="d7d22-154">Definir `miNative` e `miUnmanaged`.</span><span class="sxs-lookup"><span data-stu-id="d7d22-154">Set `miNative` and `miUnmanaged`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d7d22-155">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d7d22-155">Requirements</span></span>  
 <span data-ttu-id="d7d22-156">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7d22-156">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7d22-157">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d7d22-157">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d7d22-158">**Biblioteca:** Usado como recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d7d22-158">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d7d22-159">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7d22-159">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7d22-160">Confira também</span><span class="sxs-lookup"><span data-stu-id="d7d22-160">See also</span></span>

- [<span data-ttu-id="d7d22-161">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="d7d22-161">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="d7d22-162">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="d7d22-162">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
