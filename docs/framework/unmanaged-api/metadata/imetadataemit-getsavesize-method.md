---
title: Método IMetaDataEmit::GetSaveSize
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetSaveSize
helpviewer_keywords:
- IMetaDataEmit::GetSaveSize method [.NET Framework metadata]
- GetSaveSize method [.NET Framework metadata]
ms.assetid: 8aea2e2c-23a3-4cda-9a06-e19f97383830
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7337222f7f419c68ae21d604d1673158acca85ba
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777396"
---
# <a name="imetadataemitgetsavesize-method"></a><span data-ttu-id="c369b-102">Método IMetaDataEmit::GetSaveSize</span><span class="sxs-lookup"><span data-stu-id="c369b-102">IMetaDataEmit::GetSaveSize Method</span></span>
<span data-ttu-id="c369b-103">Obtém o tamanho estimado de binário de assembly e seus metadados no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="c369b-103">Gets the estimated binary size of the assembly and its metadata in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c369b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c369b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c369b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c369b-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="c369b-106">[in] Um valor igual a [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) enumeração que especifica se deve obter um tamanho aproximado ou preciso.</span><span class="sxs-lookup"><span data-stu-id="c369b-106">[in] A value of the [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) enumeration that specifies whether to get an accurate or approximate size.</span></span> <span data-ttu-id="c369b-107">Apenas três valores são válidos: cssAccurate, cssQuick e cssDiscardTransientCAs:</span><span class="sxs-lookup"><span data-stu-id="c369b-107">Only three values are valid: cssAccurate, cssQuick, and cssDiscardTransientCAs:</span></span>  
  
- <span data-ttu-id="c369b-108">cssAccurate retorna Salvar tamanho exato, mas leva mais tempo para calcular.</span><span class="sxs-lookup"><span data-stu-id="c369b-108">cssAccurate returns the exact save size but takes longer to calculate.</span></span>  
  
- <span data-ttu-id="c369b-109">cssQuick retorna um tamanho preenchido para segurança, mas leva menos tempo para calcular.</span><span class="sxs-lookup"><span data-stu-id="c369b-109">cssQuick returns a size, padded for safety, but takes less time to calculate.</span></span>  
  
- <span data-ttu-id="c369b-110">informa ao cssDiscardTransientCAs `GetSaveSize` que ele pode jogar fora descartáveis atributos personalizados.</span><span class="sxs-lookup"><span data-stu-id="c369b-110">cssDiscardTransientCAs tells `GetSaveSize` that it can throw away discardable custom attributes.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="c369b-111">[out] Um ponteiro para o tamanho que é necessário para salvar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="c369b-111">[out] A pointer to the size that is required to save the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c369b-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="c369b-112">Remarks</span></span>  
 <span data-ttu-id="c369b-113">`GetSaveSize` calcula o espaço necessário, em bytes, para salvar o assembly e todos os seus metadados no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="c369b-113">`GetSaveSize` calculates the space required, in bytes, to save the assembly and all its metadata in the current scope.</span></span> <span data-ttu-id="c369b-114">(Uma chamada para o [imetadataemit:: Savetostream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) método seria emitir esse número de bytes.)</span><span class="sxs-lookup"><span data-stu-id="c369b-114">(A call to the [IMetaDataEmit::SaveToStream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) method would emit this number of bytes.)</span></span>  
  
 <span data-ttu-id="c369b-115">Se o chamador implementa o [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) interface (por meio de [imetadataemit:: Sethandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) ou [imetadataemit:: Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` executará duas passagens sobre os metadados para otimizar e compactá-lo.</span><span class="sxs-lookup"><span data-stu-id="c369b-115">If the caller implements the [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) interface (through [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) or [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` will perform two passes over the metadata to optimize and compress it.</span></span> <span data-ttu-id="c369b-116">Caso contrário, nenhuma otimização é executada.</span><span class="sxs-lookup"><span data-stu-id="c369b-116">Otherwise, no optimizations are performed.</span></span>  
  
 <span data-ttu-id="c369b-117">Se a otimização é executada, a primeira passagem simplesmente classifica as estruturas de metadados para ajustar o desempenho de pesquisas do momento da importação.</span><span class="sxs-lookup"><span data-stu-id="c369b-117">If optimization is performed, the first pass simply sorts the metadata structures to tune the performance of import-time searches.</span></span> <span data-ttu-id="c369b-118">Esta etapa normalmente resulta na movimentação de registros, com o efeito colateral que os tokens retidos pela ferramenta para referência futura são invalidados.</span><span class="sxs-lookup"><span data-stu-id="c369b-118">This step typically results in moving records around, with the side effect that tokens retained by the tool for future reference are invalidated.</span></span> <span data-ttu-id="c369b-119">Os metadados não informar o chamador dessas alterações token até após a segunda passagem, no entanto.</span><span class="sxs-lookup"><span data-stu-id="c369b-119">The metadata does not inform the caller of these token changes until after the second pass, however.</span></span> <span data-ttu-id="c369b-120">Na segunda etapa, várias otimizações são executadas que se destinam a reduzir o tamanho geral dos metadados, como otimização ausente (vinculação inicial) `mdTypeRef` e `mdMemberRef` tokens quando a referência é para um tipo ou membro é declarado no escopo de metadados atual.</span><span class="sxs-lookup"><span data-stu-id="c369b-120">In the second pass, various optimizations are performed that are intended to reduce the overall size of the metadata, such as optimizing away (early binding) `mdTypeRef` and `mdMemberRef` tokens when the reference is to a type or member that is declared in the current metadata scope.</span></span> <span data-ttu-id="c369b-121">Essa etapa, ocorre outra rodada de mapeamento de token.</span><span class="sxs-lookup"><span data-stu-id="c369b-121">In this pass, another round of token mapping occurs.</span></span> <span data-ttu-id="c369b-122">Após essa etapa, o mecanismo de metadados notifica o chamador por meio de seu `IMapToken` interface, de qualquer tiver alterado os valores de token.</span><span class="sxs-lookup"><span data-stu-id="c369b-122">After this pass, the metadata engine notifies the caller, through its `IMapToken` interface, of any changed token values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c369b-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c369b-123">Requirements</span></span>  
 <span data-ttu-id="c369b-124">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c369b-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c369b-125">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c369b-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c369b-126">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="c369b-126">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c369b-127">**Versões do .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c369b-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c369b-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c369b-128">See also</span></span>

- [<span data-ttu-id="c369b-129">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="c369b-129">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="c369b-130">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="c369b-130">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
