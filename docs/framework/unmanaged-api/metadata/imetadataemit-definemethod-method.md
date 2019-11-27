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
ms.openlocfilehash: c46b075341742aac605537a08b762b3cf47ef35b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431809"
---
# <a name="imetadataemitdefinemethod-method"></a><span data-ttu-id="11b5b-102">Método IMetaDataEmit::DefineMethod</span><span class="sxs-lookup"><span data-stu-id="11b5b-102">IMetaDataEmit::DefineMethod Method</span></span>
<span data-ttu-id="11b5b-103">Cria uma definição para um método ou função global com a assinatura especificada e retorna um token para essa definição de método.</span><span class="sxs-lookup"><span data-stu-id="11b5b-103">Creates a definition for a method or global function with the specified signature, and returns a token to that method definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11b5b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="11b5b-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="11b5b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="11b5b-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="11b5b-106">no O token `mdTypedef` da classe pai ou da interface pai do método.</span><span class="sxs-lookup"><span data-stu-id="11b5b-106">[in] The `mdTypedef` token of the parent class or parent interface of the method.</span></span> <span data-ttu-id="11b5b-107">Defina `td` como `mdTokenNil`, se você estiver definindo uma função global.</span><span class="sxs-lookup"><span data-stu-id="11b5b-107">Set `td` to `mdTokenNil`, if you are defining a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="11b5b-108">no O nome do membro em Unicode.</span><span class="sxs-lookup"><span data-stu-id="11b5b-108">[in] The member name in Unicode.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="11b5b-109">no Um valor da enumeração [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) que especifica os atributos do método ou da função global.</span><span class="sxs-lookup"><span data-stu-id="11b5b-109">[in] A value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration that specifies the attributes of the method or global function.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="11b5b-110">no A assinatura do método.</span><span class="sxs-lookup"><span data-stu-id="11b5b-110">[in] The method signature.</span></span> <span data-ttu-id="11b5b-111">A assinatura é persistida conforme fornecido.</span><span class="sxs-lookup"><span data-stu-id="11b5b-111">The signature is persisted as supplied.</span></span> <span data-ttu-id="11b5b-112">Se você precisar especificar informações adicionais para quaisquer parâmetros, use o método [IMetaDataEmit:: SetParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) .</span><span class="sxs-lookup"><span data-stu-id="11b5b-112">If you need to specify additional information for any parameters, use the [IMetaDataEmit::SetParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="11b5b-113">no A contagem de bytes em `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="11b5b-113">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="11b5b-114">no O endereço do código.</span><span class="sxs-lookup"><span data-stu-id="11b5b-114">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="11b5b-115">no Um valor da enumeração [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) que especifica os recursos de implementação do método.</span><span class="sxs-lookup"><span data-stu-id="11b5b-115">[in] A value of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the implementation features of the method.</span></span>  
  
 `pmd`  
 <span data-ttu-id="11b5b-116">fora O token do membro.</span><span class="sxs-lookup"><span data-stu-id="11b5b-116">[out] The member token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11b5b-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="11b5b-117">Remarks</span></span>  
 <span data-ttu-id="11b5b-118">A API de metadados garante que os métodos persistam na mesma ordem em que o chamador os emite para uma determinada classe ou interface de delimitação, que é especificada no parâmetro `td`.</span><span class="sxs-lookup"><span data-stu-id="11b5b-118">The metadata API guarantees to persist methods in the same order as the caller emits them for a given enclosing class or interface, which is specified in the `td` parameter.</span></span>  
  
 <span data-ttu-id="11b5b-119">Informações adicionais sobre o uso de `DefineMethod` e configurações de parâmetros específicas são fornecidas abaixo.</span><span class="sxs-lookup"><span data-stu-id="11b5b-119">Additional information regarding the use of `DefineMethod` and particular parameter settings is given below.</span></span>  
  
