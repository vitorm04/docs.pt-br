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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 96475086b1244ae75ed692dd10cb693af0be9af7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992596"
---
# <a name="imetadatadispenserex-interface"></a><span data-ttu-id="05eb9-102">Interface IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="05eb9-102">IMetaDataDispenserEx Interface</span></span>
<span data-ttu-id="05eb9-103">Estende o [IMetaDataDispenser Interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) interface para fornecer a capacidade de controlar como as APIs de metadados operam no escopo atual de metadados.</span><span class="sxs-lookup"><span data-stu-id="05eb9-103">Extends the [IMetaDataDispenser Interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) interface to provide the capability to control how the metadata APIs operate on the current metadata scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="05eb9-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="05eb9-104">Methods</span></span>  
  
|<span data-ttu-id="05eb9-105">Método</span><span class="sxs-lookup"><span data-stu-id="05eb9-105">Method</span></span>|<span data-ttu-id="05eb9-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="05eb9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="05eb9-107">Método FindAssembly</span><span class="sxs-lookup"><span data-stu-id="05eb9-107">FindAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassembly-method.md)|<span data-ttu-id="05eb9-108">Este método não está implementado.</span><span class="sxs-lookup"><span data-stu-id="05eb9-108">This method is not implemented.</span></span> <span data-ttu-id="05eb9-109">Se chamado, ele retornará E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="05eb9-109">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="05eb9-110">Método FindAssemblyModule</span><span class="sxs-lookup"><span data-stu-id="05eb9-110">FindAssemblyModule Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassemblymodule-method.md)|<span data-ttu-id="05eb9-111">Este método não está implementado.</span><span class="sxs-lookup"><span data-stu-id="05eb9-111">This method is not implemented.</span></span> <span data-ttu-id="05eb9-112">Se chamado, ele retornará E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="05eb9-112">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="05eb9-113">Método GetCORSystemDirectory</span><span class="sxs-lookup"><span data-stu-id="05eb9-113">GetCORSystemDirectory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getcorsystemdirectory-method.md)|<span data-ttu-id="05eb9-114">Obtém o diretório que mantém o atual common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="05eb9-114">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="05eb9-115">Esse método tem suporte apenas para uso por depuradores out-of-process.</span><span class="sxs-lookup"><span data-stu-id="05eb9-115">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="05eb9-116">Se chamado de outro componente, ele retornará E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="05eb9-116">If called from another component, it will return E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="05eb9-117">Método GetOption</span><span class="sxs-lookup"><span data-stu-id="05eb9-117">GetOption Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getoption-method.md)|<span data-ttu-id="05eb9-118">Obtém o valor da opção especificada para o escopo de metadados atual.</span><span class="sxs-lookup"><span data-stu-id="05eb9-118">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="05eb9-119">A opção controla como as chamadas para o escopo de metadados atual são tratadas.</span><span class="sxs-lookup"><span data-stu-id="05eb9-119">The option controls how calls to the current metadata scope are handled.</span></span>|  
|[<span data-ttu-id="05eb9-120">Método OpenScopeOnITypeInfo</span><span class="sxs-lookup"><span data-stu-id="05eb9-120">OpenScopeOnITypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-openscopeonitypeinfo-method.md)|<span data-ttu-id="05eb9-121">Este método não está implementado.</span><span class="sxs-lookup"><span data-stu-id="05eb9-121">This method is not implemented.</span></span> <span data-ttu-id="05eb9-122">Se chamado, ele retornará E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="05eb9-122">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="05eb9-123">Método SetOption</span><span class="sxs-lookup"><span data-stu-id="05eb9-123">SetOption Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)|<span data-ttu-id="05eb9-124">Define a opção especificada para um determinado valor para o escopo de metadados atual.</span><span class="sxs-lookup"><span data-stu-id="05eb9-124">Sets the specified option to a given value for the current metadata scope.</span></span> <span data-ttu-id="05eb9-125">A opção controla como as chamadas para o escopo de metadados atual são tratadas.</span><span class="sxs-lookup"><span data-stu-id="05eb9-125">The option controls how calls to the current metadata scope are handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="05eb9-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="05eb9-126">Requirements</span></span>  
 <span data-ttu-id="05eb9-127">**Plataforma:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05eb9-127">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05eb9-128">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="05eb9-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="05eb9-129">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="05eb9-129">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="05eb9-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05eb9-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05eb9-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="05eb9-131">See also</span></span>

- [<span data-ttu-id="05eb9-132">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="05eb9-132">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="05eb9-133">Interface IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="05eb9-133">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="05eb9-134">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="05eb9-134">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="05eb9-135">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="05eb9-135">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
