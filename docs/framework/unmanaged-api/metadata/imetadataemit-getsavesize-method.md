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
ms.openlocfilehash: 125a63638a41707b8eed918253cb1f93abb907eb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434327"
---
# <a name="imetadataemitgetsavesize-method"></a><span data-ttu-id="f895b-102">Método IMetaDataEmit::GetSaveSize</span><span class="sxs-lookup"><span data-stu-id="f895b-102">IMetaDataEmit::GetSaveSize Method</span></span>
<span data-ttu-id="f895b-103">Obtém o tamanho binário estimado do assembly e seus metadados no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="f895b-103">Gets the estimated binary size of the assembly and its metadata in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f895b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f895b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f895b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f895b-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="f895b-106">no Um valor da enumeração [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) que especifica se um tamanho preciso ou aproximado deve ser obtido.</span><span class="sxs-lookup"><span data-stu-id="f895b-106">[in] A value of the [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) enumeration that specifies whether to get an accurate or approximate size.</span></span> <span data-ttu-id="f895b-107">Somente três valores são válidos: cssAccurate, cssQuick e cssDiscardTransientCAs:</span><span class="sxs-lookup"><span data-stu-id="f895b-107">Only three values are valid: cssAccurate, cssQuick, and cssDiscardTransientCAs:</span></span>  
  
- <span data-ttu-id="f895b-108">cssAccurate retorna o tamanho exato da gravação, mas leva mais tempo para calcular.</span><span class="sxs-lookup"><span data-stu-id="f895b-108">cssAccurate returns the exact save size but takes longer to calculate.</span></span>  
  
- <span data-ttu-id="f895b-109">cssQuick retorna um tamanho, preenchido para segurança, mas leva menos tempo para calcular.</span><span class="sxs-lookup"><span data-stu-id="f895b-109">cssQuick returns a size, padded for safety, but takes less time to calculate.</span></span>  
  
- <span data-ttu-id="f895b-110">cssDiscardTransientCAs informa `GetSaveSize` que ele pode gerar atributos personalizados descartados.</span><span class="sxs-lookup"><span data-stu-id="f895b-110">cssDiscardTransientCAs tells `GetSaveSize` that it can throw away discardable custom attributes.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="f895b-111">fora Um ponteiro para o tamanho necessário para salvar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="f895b-111">[out] A pointer to the size that is required to save the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f895b-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="f895b-112">Remarks</span></span>  
 <span data-ttu-id="f895b-113">`GetSaveSize` calcula o espaço necessário, em bytes, para salvar o assembly e todos os seus metadados no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="f895b-113">`GetSaveSize` calculates the space required, in bytes, to save the assembly and all its metadata in the current scope.</span></span> <span data-ttu-id="f895b-114">(Uma chamada para o método [IMetaDataEmit:: SaveToStream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) emitiria esse número de bytes.)</span><span class="sxs-lookup"><span data-stu-id="f895b-114">(A call to the [IMetaDataEmit::SaveToStream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) method would emit this number of bytes.)</span></span>  
  
 <span data-ttu-id="f895b-115">Se o chamador implementar a interface [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) (por meio de [IMetaDataEmit:: SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) ou [IMetaDataEmit:: Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` executará duas passagens sobre os metadados para otimizá-la e compactá-la.</span><span class="sxs-lookup"><span data-stu-id="f895b-115">If the caller implements the [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) interface (through [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) or [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` will perform two passes over the metadata to optimize and compress it.</span></span> <span data-ttu-id="f895b-116">Caso contrário, nenhuma otimização será executada.</span><span class="sxs-lookup"><span data-stu-id="f895b-116">Otherwise, no optimizations are performed.</span></span>  
  
 <span data-ttu-id="f895b-117">Se a otimização for executada, a primeira passagem simplesmente classificará as estruturas de metadados para ajustar o desempenho das pesquisas de tempo de importação.</span><span class="sxs-lookup"><span data-stu-id="f895b-117">If optimization is performed, the first pass simply sorts the metadata structures to tune the performance of import-time searches.</span></span> <span data-ttu-id="f895b-118">Em geral, essa etapa resulta na movimentação de registros, com o efeito colateral de que os tokens retidos pela ferramenta para referência futura são invalidados.</span><span class="sxs-lookup"><span data-stu-id="f895b-118">This step typically results in moving records around, with the side effect that tokens retained by the tool for future reference are invalidated.</span></span> <span data-ttu-id="f895b-119">No entanto, os metadados não informam o chamador dessas alterações de token até depois da segunda passagem.</span><span class="sxs-lookup"><span data-stu-id="f895b-119">The metadata does not inform the caller of these token changes until after the second pass, however.</span></span> <span data-ttu-id="f895b-120">Na segunda passagem, são executadas várias otimizações que se destinam a reduzir o tamanho geral dos metadados, como a otimização de `mdTypeRef` (Associação antecipada) e `mdMemberRef` tokens quando a referência é para um tipo ou membro declarado no escopo de metadados atual.</span><span class="sxs-lookup"><span data-stu-id="f895b-120">In the second pass, various optimizations are performed that are intended to reduce the overall size of the metadata, such as optimizing away (early binding) `mdTypeRef` and `mdMemberRef` tokens when the reference is to a type or member that is declared in the current metadata scope.</span></span> <span data-ttu-id="f895b-121">Nessa passagem, ocorre outra rodada de mapeamento de token.</span><span class="sxs-lookup"><span data-stu-id="f895b-121">In this pass, another round of token mapping occurs.</span></span> <span data-ttu-id="f895b-122">Após essa passagem, o mecanismo de metadados notifica o chamador, por meio de sua interface de `IMapToken`, de quaisquer valores de token alterados.</span><span class="sxs-lookup"><span data-stu-id="f895b-122">After this pass, the metadata engine notifies the caller, through its `IMapToken` interface, of any changed token values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f895b-123">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="f895b-123">Requirements</span></span>  
 <span data-ttu-id="f895b-124">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f895b-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f895b-125">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f895b-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f895b-126">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f895b-126">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f895b-127">**Versões do .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f895b-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f895b-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f895b-128">See also</span></span>

- [<span data-ttu-id="f895b-129">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="f895b-129">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="f895b-130">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="f895b-130">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