## <a name="slots-in-the-v-table"></a><span data-ttu-id="11b5b-120">Slots na tabela V</span><span class="sxs-lookup"><span data-stu-id="11b5b-120">Slots in the V-table</span></span>  
 <span data-ttu-id="11b5b-121">O tempo de execução usa definições de método para configurar slots de tabela v.</span><span class="sxs-lookup"><span data-stu-id="11b5b-121">The runtime uses method definitions to set up v-table slots.</span></span> <span data-ttu-id="11b5b-122">No caso em que um ou mais slots precisam ser ignorados, como para preservar a paridade com um layout de interface COM, um método fictício é definido para ocupar o slot ou os slots na tabela v; Defina o `dwMethodFlags` para o valor de `mdRTSpecialName` da enumeração [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) e especifique o nome como:</span><span class="sxs-lookup"><span data-stu-id="11b5b-122">In the case where one or more slots need to be skipped, such as to preserve parity with a COM interface layout, a dummy method is defined to take up the slot or slots in the v-table; set the `dwMethodFlags` to the `mdRTSpecialName` value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration and specify the name as:</span></span>  
  
 <span data-ttu-id="11b5b-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span><span class="sxs-lookup"><span data-stu-id="11b5b-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span></span>
  
 <span data-ttu-id="11b5b-124">em que *SequenceNumber* é o número de sequência do método e *CountOfSlots* é o número de Slots a serem ignorados na tabela v.</span><span class="sxs-lookup"><span data-stu-id="11b5b-124">where *SequenceNumber* is the sequence number of the method and *CountOfSlots* is the number of slots to skip in the v-table.</span></span> <span data-ttu-id="11b5b-125">Se *CountOfSlots* for omitido, 1 será assumido.</span><span class="sxs-lookup"><span data-stu-id="11b5b-125">If *CountOfSlots* is omitted, 1 is assumed.</span></span> <span data-ttu-id="11b5b-126">Esses métodos fictícios não podem ser chamados de código gerenciado ou não gerenciado e qualquer tentativa de chamá-los, a partir de código gerenciado ou não gerenciado, gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="11b5b-126">These dummy methods are not callable from either managed or unmanaged code and any attempt to call them, from either managed or unmanaged code, generates an exception.</span></span> <span data-ttu-id="11b5b-127">Sua única finalidade é ocupar espaço na tabela v que o tempo de execução gera para a integração COM.</span><span class="sxs-lookup"><span data-stu-id="11b5b-127">Their only purpose is to take up space in the v-table that the runtime generates for COM integration.</span></span>  
  
