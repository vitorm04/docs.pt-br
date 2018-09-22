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
ms.openlocfilehash: 2dbc6b5ffaa3a381bdd657059a682a3d12dc4cf1
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46584260"
---
# <a name="imetadataemitdefinemethod-method"></a><span data-ttu-id="8a54e-102">Método IMetaDataEmit::DefineMethod</span><span class="sxs-lookup"><span data-stu-id="8a54e-102">IMetaDataEmit::DefineMethod Method</span></span>
<span data-ttu-id="8a54e-103">Cria uma definição para um método ou uma função global com a assinatura especificada e retorna um token para essa definição de método.</span><span class="sxs-lookup"><span data-stu-id="8a54e-103">Creates a definition for a method or global function with the specified signature, and returns a token to that method definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a54e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8a54e-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="8a54e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8a54e-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="8a54e-106">[in] O `mdTypedef` token da classe pai ou a interface pai do método.</span><span class="sxs-lookup"><span data-stu-id="8a54e-106">[in] The `mdTypedef` token of the parent class or parent interface of the method.</span></span> <span data-ttu-id="8a54e-107">Definir `td` para `mdTokenNil`, se você estiver definindo uma função global.</span><span class="sxs-lookup"><span data-stu-id="8a54e-107">Set `td` to `mdTokenNil`, if you are defining a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="8a54e-108">[in] O nome do membro em Unicode.</span><span class="sxs-lookup"><span data-stu-id="8a54e-108">[in] The member name in Unicode.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="8a54e-109">[in] Um valor igual a [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeração que especifica os atributos do método ou função global.</span><span class="sxs-lookup"><span data-stu-id="8a54e-109">[in] A value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration that specifies the attributes of the method or global function.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="8a54e-110">[in] A assinatura do método.</span><span class="sxs-lookup"><span data-stu-id="8a54e-110">[in] The method signature.</span></span> <span data-ttu-id="8a54e-111">A assinatura é mantida como fornecidos.</span><span class="sxs-lookup"><span data-stu-id="8a54e-111">The signature is persisted as supplied.</span></span> <span data-ttu-id="8a54e-112">Se você precisar especificar informações adicionais para quaisquer parâmetros, use o [imetadataemit:: Setparamprops](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="8a54e-112">If you need to specify additional information for any parameters, use the [IMetaDataEmit::SetParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="8a54e-113">[in] A contagem de bytes em `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="8a54e-113">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="8a54e-114">[in] O endereço do código.</span><span class="sxs-lookup"><span data-stu-id="8a54e-114">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="8a54e-115">[in] Um valor igual a [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeração que especifica os recursos de implementação do método.</span><span class="sxs-lookup"><span data-stu-id="8a54e-115">[in] A value of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the implementation features of the method.</span></span>  
  
 `pmd`  
 <span data-ttu-id="8a54e-116">[out] O token de membro.</span><span class="sxs-lookup"><span data-stu-id="8a54e-116">[out] The member token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a54e-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="8a54e-117">Remarks</span></span>  
 <span data-ttu-id="8a54e-118">A API de metadados garante para persistir os métodos na mesma ordem conforme o chamador emite-los para uma determinada classe delimitadora ou interface, que é especificado no `td` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="8a54e-118">The metadata API guarantees to persist methods in the same order as the caller emits them for a given enclosing class or interface, which is specified in the `td` parameter.</span></span>  
  
 <span data-ttu-id="8a54e-119">Informações adicionais sobre o uso do `DefineMethod` e configurações de parâmetro específica é fornecido abaixo.</span><span class="sxs-lookup"><span data-stu-id="8a54e-119">Additional information regarding the use of `DefineMethod` and particular parameter settings is given below.</span></span>  
  
