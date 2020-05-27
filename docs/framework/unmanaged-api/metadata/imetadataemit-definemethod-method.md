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
ms.openlocfilehash: 514f227e3c0c385f61090079d2f5214dac9b3924
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004524"
---
# <a name="imetadataemitdefinemethod-method"></a><span data-ttu-id="615e5-102">Método IMetaDataEmit::DefineMethod</span><span class="sxs-lookup"><span data-stu-id="615e5-102">IMetaDataEmit::DefineMethod Method</span></span>
<span data-ttu-id="615e5-103">Cria uma definição para um método ou função global com a assinatura especificada e retorna um token para essa definição de método.</span><span class="sxs-lookup"><span data-stu-id="615e5-103">Creates a definition for a method or global function with the specified signature, and returns a token to that method definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="615e5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="615e5-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="615e5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="615e5-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="615e5-106">no O `mdTypedef` token da classe pai ou da interface pai do método.</span><span class="sxs-lookup"><span data-stu-id="615e5-106">[in] The `mdTypedef` token of the parent class or parent interface of the method.</span></span> <span data-ttu-id="615e5-107">Defina `td` como `mdTokenNil` , se você estiver definindo uma função global.</span><span class="sxs-lookup"><span data-stu-id="615e5-107">Set `td` to `mdTokenNil`, if you are defining a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="615e5-108">no O nome do membro em Unicode.</span><span class="sxs-lookup"><span data-stu-id="615e5-108">[in] The member name in Unicode.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="615e5-109">no Um valor da enumeração [CorMethodAttr](cormethodattr-enumeration.md) que especifica os atributos do método ou da função global.</span><span class="sxs-lookup"><span data-stu-id="615e5-109">[in] A value of the [CorMethodAttr](cormethodattr-enumeration.md) enumeration that specifies the attributes of the method or global function.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="615e5-110">no A assinatura do método.</span><span class="sxs-lookup"><span data-stu-id="615e5-110">[in] The method signature.</span></span> <span data-ttu-id="615e5-111">A assinatura é persistida conforme fornecido.</span><span class="sxs-lookup"><span data-stu-id="615e5-111">The signature is persisted as supplied.</span></span> <span data-ttu-id="615e5-112">Se você precisar especificar informações adicionais para quaisquer parâmetros, use o método [IMetaDataEmit:: SetParamProps](imetadataemit-setparamprops-method.md) .</span><span class="sxs-lookup"><span data-stu-id="615e5-112">If you need to specify additional information for any parameters, use the [IMetaDataEmit::SetParamProps](imetadataemit-setparamprops-method.md) method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="615e5-113">no A contagem de bytes em `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="615e5-113">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="615e5-114">no O endereço do código.</span><span class="sxs-lookup"><span data-stu-id="615e5-114">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="615e5-115">no Um valor da enumeração [CorMethodImpl](cormethodimpl-enumeration.md) que especifica os recursos de implementação do método.</span><span class="sxs-lookup"><span data-stu-id="615e5-115">[in] A value of the [CorMethodImpl](cormethodimpl-enumeration.md) enumeration that specifies the implementation features of the method.</span></span>  
  
 `pmd`  
 <span data-ttu-id="615e5-116">fora O token do membro.</span><span class="sxs-lookup"><span data-stu-id="615e5-116">[out] The member token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="615e5-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="615e5-117">Remarks</span></span>  
 <span data-ttu-id="615e5-118">A API de metadados garante que os métodos persistam na mesma ordem em que o chamador os emite para uma determinada classe ou interface de delimitação, que é especificada no `td` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="615e5-118">The metadata API guarantees to persist methods in the same order as the caller emits them for a given enclosing class or interface, which is specified in the `td` parameter.</span></span>  
  
 <span data-ttu-id="615e5-119">Informações adicionais sobre o uso de `DefineMethod` e configurações de parâmetros específicas são fornecidas abaixo.</span><span class="sxs-lookup"><span data-stu-id="615e5-119">Additional information regarding the use of `DefineMethod` and particular parameter settings is given below.</span></span>  
  
## <a name="slots-in-the-v-table"></a><span data-ttu-id="615e5-120">Slots na tabela V</span><span class="sxs-lookup"><span data-stu-id="615e5-120">Slots in the V-table</span></span>  
 <span data-ttu-id="615e5-121">O tempo de execução usa definições de método para configurar slots de tabela v.</span><span class="sxs-lookup"><span data-stu-id="615e5-121">The runtime uses method definitions to set up v-table slots.</span></span> <span data-ttu-id="615e5-122">No caso em que um ou mais slots precisam ser ignorados, como para preservar a paridade com um layout de interface COM, um método fictício é definido para ocupar o slot ou os slots na tabela v; Defina `dwMethodFlags` como o `mdRTSpecialName` valor da enumeração [CorMethodAttr](cormethodattr-enumeration.md) e especifique o nome como:</span><span class="sxs-lookup"><span data-stu-id="615e5-122">In the case where one or more slots need to be skipped, such as to preserve parity with a COM interface layout, a dummy method is defined to take up the slot or slots in the v-table; set the `dwMethodFlags` to the `mdRTSpecialName` value of the [CorMethodAttr](cormethodattr-enumeration.md) enumeration and specify the name as:</span></span>  
  
 <span data-ttu-id="615e5-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span><span class="sxs-lookup"><span data-stu-id="615e5-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span></span>
  
 <span data-ttu-id="615e5-124">em que *SequenceNumber* é o número de sequência do método e *CountOfSlots* é o número de Slots a serem ignorados na tabela v.</span><span class="sxs-lookup"><span data-stu-id="615e5-124">where *SequenceNumber* is the sequence number of the method and *CountOfSlots* is the number of slots to skip in the v-table.</span></span> <span data-ttu-id="615e5-125">Se *CountOfSlots* for omitido, 1 será assumido.</span><span class="sxs-lookup"><span data-stu-id="615e5-125">If *CountOfSlots* is omitted, 1 is assumed.</span></span> <span data-ttu-id="615e5-126">Esses métodos fictícios não podem ser chamados de código gerenciado ou não gerenciado e qualquer tentativa de chamá-los, a partir de código gerenciado ou não gerenciado, gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="615e5-126">These dummy methods are not callable from either managed or unmanaged code and any attempt to call them, from either managed or unmanaged code, generates an exception.</span></span> <span data-ttu-id="615e5-127">Sua única finalidade é ocupar espaço na tabela v que o tempo de execução gera para a integração COM.</span><span class="sxs-lookup"><span data-stu-id="615e5-127">Their only purpose is to take up space in the v-table that the runtime generates for COM integration.</span></span>  
  
## <a name="duplicate-methods"></a><span data-ttu-id="615e5-128">Métodos duplicados</span><span class="sxs-lookup"><span data-stu-id="615e5-128">Duplicate Methods</span></span>  
 <span data-ttu-id="615e5-129">Você não deve definir métodos duplicados.</span><span class="sxs-lookup"><span data-stu-id="615e5-129">You should not define duplicate methods.</span></span> <span data-ttu-id="615e5-130">Ou seja, você não deve chamar `DefineMethod` com um conjunto duplicado de valores nos `td` `wzName` parâmetros, e `pvSig` .</span><span class="sxs-lookup"><span data-stu-id="615e5-130">That is, you should not call `DefineMethod` with a duplicate set of values in the `td`, `wzName`, and `pvSig` parameters.</span></span> <span data-ttu-id="615e5-131">(Esses três parâmetros definem exclusivamente o método.).</span><span class="sxs-lookup"><span data-stu-id="615e5-131">(These three parameters together uniquely define the method.).</span></span> <span data-ttu-id="615e5-132">No entanto, você pode usar um triplo duplicado que, para uma das definições de método, defina o `mdPrivateScope` bit no `dwMethodFlags` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="615e5-132">However, you can use a duplicate triple provided that, for one of the method definitions, you set the `mdPrivateScope` bit in the `dwMethodFlags` parameter.</span></span> <span data-ttu-id="615e5-133">(O `mdPrivateScope` bit significa que o compilador não emitirá uma referência a essa definição de método.)</span><span class="sxs-lookup"><span data-stu-id="615e5-133">(The `mdPrivateScope` bit means that the compiler will not emit a reference to this method definition.)</span></span>  
  
## <a name="method-implementation-information"></a><span data-ttu-id="615e5-134">Informações de implementação do método</span><span class="sxs-lookup"><span data-stu-id="615e5-134">Method Implementation Information</span></span>  
 <span data-ttu-id="615e5-135">As informações sobre a implementação do método geralmente não são conhecidas no momento em que o método é declarado.</span><span class="sxs-lookup"><span data-stu-id="615e5-135">Information about the method implementation is often not known at the time the method is declared.</span></span> <span data-ttu-id="615e5-136">Portanto, você não precisa passar valores nos `ulCodeRVA` `dwImplFlags` parâmetros e ao chamar `DefineMethod` .</span><span class="sxs-lookup"><span data-stu-id="615e5-136">Therefore, you do not need to pass values in the `ulCodeRVA` and `dwImplFlags` parameters when calling `DefineMethod`.</span></span> <span data-ttu-id="615e5-137">Os valores podem ser fornecidos posteriormente por meio de [IMetaDataEmit:: SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) ou [IMetaDataEmit:: SetRVA](imetadataemit-setrva-method.md), conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="615e5-137">The values can be supplied later through [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) or [IMetaDataEmit::SetRVA](imetadataemit-setrva-method.md), as appropriate.</span></span>  
  
 <span data-ttu-id="615e5-138">Em algumas situações, como a invocação de plataforma (PInvoke) ou cenários de interoperabilidade COM, o corpo do método não será fornecido e `ulCodeRVA` deverá ser definido como zero.</span><span class="sxs-lookup"><span data-stu-id="615e5-138">In some situations, such as platform invocation (PInvoke) or COM interop scenarios, the method body will not be supplied, and `ulCodeRVA` should be set to zero.</span></span> <span data-ttu-id="615e5-139">Nessas situações, o método não deve ser marcado como abstrato, pois o tempo de execução localizará a implementação.</span><span class="sxs-lookup"><span data-stu-id="615e5-139">In these situations, the method should not be tagged as abstract, because the runtime will locate the implementation.</span></span>  
  
## <a name="defining-a-method-for-pinvoke"></a><span data-ttu-id="615e5-140">Definindo um método para PInvoke</span><span class="sxs-lookup"><span data-stu-id="615e5-140">Defining a Method for PInvoke</span></span>  
 <span data-ttu-id="615e5-141">Para cada função não gerenciada a ser chamada por meio de PInvoke, você deve definir um método gerenciado que representa a função de destino não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="615e5-141">For each unmanaged function to be called through PInvoke, you must define a managed method that represents the target unmanaged function.</span></span> <span data-ttu-id="615e5-142">Para definir o método gerenciado, use `DefineMethod` com alguns dos parâmetros definidos para determinados valores, dependendo da maneira como o PInvoke é usado:</span><span class="sxs-lookup"><span data-stu-id="615e5-142">To define the managed method, use `DefineMethod` with some of the parameters set to certain values, depending on the way in which PInvoke is used:</span></span>  
  
- <span data-ttu-id="615e5-143">Verdadeiro PInvoke – envolve a invocação de um método externo não gerenciado que reside em uma DLL não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="615e5-143">True PInvoke - involves invocation of an external unmanaged method that resides in an unmanaged DLL.</span></span>  
  
- <span data-ttu-id="615e5-144">PInvoke local – envolve a invocação de um método nativo não gerenciado que é inserido no módulo gerenciado atual.</span><span class="sxs-lookup"><span data-stu-id="615e5-144">Local PInvoke - involves invocation of a native unmanaged method that is embedded in the current managed module.</span></span>  
  
 <span data-ttu-id="615e5-145">As configurações de parâmetro são fornecidas na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="615e5-145">The parameter settings are given in the following table.</span></span>  
  
|<span data-ttu-id="615e5-146">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="615e5-146">Parameter</span></span>|<span data-ttu-id="615e5-147">Valores para verdadeiro PInvoke</span><span class="sxs-lookup"><span data-stu-id="615e5-147">Values for true PInvoke</span></span>|<span data-ttu-id="615e5-148">Valores para o PInvoke local</span><span class="sxs-lookup"><span data-stu-id="615e5-148">Values for local PInvoke</span></span>|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||<span data-ttu-id="615e5-149">Definir `mdStatic` ; limpar `mdSynchronized` e `mdAbstract` .</span><span class="sxs-lookup"><span data-stu-id="615e5-149">Set `mdStatic`; clear `mdSynchronized` and `mdAbstract`.</span></span>|  
|`pvSigBlob`|<span data-ttu-id="615e5-150">Uma assinatura de método de Common Language Runtime (CLR) válida com parâmetros que são tipos gerenciados válidos.</span><span class="sxs-lookup"><span data-stu-id="615e5-150">A valid common language runtime (CLR) method signature with parameters that are valid managed types.</span></span>|<span data-ttu-id="615e5-151">Uma assinatura de método CLR válida com parâmetros que são tipos gerenciados válidos.</span><span class="sxs-lookup"><span data-stu-id="615e5-151">A valid CLR method signature with parameters that are valid managed types.</span></span>|  
|`ulCodeRVA`||<span data-ttu-id="615e5-152">0</span><span class="sxs-lookup"><span data-stu-id="615e5-152">0</span></span>|  
|`dwImplFlags`|<span data-ttu-id="615e5-153">Definir `miCil` e `miManaged`.</span><span class="sxs-lookup"><span data-stu-id="615e5-153">Set `miCil` and `miManaged`.</span></span>|<span data-ttu-id="615e5-154">Definir `miNative` e `miUnmanaged`.</span><span class="sxs-lookup"><span data-stu-id="615e5-154">Set `miNative` and `miUnmanaged`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="615e5-155">Requisitos</span><span class="sxs-lookup"><span data-stu-id="615e5-155">Requirements</span></span>  
 <span data-ttu-id="615e5-156">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="615e5-156">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="615e5-157">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="615e5-157">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="615e5-158">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="615e5-158">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="615e5-159">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="615e5-159">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="615e5-160">Confira também</span><span class="sxs-lookup"><span data-stu-id="615e5-160">See also</span></span>

- [<span data-ttu-id="615e5-161">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="615e5-161">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="615e5-162">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="615e5-162">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
