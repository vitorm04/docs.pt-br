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
ms.openlocfilehash: 235134c66395f04a87ed4f3325f5cc4cd9fecfc8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemit2-interface"></a><span data-ttu-id="dd857-102">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="dd857-102">IMetaDataEmit2 Interface</span></span>
<span data-ttu-id="dd857-103">Estende o [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface principalmente para oferecer a capacidade de trabalhar com tipos genéricos.</span><span class="sxs-lookup"><span data-stu-id="dd857-103">Extends the [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface primarily to provide the ability to work with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dd857-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="dd857-104">Methods</span></span>  
  
|<span data-ttu-id="dd857-105">Método</span><span class="sxs-lookup"><span data-stu-id="dd857-105">Method</span></span>|<span data-ttu-id="dd857-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="dd857-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dd857-107">Método DefineGenericParam</span><span class="sxs-lookup"><span data-stu-id="dd857-107">DefineGenericParam Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md)|<span data-ttu-id="dd857-108">Cria uma definição para um parâmetro de tipo genérico e obtém um token para esse parâmetro de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="dd857-108">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>|  
|[<span data-ttu-id="dd857-109">Método DefineMethodSpec</span><span class="sxs-lookup"><span data-stu-id="dd857-109">DefineMethodSpec Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md)|<span data-ttu-id="dd857-110">Cria uma instância genérica de um método e recebe um token para a definição.</span><span class="sxs-lookup"><span data-stu-id="dd857-110">Creates a generic instance of a method, and gets a token to the definition.</span></span>|  
|[<span data-ttu-id="dd857-111">Método GetDeltaSaveSize</span><span class="sxs-lookup"><span data-stu-id="dd857-111">GetDeltaSaveSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md)|<span data-ttu-id="dd857-112">Obtém um valor que indica a diferença no tamanho dos dados que é necessário para expressar as alterações para a sessão atual de edit-and-continue.</span><span class="sxs-lookup"><span data-stu-id="dd857-112">Gets a value indicating the difference in size of the data that is required to express the changes for the current edit-and-continue session.</span></span>|  
|[<span data-ttu-id="dd857-113">Método ResetENCLog</span><span class="sxs-lookup"><span data-stu-id="dd857-113">ResetENCLog Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md)|<span data-ttu-id="dd857-114">Redefine o log de edit-and-continue e inicia uma nova sessão.</span><span class="sxs-lookup"><span data-stu-id="dd857-114">Resets the edit-and-continue log and starts a new session.</span></span>|  
|[<span data-ttu-id="dd857-115">Método SaveDelta</span><span class="sxs-lookup"><span data-stu-id="dd857-115">SaveDelta Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedelta-method.md)|<span data-ttu-id="dd857-116">Salva as alterações da sessão atual edit-and-continue para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="dd857-116">Saves changes from the current edit-and-continue session to the specified file.</span></span>|  
|[<span data-ttu-id="dd857-117">Método SaveDeltaToMemory</span><span class="sxs-lookup"><span data-stu-id="dd857-117">SaveDeltaToMemory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)|<span data-ttu-id="dd857-118">Salva as alterações da sessão atual edit-and-continue na memória.</span><span class="sxs-lookup"><span data-stu-id="dd857-118">Saves changes from the current edit-and-continue session to memory.</span></span>|  
|[<span data-ttu-id="dd857-119">Método SaveDeltaToStream</span><span class="sxs-lookup"><span data-stu-id="dd857-119">SaveDeltaToStream Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatostream-method.md)|<span data-ttu-id="dd857-120">Salva as alterações da sessão atual de editar e continuar o fluxo especificado.</span><span class="sxs-lookup"><span data-stu-id="dd857-120">Saves changes from the current edit-and-continue session to the specified stream.</span></span>|  
|[<span data-ttu-id="dd857-121">Método SetGenericParamProps</span><span class="sxs-lookup"><span data-stu-id="dd857-121">SetGenericParamProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-setgenericparamprops-method.md)|<span data-ttu-id="dd857-122">Define valores de propriedade para a definição de parâmetro genérico referenciado por token especificado.</span><span class="sxs-lookup"><span data-stu-id="dd857-122">Sets property values for the generic parameter definition referenced by the specified token.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dd857-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dd857-123">Requirements</span></span>  
 <span data-ttu-id="dd857-124">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd857-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd857-125">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dd857-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dd857-126">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="dd857-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dd857-127">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd857-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd857-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dd857-128">See Also</span></span>  
 [<span data-ttu-id="dd857-129">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="dd857-129">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="dd857-130">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="dd857-130">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
