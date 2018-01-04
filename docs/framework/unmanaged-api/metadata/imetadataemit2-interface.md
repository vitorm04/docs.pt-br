---
title: Interface IMetaDataEmit2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit2
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit2
helpviewer_keywords: IMetaDataEmit2 interface [.NET Framework metadata]
ms.assetid: 866dc96b-bbfc-4c0f-80c2-38ce93072106
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 94180a1f844ac43d8a42be59ac4fca807a70ec70
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemit2-interface"></a><span data-ttu-id="7c902-102">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="7c902-102">IMetaDataEmit2 Interface</span></span>
<span data-ttu-id="7c902-103">Estende o [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface principalmente para oferecer a capacidade de trabalhar com tipos genéricos.</span><span class="sxs-lookup"><span data-stu-id="7c902-103">Extends the [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface primarily to provide the ability to work with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7c902-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="7c902-104">Methods</span></span>  
  
|<span data-ttu-id="7c902-105">Método</span><span class="sxs-lookup"><span data-stu-id="7c902-105">Method</span></span>|<span data-ttu-id="7c902-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="7c902-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7c902-107">Método DefineGenericParam</span><span class="sxs-lookup"><span data-stu-id="7c902-107">DefineGenericParam Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md)|<span data-ttu-id="7c902-108">Cria uma definição para um parâmetro de tipo genérico e obtém um token para esse parâmetro de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="7c902-108">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>|  
|[<span data-ttu-id="7c902-109">Método DefineMethodSpec</span><span class="sxs-lookup"><span data-stu-id="7c902-109">DefineMethodSpec Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md)|<span data-ttu-id="7c902-110">Cria uma instância genérica de um método e recebe um token para a definição.</span><span class="sxs-lookup"><span data-stu-id="7c902-110">Creates a generic instance of a method, and gets a token to the definition.</span></span>|  
|[<span data-ttu-id="7c902-111">Método GetDeltaSaveSize</span><span class="sxs-lookup"><span data-stu-id="7c902-111">GetDeltaSaveSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md)|<span data-ttu-id="7c902-112">Obtém um valor que indica a diferença no tamanho dos dados que é necessário para expressar as alterações para a sessão atual de edit-and-continue.</span><span class="sxs-lookup"><span data-stu-id="7c902-112">Gets a value indicating the difference in size of the data that is required to express the changes for the current edit-and-continue session.</span></span>|  
|[<span data-ttu-id="7c902-113">Método ResetENCLog</span><span class="sxs-lookup"><span data-stu-id="7c902-113">ResetENCLog Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md)|<span data-ttu-id="7c902-114">Redefine o log de edit-and-continue e inicia uma nova sessão.</span><span class="sxs-lookup"><span data-stu-id="7c902-114">Resets the edit-and-continue log and starts a new session.</span></span>|  
|[<span data-ttu-id="7c902-115">Método SaveDelta</span><span class="sxs-lookup"><span data-stu-id="7c902-115">SaveDelta Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedelta-method.md)|<span data-ttu-id="7c902-116">Salva as alterações da sessão atual edit-and-continue para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="7c902-116">Saves changes from the current edit-and-continue session to the specified file.</span></span>|  
|[<span data-ttu-id="7c902-117">Método SaveDeltaToMemory</span><span class="sxs-lookup"><span data-stu-id="7c902-117">SaveDeltaToMemory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)|<span data-ttu-id="7c902-118">Salva as alterações da sessão atual edit-and-continue na memória.</span><span class="sxs-lookup"><span data-stu-id="7c902-118">Saves changes from the current edit-and-continue session to memory.</span></span>|  
|[<span data-ttu-id="7c902-119">Método SaveDeltaToStream</span><span class="sxs-lookup"><span data-stu-id="7c902-119">SaveDeltaToStream Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatostream-method.md)|<span data-ttu-id="7c902-120">Salva as alterações da sessão atual de editar e continuar o fluxo especificado.</span><span class="sxs-lookup"><span data-stu-id="7c902-120">Saves changes from the current edit-and-continue session to the specified stream.</span></span>|  
|[<span data-ttu-id="7c902-121">Método SetGenericParamProps</span><span class="sxs-lookup"><span data-stu-id="7c902-121">SetGenericParamProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-setgenericparamprops-method.md)|<span data-ttu-id="7c902-122">Define valores de propriedade para a definição de parâmetro genérico referenciado por token especificado.</span><span class="sxs-lookup"><span data-stu-id="7c902-122">Sets property values for the generic parameter definition referenced by the specified token.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7c902-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7c902-123">Requirements</span></span>  
 <span data-ttu-id="7c902-124">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c902-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c902-125">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7c902-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7c902-126">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="7c902-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7c902-127">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c902-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c902-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c902-128">See Also</span></span>  
 [<span data-ttu-id="7c902-129">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="7c902-129">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="7c902-130">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="7c902-130">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