## <a name="duplicate-methods"></a><span data-ttu-id="11b5b-128">Métodos duplicados</span><span class="sxs-lookup"><span data-stu-id="11b5b-128">Duplicate Methods</span></span>  
 <span data-ttu-id="11b5b-129">Você não deve definir métodos duplicados.</span><span class="sxs-lookup"><span data-stu-id="11b5b-129">You should not define duplicate methods.</span></span> <span data-ttu-id="11b5b-130">Ou seja, você não deve chamar `DefineMethod` com um conjunto duplicado de valores nos parâmetros `td`, `wzName`e `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="11b5b-130">That is, you should not call `DefineMethod` with a duplicate set of values in the `td`, `wzName`, and `pvSig` parameters.</span></span> <span data-ttu-id="11b5b-131">(Esses três parâmetros definem exclusivamente o método.).</span><span class="sxs-lookup"><span data-stu-id="11b5b-131">(These three parameters together uniquely define the method.).</span></span> <span data-ttu-id="11b5b-132">No entanto, você pode usar um triplo de duplicatas fornecido que, para uma das definições de método, você define o `mdPrivateScope` bit no parâmetro `dwMethodFlags`.</span><span class="sxs-lookup"><span data-stu-id="11b5b-132">However, you can use a duplicate triple provided that, for one of the method definitions, you set the `mdPrivateScope` bit in the `dwMethodFlags` parameter.</span></span> <span data-ttu-id="11b5b-133">(O bit de `mdPrivateScope` significa que o compilador não emitirá uma referência para essa definição de método.)</span><span class="sxs-lookup"><span data-stu-id="11b5b-133">(The `mdPrivateScope` bit means that the compiler will not emit a reference to this method definition.)</span></span>  
  
## <a name="method-implementation-information"></a><span data-ttu-id="11b5b-134">Informações de implementação do método</span><span class="sxs-lookup"><span data-stu-id="11b5b-134">Method Implementation Information</span></span>  
 <span data-ttu-id="11b5b-135">As informações sobre a implementação do método geralmente não são conhecidas no momento em que o método é declarado.</span><span class="sxs-lookup"><span data-stu-id="11b5b-135">Information about the method implementation is often not known at the time the method is declared.</span></span> <span data-ttu-id="11b5b-136">Portanto, você não precisa passar valores nos parâmetros `ulCodeRVA` e `dwImplFlags` ao chamar `DefineMethod`.</span><span class="sxs-lookup"><span data-stu-id="11b5b-136">Therefore, you do not need to pass values in the `ulCodeRVA` and `dwImplFlags` parameters when calling `DefineMethod`.</span></span> <span data-ttu-id="11b5b-137">Os valores podem ser fornecidos posteriormente por meio de [IMetaDataEmit:: SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) ou [IMetaDataEmit:: SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="11b5b-137">The values can be supplied later through [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) or [IMetaDataEmit::SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), as appropriate.</span></span>  
  
 <span data-ttu-id="11b5b-138">Em algumas situações, como a invocação de plataforma (PInvoke) ou cenários de interoperabilidade COM, o corpo do método não será fornecido e `ulCodeRVA` deverá ser definido como zero.</span><span class="sxs-lookup"><span data-stu-id="11b5b-138">In some situations, such as platform invocation (PInvoke) or COM interop scenarios, the method body will not be supplied, and `ulCodeRVA` should be set to zero.</span></span> <span data-ttu-id="11b5b-139">Nessas situações, o método não deve ser marcado como abstrato, pois o tempo de execução localizará a implementação.</span><span class="sxs-lookup"><span data-stu-id="11b5b-139">In these situations, the method should not be tagged as abstract, because the runtime will locate the implementation.</span></span>  
  
## <a name="defining-a-method-for-pinvoke"></a><span data-ttu-id="11b5b-140">Definindo um método para PInvoke</span><span class="sxs-lookup"><span data-stu-id="11b5b-140">Defining a Method for PInvoke</span></span>  
 <span data-ttu-id="11b5b-141">Para cada função não gerenciada a ser chamada por meio de PInvoke, você deve definir um método gerenciado que representa a função de destino não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="11b5b-141">For each unmanaged function to be called through PInvoke, you must define a managed method that represents the target unmanaged function.</span></span> <span data-ttu-id="11b5b-142">Para definir o método gerenciado, use `DefineMethod` com alguns dos parâmetros definidos para determinados valores, dependendo da maneira como o PInvoke é usado:</span><span class="sxs-lookup"><span data-stu-id="11b5b-142">To define the managed method, use `DefineMethod` with some of the parameters set to certain values, depending on the way in which PInvoke is used:</span></span>  
  
- <span data-ttu-id="11b5b-143">Verdadeiro PInvoke – envolve a invocação de um método externo não gerenciado que reside em uma DLL não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="11b5b-143">True PInvoke - involves invocation of an external unmanaged method that resides in an unmanaged DLL.</span></span>  
  
- <span data-ttu-id="11b5b-144">PInvoke local – envolve a invocação de um método nativo não gerenciado que é inserido no módulo gerenciado atual.</span><span class="sxs-lookup"><span data-stu-id="11b5b-144">Local PInvoke - involves invocation of a native unmanaged method that is embedded in the current managed module.</span></span>  
  
 <span data-ttu-id="11b5b-145">As configurações de parâmetro são fornecidas na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="11b5b-145">The parameter settings are given in the following table.</span></span>  
  
|<span data-ttu-id="11b5b-146">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="11b5b-146">Parameter</span></span>|<span data-ttu-id="11b5b-147">Valores para verdadeiro PInvoke</span><span class="sxs-lookup"><span data-stu-id="11b5b-147">Values for true PInvoke</span></span>|<span data-ttu-id="11b5b-148">Valores para o PInvoke local</span><span class="sxs-lookup"><span data-stu-id="11b5b-148">Values for local PInvoke</span></span>|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||<span data-ttu-id="11b5b-149">Definir `mdStatic`; Desmarque `mdSynchronized` e `mdAbstract`.</span><span class="sxs-lookup"><span data-stu-id="11b5b-149">Set `mdStatic`; clear `mdSynchronized` and `mdAbstract`.</span></span>|  
|`pvSigBlob`|<span data-ttu-id="11b5b-150">Uma assinatura de método de Common Language Runtime (CLR) válida com parâmetros que são tipos gerenciados válidos.</span><span class="sxs-lookup"><span data-stu-id="11b5b-150">A valid common language runtime (CLR) method signature with parameters that are valid managed types.</span></span>|<span data-ttu-id="11b5b-151">Uma assinatura de método CLR válida com parâmetros que são tipos gerenciados válidos.</span><span class="sxs-lookup"><span data-stu-id="11b5b-151">A valid CLR method signature with parameters that are valid managed types.</span></span>|  
|`ulCodeRVA`||<span data-ttu-id="11b5b-152">0</span><span class="sxs-lookup"><span data-stu-id="11b5b-152">0</span></span>|  
|`dwImplFlags`|<span data-ttu-id="11b5b-153">Defina `miCil` e `miManaged`.</span><span class="sxs-lookup"><span data-stu-id="11b5b-153">Set `miCil` and `miManaged`.</span></span>|<span data-ttu-id="11b5b-154">Defina `miNative` e `miUnmanaged`.</span><span class="sxs-lookup"><span data-stu-id="11b5b-154">Set `miNative` and `miUnmanaged`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="11b5b-155">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="11b5b-155">Requirements</span></span>  
 <span data-ttu-id="11b5b-156">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11b5b-156">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11b5b-157">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="11b5b-157">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="11b5b-158">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="11b5b-158">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="11b5b-159">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11b5b-159">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11b5b-160">Consulte também</span><span class="sxs-lookup"><span data-stu-id="11b5b-160">See also</span></span>

- [<span data-ttu-id="11b5b-161">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="11b5b-161">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="11b5b-162">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="11b5b-162">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
