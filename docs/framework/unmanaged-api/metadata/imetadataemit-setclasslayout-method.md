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
ms.openlocfilehash: 5214298c6ad9594548ab45ed583cb5b14ce1f30d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441771"
---
# <a name="imetadataemitsetclasslayout-method"></a><span data-ttu-id="4fdd4-102">Método IMetaDataEmit::SetClassLayout</span><span class="sxs-lookup"><span data-stu-id="4fdd4-102">IMetaDataEmit::SetClassLayout Method</span></span>
<span data-ttu-id="4fdd4-103">Conclui o layout de campos para uma classe que foi definida por uma chamada anterior ao [método DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="4fdd4-103">Completes the layout of fields for a class that has been defined by a prior call to [DefineTypeDef Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fdd4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4fdd4-104">Syntax</span></span>  
  
```cpp  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,   
    [in]  DWORD               dwPackSize,   
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],   
    [in]  ULONG               ulClassSize   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4fdd4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4fdd4-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="4fdd4-106">no Um token `mdTypeDef` que especifica a classe a ser disposta.</span><span class="sxs-lookup"><span data-stu-id="4fdd4-106">[in] An `mdTypeDef` token that specifies the class to be laid out.</span></span>  
  
 `dwPackSize`  
 <span data-ttu-id="4fdd4-107">no O tamanho da embalagem: 1, 2, 4, 8 ou 16 bytes.</span><span class="sxs-lookup"><span data-stu-id="4fdd4-107">[in] The packing size: 1, 2, 4, 8 or 16 bytes.</span></span> <span data-ttu-id="4fdd4-108">O tamanho da embalagem é o número de bytes entre os campos adjacentes.</span><span class="sxs-lookup"><span data-stu-id="4fdd4-108">The packing size is the number of bytes between adjacent fields.</span></span>  
  
 `rFieldOffsets`  
 <span data-ttu-id="4fdd4-109">no Uma matriz de estruturas [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) , cada uma delas especifica um campo da classe e o deslocamento do campo dentro da classe.</span><span class="sxs-lookup"><span data-stu-id="4fdd4-109">[in] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, each of which specifies a field of the class and the field's offset within the class.</span></span> <span data-ttu-id="4fdd4-110">Encerre a matriz com `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="4fdd4-110">Terminate the array with `mdTokenNil`.</span></span>  
  
 `ulClassSize`  
 <span data-ttu-id="4fdd4-111">no O tamanho, em bytes, da classe.</span><span class="sxs-lookup"><span data-stu-id="4fdd4-111">[in] The size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4fdd4-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="4fdd4-112">Remarks</span></span>  
 <span data-ttu-id="4fdd4-113">A classe é definida inicialmente chamando o método [IMetaDataEmit::D efinetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) e especificando um dos três layouts para os campos da classe: automático, sequencial ou explícito.</span><span class="sxs-lookup"><span data-stu-id="4fdd4-113">The class is initially defined by calling the [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) method, and specifying one of three layouts for the fields of the class: automatic, sequential, or explicit.</span></span> <span data-ttu-id="4fdd4-114">Normalmente, você usaria o layout automático e permite que o tempo de execução escolha a melhor maneira de modelar os campos.</span><span class="sxs-lookup"><span data-stu-id="4fdd4-114">Normally, you would use automatic layout and let the runtime choose the best way to lay out the fields.</span></span>  
  
 <span data-ttu-id="4fdd4-115">No entanto, talvez você queira que os campos sejam dispostos de acordo com a organização usada pelo código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="4fdd4-115">However, you might want the fields laid out according to the arrangement that unmanaged code uses.</span></span> <span data-ttu-id="4fdd4-116">Nesse caso, escolha o layout sequencial ou explícito e chame `SetClassLayout` para concluir o layout dos campos:</span><span class="sxs-lookup"><span data-stu-id="4fdd4-116">In this case, choose either sequential or explicit layout and call `SetClassLayout` to complete the layout of the fields:</span></span>  
  
- <span data-ttu-id="4fdd4-117">Layout sequencial: especifique o tamanho da embalagem.</span><span class="sxs-lookup"><span data-stu-id="4fdd4-117">Sequential layout: Specify the packing size.</span></span> <span data-ttu-id="4fdd4-118">Um campo é alinhado de acordo com seu tamanho natural ou o tamanho da embalagem, o que resultar no deslocamento menor do campo.</span><span class="sxs-lookup"><span data-stu-id="4fdd4-118">A field is aligned according to either its natural size or the packing size, whichever results in the smaller offset of the field.</span></span> <span data-ttu-id="4fdd4-119">Defina `rFieldOffsets` e `ulClassSize` como zero.</span><span class="sxs-lookup"><span data-stu-id="4fdd4-119">Set `rFieldOffsets` and `ulClassSize` to zero.</span></span>  
  
- <span data-ttu-id="4fdd4-120">Layout explícito: especifique o deslocamento de cada campo ou especifique o tamanho da classe e o tamanho da embalagem.</span><span class="sxs-lookup"><span data-stu-id="4fdd4-120">Explicit layout: Either specify the offset of each field or specify the class size and the packing size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fdd4-121">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="4fdd4-121">Requirements</span></span>  
 <span data-ttu-id="4fdd4-122">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fdd4-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fdd4-123">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4fdd4-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4fdd4-124">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4fdd4-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4fdd4-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fdd4-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fdd4-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4fdd4-126">See also</span></span>

- [<span data-ttu-id="4fdd4-127">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="4fdd4-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="4fdd4-128">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="4fdd4-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
