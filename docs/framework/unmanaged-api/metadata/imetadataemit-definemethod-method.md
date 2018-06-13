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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 53fd830cdefda58d40f96f8662a80d1888d963dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449193"
---
# <a name="imetadataemitdefinemethod-method"></a><span data-ttu-id="e8677-102">Método IMetaDataEmit::DefineMethod</span><span class="sxs-lookup"><span data-stu-id="e8677-102">IMetaDataEmit::DefineMethod Method</span></span>
<span data-ttu-id="e8677-103">Cria uma definição para um método ou função global com a assinatura especificada e retorna um token para que a definição de método.</span><span class="sxs-lookup"><span data-stu-id="e8677-103">Creates a definition for a method or global function with the specified signature, and returns a token to that method definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8677-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e8677-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="e8677-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e8677-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="e8677-106">[in] O `mdTypedef` token da classe pai ou interface pai do método.</span><span class="sxs-lookup"><span data-stu-id="e8677-106">[in] The `mdTypedef` token of the parent class or parent interface of the method.</span></span> <span data-ttu-id="e8677-107">Definir `td` para `mdTokenNil`, se você estiver definindo uma função global.</span><span class="sxs-lookup"><span data-stu-id="e8677-107">Set `td` to `mdTokenNil`, if you are defining a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="e8677-108">[in] O nome de membro em Unicode.</span><span class="sxs-lookup"><span data-stu-id="e8677-108">[in] The member name in Unicode.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="e8677-109">[in] Um valor de [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeração que especifica os atributos de método ou função global.</span><span class="sxs-lookup"><span data-stu-id="e8677-109">[in] A value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration that specifies the attributes of the method or global function.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="e8677-110">[in] A assinatura do método.</span><span class="sxs-lookup"><span data-stu-id="e8677-110">[in] The method signature.</span></span> <span data-ttu-id="e8677-111">A assinatura é mantida conforme fornecido.</span><span class="sxs-lookup"><span data-stu-id="e8677-111">The signature is persisted as supplied.</span></span> <span data-ttu-id="e8677-112">Se você precisar especificar informações adicionais para qualquer parâmetro, use o [Setparamprops](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="e8677-112">If you need to specify additional information for any parameters, use the [IMetaDataEmit::SetParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="e8677-113">[in] A contagem de bytes em `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="e8677-113">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="e8677-114">[in] O endereço do código.</span><span class="sxs-lookup"><span data-stu-id="e8677-114">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="e8677-115">[in] Um valor de [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeração que especifica os recursos de implementação do método.</span><span class="sxs-lookup"><span data-stu-id="e8677-115">[in] A value of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the implementation features of the method.</span></span>  
  
 `pmd`  
 <span data-ttu-id="e8677-116">[out] O token de membro.</span><span class="sxs-lookup"><span data-stu-id="e8677-116">[out] The member token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8677-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="e8677-117">Remarks</span></span>  
 <span data-ttu-id="e8677-118">Os metadados de API garante persistem métodos na mesma ordem em que o chamador emite-los para uma determinada classe de delimitador ou a interface, que é especificada no `td` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e8677-118">The metadata API guarantees to persist methods in the same order as the caller emits them for a given enclosing class or interface, which is specified in the `td` parameter.</span></span>  
  
 <span data-ttu-id="e8677-119">Informações adicionais sobre o uso do `DefineMethod` e configurações de parâmetro específico são indicados abaixo.</span><span class="sxs-lookup"><span data-stu-id="e8677-119">Additional information regarding the use of `DefineMethod` and particular parameter settings is given below.</span></span>  
  
