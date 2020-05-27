---
title: Interface IMetaDataDispenserEx
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx
helpviewer_keywords:
- IMetaDataDispenserEx interface [.NET Framework metadata]
ms.assetid: 78b3629e-77a2-4406-89c3-56b5cc2c4594
topic_type:
- apiref
ms.openlocfilehash: 96f0c0c254ce255581ac2937c805096918ab29e8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008047"
---
# <a name="imetadatadispenserex-interface"></a><span data-ttu-id="0afe5-102">Interface IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="0afe5-102">IMetaDataDispenserEx Interface</span></span>
<span data-ttu-id="0afe5-103">Estende a interface de [interface IMetaDataDispenser](imetadatadispenser-interface.md) para fornecer a capacidade de controlar como as APIs de metadados operam no escopo de metadados atual.</span><span class="sxs-lookup"><span data-stu-id="0afe5-103">Extends the [IMetaDataDispenser Interface](imetadatadispenser-interface.md) interface to provide the capability to control how the metadata APIs operate on the current metadata scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0afe5-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="0afe5-104">Methods</span></span>  
  
|<span data-ttu-id="0afe5-105">Método</span><span class="sxs-lookup"><span data-stu-id="0afe5-105">Method</span></span>|<span data-ttu-id="0afe5-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="0afe5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0afe5-107">Método FindAssembly</span><span class="sxs-lookup"><span data-stu-id="0afe5-107">FindAssembly Method</span></span>](imetadatadispenserex-findassembly-method.md)|<span data-ttu-id="0afe5-108">Este método não está implementado.</span><span class="sxs-lookup"><span data-stu-id="0afe5-108">This method is not implemented.</span></span> <span data-ttu-id="0afe5-109">Se chamado, ele retornará E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="0afe5-109">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="0afe5-110">Método FindAssemblyModule</span><span class="sxs-lookup"><span data-stu-id="0afe5-110">FindAssemblyModule Method</span></span>](imetadatadispenserex-findassemblymodule-method.md)|<span data-ttu-id="0afe5-111">Este método não está implementado.</span><span class="sxs-lookup"><span data-stu-id="0afe5-111">This method is not implemented.</span></span> <span data-ttu-id="0afe5-112">Se chamado, ele retornará E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="0afe5-112">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="0afe5-113">Método GetCORSystemDirectory</span><span class="sxs-lookup"><span data-stu-id="0afe5-113">GetCORSystemDirectory Method</span></span>](imetadatadispenserex-getcorsystemdirectory-method.md)|<span data-ttu-id="0afe5-114">Obtém o diretório que contém o Common Language Runtime atual (CLR).</span><span class="sxs-lookup"><span data-stu-id="0afe5-114">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="0afe5-115">Esse método só tem suporte para uso por depuradores fora do processo.</span><span class="sxs-lookup"><span data-stu-id="0afe5-115">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="0afe5-116">Se for chamado de outro componente, ele retornará E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="0afe5-116">If called from another component, it will return E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="0afe5-117">Método GetOption</span><span class="sxs-lookup"><span data-stu-id="0afe5-117">GetOption Method</span></span>](imetadatadispenserex-getoption-method.md)|<span data-ttu-id="0afe5-118">Obtém o valor da opção especificada para o escopo de metadados atual.</span><span class="sxs-lookup"><span data-stu-id="0afe5-118">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="0afe5-119">A opção controla como as chamadas para o escopo de metadados atual são tratadas.</span><span class="sxs-lookup"><span data-stu-id="0afe5-119">The option controls how calls to the current metadata scope are handled.</span></span>|  
|[<span data-ttu-id="0afe5-120">Método OpenScopeOnITypeInfo</span><span class="sxs-lookup"><span data-stu-id="0afe5-120">OpenScopeOnITypeInfo Method</span></span>](imetadatadispenserex-openscopeonitypeinfo-method.md)|<span data-ttu-id="0afe5-121">Este método não está implementado.</span><span class="sxs-lookup"><span data-stu-id="0afe5-121">This method is not implemented.</span></span> <span data-ttu-id="0afe5-122">Se chamado, ele retornará E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="0afe5-122">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="0afe5-123">Método SetOption</span><span class="sxs-lookup"><span data-stu-id="0afe5-123">SetOption Method</span></span>](imetadatadispenserex-setoption-method.md)|<span data-ttu-id="0afe5-124">Define a opção especificada para um determinado valor para o escopo de metadados atual.</span><span class="sxs-lookup"><span data-stu-id="0afe5-124">Sets the specified option to a given value for the current metadata scope.</span></span> <span data-ttu-id="0afe5-125">A opção controla como as chamadas para o escopo de metadados atual são tratadas.</span><span class="sxs-lookup"><span data-stu-id="0afe5-125">The option controls how calls to the current metadata scope are handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0afe5-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0afe5-126">Requirements</span></span>  
 <span data-ttu-id="0afe5-127">**Plataforma:** Consulte [requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0afe5-127">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0afe5-128">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0afe5-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0afe5-129">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0afe5-129">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0afe5-130">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0afe5-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0afe5-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="0afe5-131">See also</span></span>

- [<span data-ttu-id="0afe5-132">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="0afe5-132">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="0afe5-133">Interface IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="0afe5-133">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
- [<span data-ttu-id="0afe5-134">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="0afe5-134">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="0afe5-135">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="0afe5-135">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
