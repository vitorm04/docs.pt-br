---
title: Interface IMetaDataEmit2
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2
helpviewer_keywords:
- IMetaDataEmit2 interface [.NET Framework metadata]
ms.assetid: 866dc96b-bbfc-4c0f-80c2-38ce93072106
topic_type:
- apiref
ms.openlocfilehash: 7ceae6f7713ab0eb1feff550838325df0ea52de2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447920"
---
# <a name="imetadataemit2-interface"></a><span data-ttu-id="f3122-102">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="f3122-102">IMetaDataEmit2 Interface</span></span>
<span data-ttu-id="f3122-103">Estende a interface [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) principalmente para fornecer a capacidade de trabalhar com tipos genéricos.</span><span class="sxs-lookup"><span data-stu-id="f3122-103">Extends the [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface primarily to provide the ability to work with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f3122-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="f3122-104">Methods</span></span>  
  
|<span data-ttu-id="f3122-105">Método</span><span class="sxs-lookup"><span data-stu-id="f3122-105">Method</span></span>|<span data-ttu-id="f3122-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="f3122-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f3122-107">Método DefineGenericParam</span><span class="sxs-lookup"><span data-stu-id="f3122-107">DefineGenericParam Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md)|<span data-ttu-id="f3122-108">Cria uma definição para um parâmetro de tipo genérico e Obtém um token para esse parâmetro de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="f3122-108">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>|  
|[<span data-ttu-id="f3122-109">Método DefineMethodSpec</span><span class="sxs-lookup"><span data-stu-id="f3122-109">DefineMethodSpec Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md)|<span data-ttu-id="f3122-110">Cria uma instância genérica de um método e Obtém um token para a definição.</span><span class="sxs-lookup"><span data-stu-id="f3122-110">Creates a generic instance of a method, and gets a token to the definition.</span></span>|  
|[<span data-ttu-id="f3122-111">Método GetDeltaSaveSize</span><span class="sxs-lookup"><span data-stu-id="f3122-111">GetDeltaSaveSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md)|<span data-ttu-id="f3122-112">Obtém um valor que indica a diferença no tamanho dos dados necessários para expressar as alterações da sessão de edição e continuação atual.</span><span class="sxs-lookup"><span data-stu-id="f3122-112">Gets a value indicating the difference in size of the data that is required to express the changes for the current edit-and-continue session.</span></span>|  
|[<span data-ttu-id="f3122-113">Método ResetENCLog</span><span class="sxs-lookup"><span data-stu-id="f3122-113">ResetENCLog Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md)|<span data-ttu-id="f3122-114">Redefine o log de edição e continuação e inicia uma nova sessão.</span><span class="sxs-lookup"><span data-stu-id="f3122-114">Resets the edit-and-continue log and starts a new session.</span></span>|  
|[<span data-ttu-id="f3122-115">Método SaveDelta</span><span class="sxs-lookup"><span data-stu-id="f3122-115">SaveDelta Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedelta-method.md)|<span data-ttu-id="f3122-116">Salva as alterações da sessão de edição e continuação atual para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="f3122-116">Saves changes from the current edit-and-continue session to the specified file.</span></span>|  
|[<span data-ttu-id="f3122-117">Método SaveDeltaToMemory</span><span class="sxs-lookup"><span data-stu-id="f3122-117">SaveDeltaToMemory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)|<span data-ttu-id="f3122-118">Salva as alterações da sessão de edição e continuação atual na memória.</span><span class="sxs-lookup"><span data-stu-id="f3122-118">Saves changes from the current edit-and-continue session to memory.</span></span>|  
|[<span data-ttu-id="f3122-119">Método SaveDeltaToStream</span><span class="sxs-lookup"><span data-stu-id="f3122-119">SaveDeltaToStream Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatostream-method.md)|<span data-ttu-id="f3122-120">Salva as alterações da sessão de edição e continuação atual para o fluxo especificado.</span><span class="sxs-lookup"><span data-stu-id="f3122-120">Saves changes from the current edit-and-continue session to the specified stream.</span></span>|  
|[<span data-ttu-id="f3122-121">Método SetGenericParamProps</span><span class="sxs-lookup"><span data-stu-id="f3122-121">SetGenericParamProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-setgenericparamprops-method.md)|<span data-ttu-id="f3122-122">Define valores de propriedade para a definição de parâmetro genérico referenciada pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="f3122-122">Sets property values for the generic parameter definition referenced by the specified token.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f3122-123">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="f3122-123">Requirements</span></span>  
 <span data-ttu-id="f3122-124">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3122-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3122-125">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f3122-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f3122-126">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f3122-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f3122-127">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3122-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3122-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3122-128">See also</span></span>

- [<span data-ttu-id="f3122-129">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="f3122-129">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="f3122-130">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="f3122-130">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
