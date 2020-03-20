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
ms.openlocfilehash: e855868d18fc6cffdd5d92cfa401606caf45b76c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177571"
---
# <a name="imetadataemitsetclasslayout-method"></a><span data-ttu-id="9b47e-102">Método IMetaDataEmit::SetClassLayout</span><span class="sxs-lookup"><span data-stu-id="9b47e-102">IMetaDataEmit::SetClassLayout Method</span></span>
<span data-ttu-id="9b47e-103">Completa o layout dos campos para uma classe definida por uma chamada anterior ao [Método DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="9b47e-103">Completes the layout of fields for a class that has been defined by a prior call to [DefineTypeDef Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b47e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9b47e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,
    [in]  DWORD               dwPackSize,
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],
    [in]  ULONG               ulClassSize
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b47e-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="9b47e-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="9b47e-106">[em] Um `mdTypeDef` token que especifica a classe a ser definida.</span><span class="sxs-lookup"><span data-stu-id="9b47e-106">[in] An `mdTypeDef` token that specifies the class to be laid out.</span></span>  
  
 `dwPackSize`  
 <span data-ttu-id="9b47e-107">[em] O tamanho da embalagem: 1, 2, 4, 8 ou 16 bytes.</span><span class="sxs-lookup"><span data-stu-id="9b47e-107">[in] The packing size: 1, 2, 4, 8 or 16 bytes.</span></span> <span data-ttu-id="9b47e-108">O tamanho da embalagem é o número de bytes entre campos adjacentes.</span><span class="sxs-lookup"><span data-stu-id="9b47e-108">The packing size is the number of bytes between adjacent fields.</span></span>  
  
 `rFieldOffsets`  
 <span data-ttu-id="9b47e-109">[em] Uma matriz de [estruturas COR_FIELD_OFFSET,](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) cada uma das quais especifica um campo da classe e o deslocamento do campo dentro da classe.</span><span class="sxs-lookup"><span data-stu-id="9b47e-109">[in] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, each of which specifies a field of the class and the field's offset within the class.</span></span> <span data-ttu-id="9b47e-110">Termine a `mdTokenNil`matriz com .</span><span class="sxs-lookup"><span data-stu-id="9b47e-110">Terminate the array with `mdTokenNil`.</span></span>  
  
 `ulClassSize`  
 <span data-ttu-id="9b47e-111">[em] O tamanho, em bytes, da classe.</span><span class="sxs-lookup"><span data-stu-id="9b47e-111">[in] The size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b47e-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="9b47e-112">Remarks</span></span>  
 <span data-ttu-id="9b47e-113">A classe é definida inicialmente chamando o método [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) e especificando um dos três layouts para os campos da classe: automático, seqüencial ou explícito.</span><span class="sxs-lookup"><span data-stu-id="9b47e-113">The class is initially defined by calling the [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) method, and specifying one of three layouts for the fields of the class: automatic, sequential, or explicit.</span></span> <span data-ttu-id="9b47e-114">Normalmente, você usaria layout automático e deixaria o tempo de execução escolher a melhor maneira de definir os campos.</span><span class="sxs-lookup"><span data-stu-id="9b47e-114">Normally, you would use automatic layout and let the runtime choose the best way to lay out the fields.</span></span>  
  
 <span data-ttu-id="9b47e-115">No entanto, você pode querer os campos definidos de acordo com o arranjo que o código não gerenciado usa.</span><span class="sxs-lookup"><span data-stu-id="9b47e-115">However, you might want the fields laid out according to the arrangement that unmanaged code uses.</span></span> <span data-ttu-id="9b47e-116">Neste caso, escolha o layout seqüencial `SetClassLayout` ou explícito e ligue para concluir o layout dos campos:</span><span class="sxs-lookup"><span data-stu-id="9b47e-116">In this case, choose either sequential or explicit layout and call `SetClassLayout` to complete the layout of the fields:</span></span>  
  
- <span data-ttu-id="9b47e-117">Layout seqüencial: Especifique o tamanho da embalagem.</span><span class="sxs-lookup"><span data-stu-id="9b47e-117">Sequential layout: Specify the packing size.</span></span> <span data-ttu-id="9b47e-118">Um campo é alinhado de acordo com seu tamanho natural ou o tamanho da embalagem, o que resultar na menor compensação do campo.</span><span class="sxs-lookup"><span data-stu-id="9b47e-118">A field is aligned according to either its natural size or the packing size, whichever results in the smaller offset of the field.</span></span> <span data-ttu-id="9b47e-119">Set `rFieldOffsets` `ulClassSize` e para zero.</span><span class="sxs-lookup"><span data-stu-id="9b47e-119">Set `rFieldOffsets` and `ulClassSize` to zero.</span></span>  
  
- <span data-ttu-id="9b47e-120">Layout explícito: Especifique a compensação de cada campo ou especifique o tamanho da classe e o tamanho da embalagem.</span><span class="sxs-lookup"><span data-stu-id="9b47e-120">Explicit layout: Either specify the offset of each field or specify the class size and the packing size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b47e-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9b47e-121">Requirements</span></span>  
 <span data-ttu-id="9b47e-122">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b47e-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b47e-123">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9b47e-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9b47e-124">**Biblioteca:** Usado como recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9b47e-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9b47e-125">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b47e-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b47e-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="9b47e-126">See also</span></span>

- [<span data-ttu-id="9b47e-127">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="9b47e-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="9b47e-128">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="9b47e-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
