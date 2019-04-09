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
ms.openlocfilehash: 80bf9de3eb274bf536b2794ba2ed14e7e9b553cc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157697"
---
# <a name="imetadataemitsetclasslayout-method"></a><span data-ttu-id="a6d8a-102">Método IMetaDataEmit::SetClassLayout</span><span class="sxs-lookup"><span data-stu-id="a6d8a-102">IMetaDataEmit::SetClassLayout Method</span></span>
<span data-ttu-id="a6d8a-103">Conclui o layout dos campos para uma classe que foi definido por uma chamada anterior ao [método DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="a6d8a-103">Completes the layout of fields for a class that has been defined by a prior call to [DefineTypeDef Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6d8a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a6d8a-104">Syntax</span></span>  
  
```  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,   
    [in]  DWORD               dwPackSize,   
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],   
    [in]  ULONG               ulClassSize   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6d8a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a6d8a-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="a6d8a-106">[in] Um `mdTypeDef` token que especifica a classe a ser dispostos.</span><span class="sxs-lookup"><span data-stu-id="a6d8a-106">[in] An `mdTypeDef` token that specifies the class to be laid out.</span></span>  
  
 `dwPackSize`  
 <span data-ttu-id="a6d8a-107">[in] O tamanho de empacotamento: 1, 2, 4, 8 ou 16 bytes.</span><span class="sxs-lookup"><span data-stu-id="a6d8a-107">[in] The packing size: 1, 2, 4, 8 or 16 bytes.</span></span> <span data-ttu-id="a6d8a-108">O tamanho do empacotamento é o número de bytes entre campos adjacentes.</span><span class="sxs-lookup"><span data-stu-id="a6d8a-108">The packing size is the number of bytes between adjacent fields.</span></span>  
  
 `rFieldOffsets`  
 <span data-ttu-id="a6d8a-109">[in] Uma matriz de [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) estruturas, cada um deles especifica um campo da classe e o campo de deslocamento dentro da classe.</span><span class="sxs-lookup"><span data-stu-id="a6d8a-109">[in] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, each of which specifies a field of the class and the field's offset within the class.</span></span> <span data-ttu-id="a6d8a-110">Encerrar a matriz com `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="a6d8a-110">Terminate the array with `mdTokenNil`.</span></span>  
  
 `ulClassSize`  
 <span data-ttu-id="a6d8a-111">[in] O tamanho, em bytes, da classe.</span><span class="sxs-lookup"><span data-stu-id="a6d8a-111">[in] The size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6d8a-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="a6d8a-112">Remarks</span></span>  
 <span data-ttu-id="a6d8a-113">A classe é definida inicialmente por meio da chamada a [imetadataemit:: Definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) método e especificando um dos três layouts para os campos da classe: automático, sequencial ou explícito.</span><span class="sxs-lookup"><span data-stu-id="a6d8a-113">The class is initially defined by calling the [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) method, and specifying one of three layouts for the fields of the class: automatic, sequential, or explicit.</span></span> <span data-ttu-id="a6d8a-114">Normalmente, você usaria o layout automático e permitir que o tempo de execução escolhe a melhor maneira para dispor os campos.</span><span class="sxs-lookup"><span data-stu-id="a6d8a-114">Normally, you would use automatic layout and let the runtime choose the best way to lay out the fields.</span></span>  
  
 <span data-ttu-id="a6d8a-115">No entanto, convém os campos dispostos de acordo com a organização não gerenciadas de código usa.</span><span class="sxs-lookup"><span data-stu-id="a6d8a-115">However, you might want the fields laid out according to the arrangement that unmanaged code uses.</span></span> <span data-ttu-id="a6d8a-116">Nesse caso, escolha o layout explícito ou sequencial e chame `SetClassLayout` para concluir o layout dos campos:</span><span class="sxs-lookup"><span data-stu-id="a6d8a-116">In this case, choose either sequential or explicit layout and call `SetClassLayout` to complete the layout of the fields:</span></span>  
  
-   <span data-ttu-id="a6d8a-117">Layout sequencial: Especifique o tamanho de empacotamento.</span><span class="sxs-lookup"><span data-stu-id="a6d8a-117">Sequential layout: Specify the packing size.</span></span> <span data-ttu-id="a6d8a-118">Um campo é alinhado de acordo com seu tamanho natural ou o tamanho de empacotamento, seja qual for o resultados no deslocamento do campo menor.</span><span class="sxs-lookup"><span data-stu-id="a6d8a-118">A field is aligned according to either its natural size or the packing size, whichever results in the smaller offset of the field.</span></span> <span data-ttu-id="a6d8a-119">Definir `rFieldOffsets` e `ulClassSize` como zero.</span><span class="sxs-lookup"><span data-stu-id="a6d8a-119">Set `rFieldOffsets` and `ulClassSize` to zero.</span></span>  
  
-   <span data-ttu-id="a6d8a-120">Layout explícito: Especifique o deslocamento de cada campo ou especificar o tamanho de classe e o tamanho de empacotamento.</span><span class="sxs-lookup"><span data-stu-id="a6d8a-120">Explicit layout: Either specify the offset of each field or specify the class size and the packing size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6d8a-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a6d8a-121">Requirements</span></span>  
 <span data-ttu-id="a6d8a-122">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6d8a-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6d8a-123">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a6d8a-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a6d8a-124">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="a6d8a-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="a6d8a-125">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="a6d8a-125">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a6d8a-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6d8a-126">See also</span></span>

- [<span data-ttu-id="a6d8a-127">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="a6d8a-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="a6d8a-128">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="a6d8a-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
