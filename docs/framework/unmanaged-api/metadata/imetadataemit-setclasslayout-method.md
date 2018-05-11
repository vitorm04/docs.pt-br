---
title: Método IMetaDataEmit::SetClassLayout
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetClassLayout
helpviewer_keywords:
- IMetaDataEmit::SetClassLayout method [.NET Framework metadata]
- SetClassLayout method [.NET Framework metadata]
ms.assetid: 2576c449-388d-4434-a0e1-9f53991e11b6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e22cf8e540bfdb53ad243640dac110b5750e53e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitsetclasslayout-method"></a><span data-ttu-id="0aa59-102">Método IMetaDataEmit::SetClassLayout</span><span class="sxs-lookup"><span data-stu-id="0aa59-102">IMetaDataEmit::SetClassLayout Method</span></span>
<span data-ttu-id="0aa59-103">Conclui o layout dos campos de uma classe que tenha sido definido por uma chamada anterior ao [método DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="0aa59-103">Completes the layout of fields for a class that has been defined by a prior call to [DefineTypeDef Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0aa59-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0aa59-104">Syntax</span></span>  
  
```  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,   
    [in]  DWORD               dwPackSize,   
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],   
    [in]  ULONG               ulClassSize   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0aa59-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0aa59-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="0aa59-106">[in] Um `mdTypeDef` token que especifica a classe a ser dispostos.</span><span class="sxs-lookup"><span data-stu-id="0aa59-106">[in] An `mdTypeDef` token that specifies the class to be laid out.</span></span>  
  
 `dwPackSize`  
 <span data-ttu-id="0aa59-107">[in] O tamanho de remessa: 1, 2, 4, 8 ou 16 bytes.</span><span class="sxs-lookup"><span data-stu-id="0aa59-107">[in] The packing size: 1, 2, 4, 8 or 16 bytes.</span></span> <span data-ttu-id="0aa59-108">O tamanho de empacotamento é o número de bytes entre campos adjacentes.</span><span class="sxs-lookup"><span data-stu-id="0aa59-108">The packing size is the number of bytes between adjacent fields.</span></span>  
  
 `rFieldOffsets`  
 <span data-ttu-id="0aa59-109">[in] Uma matriz de [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) estruturas, cada uma delas Especifica um campo da classe e o campo de deslocamento dentro da classe.</span><span class="sxs-lookup"><span data-stu-id="0aa59-109">[in] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, each of which specifies a field of the class and the field's offset within the class.</span></span> <span data-ttu-id="0aa59-110">Encerrar a matriz com `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="0aa59-110">Terminate the array with `mdTokenNil`.</span></span>  
  
 `ulClassSize`  
 <span data-ttu-id="0aa59-111">[in] O tamanho, em bytes, da classe.</span><span class="sxs-lookup"><span data-stu-id="0aa59-111">[in] The size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0aa59-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="0aa59-112">Remarks</span></span>  
 <span data-ttu-id="0aa59-113">A classe é definida inicialmente chamando o [Definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) método e especificando um dos três layouts para os campos da classe: automático, sequencial ou explícito.</span><span class="sxs-lookup"><span data-stu-id="0aa59-113">The class is initially defined by calling the [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) method, and specifying one of three layouts for the fields of the class: automatic, sequential, or explicit.</span></span> <span data-ttu-id="0aa59-114">Normalmente, você usaria o layout automático e permitir que o tempo de execução escolhe a melhor maneira para dispor os campos.</span><span class="sxs-lookup"><span data-stu-id="0aa59-114">Normally, you would use automatic layout and let the runtime choose the best way to lay out the fields.</span></span>  
  
 <span data-ttu-id="0aa59-115">Entretanto, você pode querer os campos organizados de acordo com a organização que usa código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="0aa59-115">However, you might want the fields laid out according to the arrangement that unmanaged code uses.</span></span> <span data-ttu-id="0aa59-116">Nesse caso, escolha o layout explícito ou sequencial e chame `SetClassLayout` para concluir o layout dos campos:</span><span class="sxs-lookup"><span data-stu-id="0aa59-116">In this case, choose either sequential or explicit layout and call `SetClassLayout` to complete the layout of the fields:</span></span>  
  
-   <span data-ttu-id="0aa59-117">Layout sequencial: especifique o tamanho de remessa.</span><span class="sxs-lookup"><span data-stu-id="0aa59-117">Sequential layout: Specify the packing size.</span></span> <span data-ttu-id="0aa59-118">Um campo é alinhado de acordo com seu tamanho natural ou o tamanho de empacotamento, o que resulta no deslocamento menor do campo.</span><span class="sxs-lookup"><span data-stu-id="0aa59-118">A field is aligned according to either its natural size or the packing size, whichever results in the smaller offset of the field.</span></span> <span data-ttu-id="0aa59-119">Definir `rFieldOffsets` e `ulClassSize` como zero.</span><span class="sxs-lookup"><span data-stu-id="0aa59-119">Set `rFieldOffsets` and `ulClassSize` to zero.</span></span>  
  
-   <span data-ttu-id="0aa59-120">Layout explícito: especifique o deslocamento de cada campo ou especifique o tamanho de classe e o tamanho de remessa.</span><span class="sxs-lookup"><span data-stu-id="0aa59-120">Explicit layout: Either specify the offset of each field or specify the class size and the packing size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0aa59-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0aa59-121">Requirements</span></span>  
 <span data-ttu-id="0aa59-122">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0aa59-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0aa59-123">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0aa59-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0aa59-124">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="0aa59-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0aa59-125">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0aa59-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0aa59-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0aa59-126">See Also</span></span>  
 [<span data-ttu-id="0aa59-127">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="0aa59-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="0aa59-128">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="0aa59-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
