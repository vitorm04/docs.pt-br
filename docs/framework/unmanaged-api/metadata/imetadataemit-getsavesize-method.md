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
ms.openlocfilehash: 22c0a317777a12294ba7a90f7af1ceeca3ad0a47
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009256"
---
# <a name="imetadataemitgetsavesize-method"></a><span data-ttu-id="c1e42-102">Método IMetaDataEmit::GetSaveSize</span><span class="sxs-lookup"><span data-stu-id="c1e42-102">IMetaDataEmit::GetSaveSize Method</span></span>
<span data-ttu-id="c1e42-103">Obtém o tamanho binário estimado do assembly e seus metadados no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="c1e42-103">Gets the estimated binary size of the assembly and its metadata in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1e42-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c1e42-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1e42-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c1e42-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="c1e42-106">no Um valor da enumeração [CorSaveSize](corsavesize-enumeration.md) que especifica se um tamanho preciso ou aproximado deve ser obtido.</span><span class="sxs-lookup"><span data-stu-id="c1e42-106">[in] A value of the [CorSaveSize](corsavesize-enumeration.md) enumeration that specifies whether to get an accurate or approximate size.</span></span> <span data-ttu-id="c1e42-107">Somente três valores são válidos: cssAccurate, cssQuick e cssDiscardTransientCAs:</span><span class="sxs-lookup"><span data-stu-id="c1e42-107">Only three values are valid: cssAccurate, cssQuick, and cssDiscardTransientCAs:</span></span>  
  
- <span data-ttu-id="c1e42-108">cssAccurate retorna o tamanho exato da gravação, mas leva mais tempo para calcular.</span><span class="sxs-lookup"><span data-stu-id="c1e42-108">cssAccurate returns the exact save size but takes longer to calculate.</span></span>  
  
- <span data-ttu-id="c1e42-109">cssQuick retorna um tamanho, preenchido para segurança, mas leva menos tempo para calcular.</span><span class="sxs-lookup"><span data-stu-id="c1e42-109">cssQuick returns a size, padded for safety, but takes less time to calculate.</span></span>  
  
- <span data-ttu-id="c1e42-110">cssDiscardTransientCAs informa `GetSaveSize` que pode gerar atributos personalizados descartados.</span><span class="sxs-lookup"><span data-stu-id="c1e42-110">cssDiscardTransientCAs tells `GetSaveSize` that it can throw away discardable custom attributes.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="c1e42-111">fora Um ponteiro para o tamanho necessário para salvar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="c1e42-111">[out] A pointer to the size that is required to save the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1e42-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="c1e42-112">Remarks</span></span>  
 <span data-ttu-id="c1e42-113">`GetSaveSize`Calcula o espaço necessário, em bytes, para salvar o assembly e todos os seus metadados no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="c1e42-113">`GetSaveSize` calculates the space required, in bytes, to save the assembly and all its metadata in the current scope.</span></span> <span data-ttu-id="c1e42-114">(Uma chamada para o método [IMetaDataEmit:: SaveToStream](imetadataemit-savetostream-method.md) emitiria esse número de bytes.)</span><span class="sxs-lookup"><span data-stu-id="c1e42-114">(A call to the [IMetaDataEmit::SaveToStream](imetadataemit-savetostream-method.md) method would emit this number of bytes.)</span></span>  
  
 <span data-ttu-id="c1e42-115">Se o chamador implementar a interface [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) (por meio de [IMetaDataEmit:: SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) ou [IMetaDataEmit:: Merge](imetadataemit-merge-method.md)), o `GetSaveSize` executará duas passagens sobre os metadados para otimizá-la e compactá-la.</span><span class="sxs-lookup"><span data-stu-id="c1e42-115">If the caller implements the [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) interface (through [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) or [IMetaDataEmit::Merge](imetadataemit-merge-method.md)), `GetSaveSize` will perform two passes over the metadata to optimize and compress it.</span></span> <span data-ttu-id="c1e42-116">Caso contrário, nenhuma otimização será executada.</span><span class="sxs-lookup"><span data-stu-id="c1e42-116">Otherwise, no optimizations are performed.</span></span>  
  
 <span data-ttu-id="c1e42-117">Se a otimização for executada, a primeira passagem simplesmente classificará as estruturas de metadados para ajustar o desempenho das pesquisas de tempo de importação.</span><span class="sxs-lookup"><span data-stu-id="c1e42-117">If optimization is performed, the first pass simply sorts the metadata structures to tune the performance of import-time searches.</span></span> <span data-ttu-id="c1e42-118">Em geral, essa etapa resulta na movimentação de registros, com o efeito colateral de que os tokens retidos pela ferramenta para referência futura são invalidados.</span><span class="sxs-lookup"><span data-stu-id="c1e42-118">This step typically results in moving records around, with the side effect that tokens retained by the tool for future reference are invalidated.</span></span> <span data-ttu-id="c1e42-119">No entanto, os metadados não informam o chamador dessas alterações de token até depois da segunda passagem.</span><span class="sxs-lookup"><span data-stu-id="c1e42-119">The metadata does not inform the caller of these token changes until after the second pass, however.</span></span> <span data-ttu-id="c1e42-120">Na segunda passagem, são executadas várias otimizações que se destinam a reduzir o tamanho geral dos metadados, como a otimização de ausência (Associação antecipada) `mdTypeRef` e `mdMemberRef` os tokens quando a referência é para um tipo ou membro declarado no escopo de metadados atual.</span><span class="sxs-lookup"><span data-stu-id="c1e42-120">In the second pass, various optimizations are performed that are intended to reduce the overall size of the metadata, such as optimizing away (early binding) `mdTypeRef` and `mdMemberRef` tokens when the reference is to a type or member that is declared in the current metadata scope.</span></span> <span data-ttu-id="c1e42-121">Nessa passagem, ocorre outra rodada de mapeamento de token.</span><span class="sxs-lookup"><span data-stu-id="c1e42-121">In this pass, another round of token mapping occurs.</span></span> <span data-ttu-id="c1e42-122">Após essa passagem, o mecanismo de metadados notifica o chamador, por meio `IMapToken` de sua interface, de quaisquer valores de token alterados.</span><span class="sxs-lookup"><span data-stu-id="c1e42-122">After this pass, the metadata engine notifies the caller, through its `IMapToken` interface, of any changed token values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1e42-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c1e42-123">Requirements</span></span>  
 <span data-ttu-id="c1e42-124">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1e42-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1e42-125">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c1e42-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c1e42-126">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c1e42-126">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c1e42-127">**.NET Framework versões:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1e42-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1e42-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="c1e42-128">See also</span></span>

- [<span data-ttu-id="c1e42-129">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="c1e42-129">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="c1e42-130">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="c1e42-130">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