## <a name="slots-in-the-v-table"></a><span data-ttu-id="e8677-120">Slots da tabela V</span><span class="sxs-lookup"><span data-stu-id="e8677-120">Slots in the V-table</span></span>  
 <span data-ttu-id="e8677-121">O tempo de execução usa definições de método para configurar os slots da tabela v.</span><span class="sxs-lookup"><span data-stu-id="e8677-121">The runtime uses method definitions to set up v-table slots.</span></span> <span data-ttu-id="e8677-122">No caso onde um ou mais slots precisam ser ignorada, como para preservar a paridade com o layout de interface COM um método fictício é definido para o slot ou slots da tabela v. definir o `dwMethodFlags` para o `mdRTSpecialName` valor o [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeração e especifique o nome como:</span><span class="sxs-lookup"><span data-stu-id="e8677-122">In the case where one or more slots need to be skipped, such as to preserve parity with a COM interface layout, a dummy method is defined to take up the slot or slots in the v-table; set the `dwMethodFlags` to the `mdRTSpecialName` value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration and specify the name as:</span></span>  
  
 <span data-ttu-id="e8677-123">VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span><span class="sxs-lookup"><span data-stu-id="e8677-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span></span>  
  
 <span data-ttu-id="e8677-124">onde *SequenceNumber* é o número de sequência do método e *CountOfSlots* é o número de slots para ignorar na tabela v.</span><span class="sxs-lookup"><span data-stu-id="e8677-124">where *SequenceNumber* is the sequence number of the method and *CountOfSlots* is the number of slots to skip in the v-table.</span></span> <span data-ttu-id="e8677-125">Se *CountOfSlots* for omitido, 1 é assumido.</span><span class="sxs-lookup"><span data-stu-id="e8677-125">If *CountOfSlots* is omitted, 1 is assumed.</span></span> <span data-ttu-id="e8677-126">Esses métodos fictícios não pode ser chamados de código gerenciado ou e qualquer tentativa de chamá-los, o código gerenciado ou, gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="e8677-126">These dummy methods are not callable from either managed or unmanaged code and any attempt to call them, from either managed or unmanaged code, generates an exception.</span></span> <span data-ttu-id="e8677-127">Seu único propósito é ocupam espaço no v-table gerados para integração COM o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e8677-127">Their only purpose is to take up space in the v-table that the runtime generates for COM integration.</span></span>  
  
## <a name="duplicate-methods"></a><span data-ttu-id="e8677-128">Métodos duplicados</span><span class="sxs-lookup"><span data-stu-id="e8677-128">Duplicate Methods</span></span>  
 <span data-ttu-id="e8677-129">Você não deve definir métodos duplicados.</span><span class="sxs-lookup"><span data-stu-id="e8677-129">You should not define duplicate methods.</span></span> <span data-ttu-id="e8677-130">Ou seja, você não deve chamar `DefineMethod` com um conjunto duplicado dos valores a `td`, `wzName`, e `pvSig` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="e8677-130">That is, you should not call `DefineMethod` with a duplicate set of values in the `td`, `wzName`, and `pvSig` parameters.</span></span> <span data-ttu-id="e8677-131">(Esses três parâmetros juntos definem exclusivamente o método.).</span><span class="sxs-lookup"><span data-stu-id="e8677-131">(These three parameters together uniquely define the method.).</span></span> <span data-ttu-id="e8677-132">No entanto, você pode usar um triplo duplicado desde que, para uma das definições de método, você deve definir o `mdPrivateScope` bit no `dwMethodFlags` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e8677-132">However, you can use a duplicate triple provided that, for one of the method definitions, you set the `mdPrivateScope` bit in the `dwMethodFlags` parameter.</span></span> <span data-ttu-id="e8677-133">(O `mdPrivateScope` bit significa que o compilador não emitirá uma referência a essa definição de método.)</span><span class="sxs-lookup"><span data-stu-id="e8677-133">(The `mdPrivateScope` bit means that the compiler will not emit a reference to this method definition.)</span></span>  
  
## <a name="method-implementation-information"></a><span data-ttu-id="e8677-134">Informações de implementação de método</span><span class="sxs-lookup"><span data-stu-id="e8677-134">Method Implementation Information</span></span>  
 <span data-ttu-id="e8677-135">Informações sobre a implementação do método geralmente não são conhecidas no momento em que o método for declarado.</span><span class="sxs-lookup"><span data-stu-id="e8677-135">Information about the method implementation is often not known at the time the method is declared.</span></span> <span data-ttu-id="e8677-136">Portanto, você não precisa passar valores de `ulCodeRVA` e `dwImplFlags` parâmetros ao chamar `DefineMethod`.</span><span class="sxs-lookup"><span data-stu-id="e8677-136">Therefore, you do not need to pass values in the `ulCodeRVA` and `dwImplFlags` parameters when calling `DefineMethod`.</span></span> <span data-ttu-id="e8677-137">Os valores podem ser fornecidos posteriormente por [: Setmethodimplflags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) ou [: Setrva](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="e8677-137">The values can be supplied later through [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) or [IMetaDataEmit::SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), as appropriate.</span></span>  
  
 <span data-ttu-id="e8677-138">Em algumas situações, como a invocação de plataforma (PInvoke) ou cenários de interoperabilidade COM, o corpo do método não será fornecido, e `ulCodeRVA` deve ser definido como zero.</span><span class="sxs-lookup"><span data-stu-id="e8677-138">In some situations, such as platform invocation (PInvoke) or COM interop scenarios, the method body will not be supplied, and `ulCodeRVA` should be set to zero.</span></span> <span data-ttu-id="e8677-139">Nessas situações, o método deve não marcado como abstract, porque o tempo de execução localizará a implementação.</span><span class="sxs-lookup"><span data-stu-id="e8677-139">In these situations, the method should not be tagged as abstract, because the runtime will locate the implementation.</span></span>  
  
## <a name="defining-a-method-for-pinvoke"></a><span data-ttu-id="e8677-140">Definindo um método de PInvoke</span><span class="sxs-lookup"><span data-stu-id="e8677-140">Defining a Method for PInvoke</span></span>  
 <span data-ttu-id="e8677-141">Para cada função não gerenciada a ser chamado por meio de PInvoke, você deve definir um método gerenciado que representa a função não gerenciada de destino.</span><span class="sxs-lookup"><span data-stu-id="e8677-141">For each unmanaged function to be called through PInvoke, you must define a managed method that represents the target unmanaged function.</span></span> <span data-ttu-id="e8677-142">Para definir o método gerenciado, use `DefineMethod` com alguns dos parâmetros definidos para determinados valores, dependendo do modo no qual PInvoke é usada:</span><span class="sxs-lookup"><span data-stu-id="e8677-142">To define the managed method, use `DefineMethod` with some of the parameters set to certain values, depending on the way in which PInvoke is used:</span></span>  
  
-   <span data-ttu-id="e8677-143">Verdadeiro PInvoke - envolve a invocação de um método externo não gerenciado que reside em uma DLL não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="e8677-143">True PInvoke - involves invocation of an external unmanaged method that resides in an unmanaged DLL.</span></span>  
  
-   <span data-ttu-id="e8677-144">PInvoke local - envolve a invocação de um método nativo não gerenciado que é inserido no módulo gerenciado atual.</span><span class="sxs-lookup"><span data-stu-id="e8677-144">Local PInvoke - involves invocation of a native unmanaged method that is embedded in the current managed module.</span></span>  
  
 <span data-ttu-id="e8677-145">As configurações de parâmetro são fornecidas na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="e8677-145">The parameter settings are given in the following table.</span></span>  
  
|<span data-ttu-id="e8677-146">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="e8677-146">Parameter</span></span>|<span data-ttu-id="e8677-147">Valores de PInvoke true</span><span class="sxs-lookup"><span data-stu-id="e8677-147">Values for true PInvoke</span></span>|<span data-ttu-id="e8677-148">Valores de PInvoke local</span><span class="sxs-lookup"><span data-stu-id="e8677-148">Values for local PInvoke</span></span>|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||<span data-ttu-id="e8677-149">Definir `mdStatic`; limpar `mdSynchronized` e `mdAbstract`.</span><span class="sxs-lookup"><span data-stu-id="e8677-149">Set `mdStatic`; clear `mdSynchronized` and `mdAbstract`.</span></span>|  
|`pvSigBlob`|<span data-ttu-id="e8677-150">Tipos gerenciados do válido common language runtime (CLR) assinatura de um método com parâmetros que são válidos.</span><span class="sxs-lookup"><span data-stu-id="e8677-150">A valid common language runtime (CLR) method signature with parameters that are valid managed types.</span></span>|<span data-ttu-id="e8677-151">Tipos gerenciados de uma assinatura de método CLR válida com parâmetros que são válidos.</span><span class="sxs-lookup"><span data-stu-id="e8677-151">A valid CLR method signature with parameters that are valid managed types.</span></span>|  
|`ulCodeRVA`||<span data-ttu-id="e8677-152">0</span><span class="sxs-lookup"><span data-stu-id="e8677-152">0</span></span>|  
|`dwImplFlags`|<span data-ttu-id="e8677-153">Definir `miCil` e `miManaged`.</span><span class="sxs-lookup"><span data-stu-id="e8677-153">Set `miCil` and `miManaged`.</span></span>|<span data-ttu-id="e8677-154">Definir `miNative` e `miUnmanaged`.</span><span class="sxs-lookup"><span data-stu-id="e8677-154">Set `miNative` and `miUnmanaged`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e8677-155">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e8677-155">Requirements</span></span>  
 <span data-ttu-id="e8677-156">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8677-156">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8677-157">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e8677-157">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e8677-158">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="e8677-158">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e8677-159">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8677-159">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8677-160">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e8677-160">See Also</span></span>  
 [<span data-ttu-id="e8677-161">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="e8677-161">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="e8677-162">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="e8677-162">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
