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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 87b5b60d75d5d28e100ec75192d0cacf51765927
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62042959"
---
# <a name="imetadataemit2-interface"></a><span data-ttu-id="f7347-102">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="f7347-102">IMetaDataEmit2 Interface</span></span>
<span data-ttu-id="f7347-103">Estende o [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface principalmente para fornecer a capacidade de trabalhar com tipos genéricos.</span><span class="sxs-lookup"><span data-stu-id="f7347-103">Extends the [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface primarily to provide the ability to work with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f7347-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="f7347-104">Methods</span></span>  
  
|<span data-ttu-id="f7347-105">Método</span><span class="sxs-lookup"><span data-stu-id="f7347-105">Method</span></span>|<span data-ttu-id="f7347-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="f7347-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f7347-107">Método DefineGenericParam</span><span class="sxs-lookup"><span data-stu-id="f7347-107">DefineGenericParam Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md)|<span data-ttu-id="f7347-108">Cria uma definição para um parâmetro de tipo genérico e obtém um token para esse parâmetro de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="f7347-108">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>|  
|[<span data-ttu-id="f7347-109">Método DefineMethodSpec</span><span class="sxs-lookup"><span data-stu-id="f7347-109">DefineMethodSpec Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md)|<span data-ttu-id="f7347-110">Cria uma instância genérica de um método e obtém um token para a definição.</span><span class="sxs-lookup"><span data-stu-id="f7347-110">Creates a generic instance of a method, and gets a token to the definition.</span></span>|  
|[<span data-ttu-id="f7347-111">Método GetDeltaSaveSize</span><span class="sxs-lookup"><span data-stu-id="f7347-111">GetDeltaSaveSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md)|<span data-ttu-id="f7347-112">Obtém um valor que indica a diferença no tamanho dos dados que é necessária para expressar as alterações para a sessão atual de editar e continuar.</span><span class="sxs-lookup"><span data-stu-id="f7347-112">Gets a value indicating the difference in size of the data that is required to express the changes for the current edit-and-continue session.</span></span>|  
|[<span data-ttu-id="f7347-113">Método ResetENCLog</span><span class="sxs-lookup"><span data-stu-id="f7347-113">ResetENCLog Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md)|<span data-ttu-id="f7347-114">Redefine o log de editar e continuar e inicia uma nova sessão.</span><span class="sxs-lookup"><span data-stu-id="f7347-114">Resets the edit-and-continue log and starts a new session.</span></span>|  
|[<span data-ttu-id="f7347-115">Método SaveDelta</span><span class="sxs-lookup"><span data-stu-id="f7347-115">SaveDelta Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedelta-method.md)|<span data-ttu-id="f7347-116">Salva as alterações da sessão atual de editar e continuar para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="f7347-116">Saves changes from the current edit-and-continue session to the specified file.</span></span>|  
|[<span data-ttu-id="f7347-117">Método SaveDeltaToMemory</span><span class="sxs-lookup"><span data-stu-id="f7347-117">SaveDeltaToMemory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)|<span data-ttu-id="f7347-118">Salva as alterações da sessão atual de editar e continuar para a memória.</span><span class="sxs-lookup"><span data-stu-id="f7347-118">Saves changes from the current edit-and-continue session to memory.</span></span>|  
|[<span data-ttu-id="f7347-119">Método SaveDeltaToStream</span><span class="sxs-lookup"><span data-stu-id="f7347-119">SaveDeltaToStream Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatostream-method.md)|<span data-ttu-id="f7347-120">Salva as alterações da sessão atual de editar e continuar o fluxo especificado.</span><span class="sxs-lookup"><span data-stu-id="f7347-120">Saves changes from the current edit-and-continue session to the specified stream.</span></span>|  
|[<span data-ttu-id="f7347-121">Método SetGenericParamProps</span><span class="sxs-lookup"><span data-stu-id="f7347-121">SetGenericParamProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-setgenericparamprops-method.md)|<span data-ttu-id="f7347-122">Define valores de propriedade para a definição de parâmetro genérico referenciada pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="f7347-122">Sets property values for the generic parameter definition referenced by the specified token.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f7347-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f7347-123">Requirements</span></span>  
 <span data-ttu-id="f7347-124">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7347-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7347-125">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f7347-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f7347-126">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="f7347-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f7347-127">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7347-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7347-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f7347-128">See also</span></span>

- [<span data-ttu-id="f7347-129">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="f7347-129">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="f7347-130">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="f7347-130">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
