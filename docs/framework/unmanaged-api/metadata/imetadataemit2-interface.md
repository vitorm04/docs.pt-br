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
ms.openlocfilehash: 5a232f30da8812c6f3bd94647d74151312a8593b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493014"
---
# <a name="imetadataemit2-interface"></a><span data-ttu-id="b572a-102">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="b572a-102">IMetaDataEmit2 Interface</span></span>
<span data-ttu-id="b572a-103">Estende a interface [IMetaDataEmit](imetadataemit-interface.md) principalmente para fornecer a capacidade de trabalhar com tipos genéricos.</span><span class="sxs-lookup"><span data-stu-id="b572a-103">Extends the [IMetaDataEmit](imetadataemit-interface.md) interface primarily to provide the ability to work with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b572a-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="b572a-104">Methods</span></span>  
  
|<span data-ttu-id="b572a-105">Método</span><span class="sxs-lookup"><span data-stu-id="b572a-105">Method</span></span>|<span data-ttu-id="b572a-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="b572a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b572a-107">Método DefineGenericParam</span><span class="sxs-lookup"><span data-stu-id="b572a-107">DefineGenericParam Method</span></span>](imetadataemit2-definegenericparam-method.md)|<span data-ttu-id="b572a-108">Cria uma definição para um parâmetro de tipo genérico e Obtém um token para esse parâmetro de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="b572a-108">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>|  
|[<span data-ttu-id="b572a-109">Método DefineMethodSpec</span><span class="sxs-lookup"><span data-stu-id="b572a-109">DefineMethodSpec Method</span></span>](imetadataemit2-definemethodspec-method.md)|<span data-ttu-id="b572a-110">Cria uma instância genérica de um método e Obtém um token para a definição.</span><span class="sxs-lookup"><span data-stu-id="b572a-110">Creates a generic instance of a method, and gets a token to the definition.</span></span>|  
|[<span data-ttu-id="b572a-111">Método GetDeltaSaveSize</span><span class="sxs-lookup"><span data-stu-id="b572a-111">GetDeltaSaveSize Method</span></span>](imetadataemit2-getdeltasavesize-method.md)|<span data-ttu-id="b572a-112">Obtém um valor que indica a diferença no tamanho dos dados necessários para expressar as alterações da sessão de edição e continuação atual.</span><span class="sxs-lookup"><span data-stu-id="b572a-112">Gets a value indicating the difference in size of the data that is required to express the changes for the current edit-and-continue session.</span></span>|  
|[<span data-ttu-id="b572a-113">Método ResetENCLog</span><span class="sxs-lookup"><span data-stu-id="b572a-113">ResetENCLog Method</span></span>](imetadataemit2-resetenclog-method.md)|<span data-ttu-id="b572a-114">Redefine o log de edição e continuação e inicia uma nova sessão.</span><span class="sxs-lookup"><span data-stu-id="b572a-114">Resets the edit-and-continue log and starts a new session.</span></span>|  
|[<span data-ttu-id="b572a-115">Método SaveDelta</span><span class="sxs-lookup"><span data-stu-id="b572a-115">SaveDelta Method</span></span>](imetadataemit2-savedelta-method.md)|<span data-ttu-id="b572a-116">Salva as alterações da sessão de edição e continuação atual para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="b572a-116">Saves changes from the current edit-and-continue session to the specified file.</span></span>|  
|[<span data-ttu-id="b572a-117">Método SaveDeltaToMemory</span><span class="sxs-lookup"><span data-stu-id="b572a-117">SaveDeltaToMemory Method</span></span>](imetadataemit2-savedeltatomemory-method.md)|<span data-ttu-id="b572a-118">Salva as alterações da sessão de edição e continuação atual na memória.</span><span class="sxs-lookup"><span data-stu-id="b572a-118">Saves changes from the current edit-and-continue session to memory.</span></span>|  
|[<span data-ttu-id="b572a-119">Método SaveDeltaToStream</span><span class="sxs-lookup"><span data-stu-id="b572a-119">SaveDeltaToStream Method</span></span>](imetadataemit2-savedeltatostream-method.md)|<span data-ttu-id="b572a-120">Salva as alterações da sessão de edição e continuação atual para o fluxo especificado.</span><span class="sxs-lookup"><span data-stu-id="b572a-120">Saves changes from the current edit-and-continue session to the specified stream.</span></span>|  
|[<span data-ttu-id="b572a-121">Método SetGenericParamProps</span><span class="sxs-lookup"><span data-stu-id="b572a-121">SetGenericParamProps Method</span></span>](imetadataemit2-setgenericparamprops-method.md)|<span data-ttu-id="b572a-122">Define valores de propriedade para a definição de parâmetro genérico referenciada pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="b572a-122">Sets property values for the generic parameter definition referenced by the specified token.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b572a-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b572a-123">Requirements</span></span>  
 <span data-ttu-id="b572a-124">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b572a-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b572a-125">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b572a-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b572a-126">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b572a-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b572a-127">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b572a-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b572a-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="b572a-128">See also</span></span>

- [<span data-ttu-id="b572a-129">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="b572a-129">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="b572a-130">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="b572a-130">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