## <a name="slots-in-the-v-table"></a><span data-ttu-id="8a54e-120">Slots na tabela V</span><span class="sxs-lookup"><span data-stu-id="8a54e-120">Slots in the V-table</span></span>  
 <span data-ttu-id="8a54e-121">O tempo de execução usa as definições de método para configurar os slots de v-table.</span><span class="sxs-lookup"><span data-stu-id="8a54e-121">The runtime uses method definitions to set up v-table slots.</span></span> <span data-ttu-id="8a54e-122">No caso em que um ou mais slots precisam ser ignorada, como para preservar a paridade com o layout de interface COM um método fictício é definido para ocupar o slot ou slots da tabela v. Defina a `dwMethodFlags` para o `mdRTSpecialName` valor da [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeração e especifique o nome como:</span><span class="sxs-lookup"><span data-stu-id="8a54e-122">In the case where one or more slots need to be skipped, such as to preserve parity with a COM interface layout, a dummy method is defined to take up the slot or slots in the v-table; set the `dwMethodFlags` to the `mdRTSpecialName` value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration and specify the name as:</span></span>  
  
 <span data-ttu-id="8a54e-123">VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span><span class="sxs-lookup"><span data-stu-id="8a54e-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span></span>
  
 <span data-ttu-id="8a54e-124">em que *SequenceNumber* é o número de sequência do método e *CountOfSlots* é o número de slots para ignorar a tabela v.</span><span class="sxs-lookup"><span data-stu-id="8a54e-124">where *SequenceNumber* is the sequence number of the method and *CountOfSlots* is the number of slots to skip in the v-table.</span></span> <span data-ttu-id="8a54e-125">Se *CountOfSlots* é omitido, 1 será pressuposto.</span><span class="sxs-lookup"><span data-stu-id="8a54e-125">If *CountOfSlots* is omitted, 1 is assumed.</span></span> <span data-ttu-id="8a54e-126">Esses métodos fictícios não estão acessíveis pelo código gerenciado ou e qualquer tentativa de chamá-los, a partir do código gerenciado ou não gerenciado, gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="8a54e-126">These dummy methods are not callable from either managed or unmanaged code and any attempt to call them, from either managed or unmanaged code, generates an exception.</span></span> <span data-ttu-id="8a54e-127">Sua única finalidade é ocupam espaço na tabela v que o tempo de execução gera para integração COM.</span><span class="sxs-lookup"><span data-stu-id="8a54e-127">Their only purpose is to take up space in the v-table that the runtime generates for COM integration.</span></span>  
  
## <a name="duplicate-methods"></a><span data-ttu-id="8a54e-128">Métodos duplicados</span><span class="sxs-lookup"><span data-stu-id="8a54e-128">Duplicate Methods</span></span>  
 <span data-ttu-id="8a54e-129">Você não deve definir métodos duplicados.</span><span class="sxs-lookup"><span data-stu-id="8a54e-129">You should not define duplicate methods.</span></span> <span data-ttu-id="8a54e-130">Ou seja, você não deve chamar `DefineMethod` com um conjunto duplicado de valores de `td`, `wzName`, e `pvSig` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="8a54e-130">That is, you should not call `DefineMethod` with a duplicate set of values in the `td`, `wzName`, and `pvSig` parameters.</span></span> <span data-ttu-id="8a54e-131">(Esses três parâmetros juntos definem exclusivamente o método.).</span><span class="sxs-lookup"><span data-stu-id="8a54e-131">(These three parameters together uniquely define the method.).</span></span> <span data-ttu-id="8a54e-132">No entanto, você pode usar um triplo duplicado desde que, para uma das definições de método, você deve definir a `mdPrivateScope` bit no `dwMethodFlags` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="8a54e-132">However, you can use a duplicate triple provided that, for one of the method definitions, you set the `mdPrivateScope` bit in the `dwMethodFlags` parameter.</span></span> <span data-ttu-id="8a54e-133">(O `mdPrivateScope` bit significa que o compilador não emitirá uma referência a essa definição de método.)</span><span class="sxs-lookup"><span data-stu-id="8a54e-133">(The `mdPrivateScope` bit means that the compiler will not emit a reference to this method definition.)</span></span>  
  
## <a name="method-implementation-information"></a><span data-ttu-id="8a54e-134">Informações de implementação de método</span><span class="sxs-lookup"><span data-stu-id="8a54e-134">Method Implementation Information</span></span>  
 <span data-ttu-id="8a54e-135">Informações sobre a implementação do método geralmente não são conhecidas no momento em que o método é declarado.</span><span class="sxs-lookup"><span data-stu-id="8a54e-135">Information about the method implementation is often not known at the time the method is declared.</span></span> <span data-ttu-id="8a54e-136">Portanto, não é necessário passar valores de `ulCodeRVA` e `dwImplFlags` parâmetros ao chamar `DefineMethod`.</span><span class="sxs-lookup"><span data-stu-id="8a54e-136">Therefore, you do not need to pass values in the `ulCodeRVA` and `dwImplFlags` parameters when calling `DefineMethod`.</span></span> <span data-ttu-id="8a54e-137">Os valores podem ser fornecidos posteriormente por meio [imetadataemit:: Setmethodimplflags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) ou [imetadataemit:: Setrva](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="8a54e-137">The values can be supplied later through [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) or [IMetaDataEmit::SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), as appropriate.</span></span>  
  
 <span data-ttu-id="8a54e-138">Em algumas situações, como invocação de plataforma (PInvoke) ou cenários de interoperabilidade COM, o corpo do método não será fornecido, e `ulCodeRVA` deve ser definido como zero.</span><span class="sxs-lookup"><span data-stu-id="8a54e-138">In some situations, such as platform invocation (PInvoke) or COM interop scenarios, the method body will not be supplied, and `ulCodeRVA` should be set to zero.</span></span> <span data-ttu-id="8a54e-139">Nessas situações, o método deve não ser marcado como abstratos, porque o tempo de execução localizará a implementação.</span><span class="sxs-lookup"><span data-stu-id="8a54e-139">In these situations, the method should not be tagged as abstract, because the runtime will locate the implementation.</span></span>  
  
## <a name="defining-a-method-for-pinvoke"></a><span data-ttu-id="8a54e-140">Definindo um método para PInvoke</span><span class="sxs-lookup"><span data-stu-id="8a54e-140">Defining a Method for PInvoke</span></span>  
 <span data-ttu-id="8a54e-141">Para cada função não gerenciada a ser chamado por meio do PInvoke, você deve definir um método gerenciado que representa a função de destino não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="8a54e-141">For each unmanaged function to be called through PInvoke, you must define a managed method that represents the target unmanaged function.</span></span> <span data-ttu-id="8a54e-142">Para definir o método gerenciado, use `DefineMethod` com alguns dos parâmetros definidos para determinados valores, dependendo de como o PInvoke é usado:</span><span class="sxs-lookup"><span data-stu-id="8a54e-142">To define the managed method, use `DefineMethod` with some of the parameters set to certain values, depending on the way in which PInvoke is used:</span></span>  
  
-   <span data-ttu-id="8a54e-143">Verdadeiro PInvoke - envolve a invocação de um método externo não gerenciado que reside em uma DLL não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="8a54e-143">True PInvoke - involves invocation of an external unmanaged method that resides in an unmanaged DLL.</span></span>  
  
-   <span data-ttu-id="8a54e-144">PInvoke local - envolve a invocação de um método nativo não gerenciado que está incorporado no módulo gerenciado atual.</span><span class="sxs-lookup"><span data-stu-id="8a54e-144">Local PInvoke - involves invocation of a native unmanaged method that is embedded in the current managed module.</span></span>  
  
 <span data-ttu-id="8a54e-145">As configurações de parâmetro são fornecidas na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="8a54e-145">The parameter settings are given in the following table.</span></span>  
  
|<span data-ttu-id="8a54e-146">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="8a54e-146">Parameter</span></span>|<span data-ttu-id="8a54e-147">Valores para verdadeiro PInvoke</span><span class="sxs-lookup"><span data-stu-id="8a54e-147">Values for true PInvoke</span></span>|<span data-ttu-id="8a54e-148">Valores de PInvoke local</span><span class="sxs-lookup"><span data-stu-id="8a54e-148">Values for local PInvoke</span></span>|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||<span data-ttu-id="8a54e-149">Definir `mdStatic`; desmarque `mdSynchronized` e `mdAbstract`.</span><span class="sxs-lookup"><span data-stu-id="8a54e-149">Set `mdStatic`; clear `mdSynchronized` and `mdAbstract`.</span></span>|  
|`pvSigBlob`|<span data-ttu-id="8a54e-150">Tipos gerenciados do válido common language runtime (CLR) assinatura de um método com parâmetros que são válidos.</span><span class="sxs-lookup"><span data-stu-id="8a54e-150">A valid common language runtime (CLR) method signature with parameters that are valid managed types.</span></span>|<span data-ttu-id="8a54e-151">Tipos gerenciados de uma assinatura de método do CLR válida com parâmetros que são válidos.</span><span class="sxs-lookup"><span data-stu-id="8a54e-151">A valid CLR method signature with parameters that are valid managed types.</span></span>|  
|`ulCodeRVA`||<span data-ttu-id="8a54e-152">0</span><span class="sxs-lookup"><span data-stu-id="8a54e-152">0</span></span>|  
|`dwImplFlags`|<span data-ttu-id="8a54e-153">Definir `miCil` e `miManaged`.</span><span class="sxs-lookup"><span data-stu-id="8a54e-153">Set `miCil` and `miManaged`.</span></span>|<span data-ttu-id="8a54e-154">Definir `miNative` e `miUnmanaged`.</span><span class="sxs-lookup"><span data-stu-id="8a54e-154">Set `miNative` and `miUnmanaged`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8a54e-155">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8a54e-155">Requirements</span></span>  
 <span data-ttu-id="8a54e-156">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a54e-156">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a54e-157">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8a54e-157">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8a54e-158">**Biblioteca:** usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="8a54e-158">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8a54e-159">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a54e-159">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a54e-160">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a54e-160">See Also</span></span>  
 [<span data-ttu-id="8a54e-161">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="8a54e-161">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="8a54e-162">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="8a54e-162">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
