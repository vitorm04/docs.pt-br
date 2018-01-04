---
title: "Método IMetaDataDispenser::OpenScope"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenser.OpenScope
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenser::OpenScope
helpviewer_keywords:
- IMetaDataDispenser::OpenScope method [.NET Framework metadata]
- OpenScope method, IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 65063ad5-e0d9-4c01-8f8b-9a5950109fa6
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f1dad7303d83ae550f54d9173a9f4359239091f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatadispenseropenscope-method"></a><span data-ttu-id="b3f2a-102">Método IMetaDataDispenser::OpenScope</span><span class="sxs-lookup"><span data-stu-id="b3f2a-102">IMetaDataDispenser::OpenScope Method</span></span>
<span data-ttu-id="b3f2a-103">Abre um arquivo existente no disco e mapeia os metadados na memória.</span><span class="sxs-lookup"><span data-stu-id="b3f2a-103">Opens an existing, on-disk file and maps its metadata into memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3f2a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b3f2a-104">Syntax</span></span>  
  
```  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b3f2a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b3f2a-105">Parameters</span></span>  
 `szScope`  
 <span data-ttu-id="b3f2a-106">[in] O nome do arquivo a ser aberto.</span><span class="sxs-lookup"><span data-stu-id="b3f2a-106">[in] The name of the file to be opened.</span></span> <span data-ttu-id="b3f2a-107">O arquivo deve conter metadados de runtime (CLR) de linguagem comum.</span><span class="sxs-lookup"><span data-stu-id="b3f2a-107">The file must contain common language runtime (CLR) metadata.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="b3f2a-108">[in] Um valor de [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeração para especificar o modo (leitura, gravação e assim por diante) para abrir.</span><span class="sxs-lookup"><span data-stu-id="b3f2a-108">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="b3f2a-109">[in] O IID da interface de metadados desejados a serem retornadas; o chamador usará a interface para importar (leitura) ou emitir metadados (gravação).</span><span class="sxs-lookup"><span data-stu-id="b3f2a-109">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="b3f2a-110">O valor de `riid` deve especificar uma das interfaces de "importação" ou "emissão".</span><span class="sxs-lookup"><span data-stu-id="b3f2a-110">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="b3f2a-111">Os valores válidos são IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 ou IID_IMetaDataImport2.</span><span class="sxs-lookup"><span data-stu-id="b3f2a-111">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="b3f2a-112">[out] O ponteiro para a interface retornado.</span><span class="sxs-lookup"><span data-stu-id="b3f2a-112">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3f2a-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="b3f2a-113">Remarks</span></span>  
 <span data-ttu-id="b3f2a-114">A cópia na memória dos metadados pode ser consultada usando métodos de uma das interfaces de "importação" ou adicionado ao uso de métodos de uma das interfaces "emissão".</span><span class="sxs-lookup"><span data-stu-id="b3f2a-114">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="b3f2a-115">Se o arquivo de destino não contém metadados do CLR, o `OpenScope` método irá falhar.</span><span class="sxs-lookup"><span data-stu-id="b3f2a-115">If the target file does not contain CLR metadata, the `OpenScope` method will fail.</span></span>  
  
 <span data-ttu-id="b3f2a-116">No .NET Framework versão 1.0 e 1.1, se um escopo é aberto com `dwOpenFlags` definido como ofRead, está qualificado para o compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="b3f2a-116">In the .NET Framework version 1.0 and version 1.1, if a scope is opened with `dwOpenFlags` set to ofRead, it is eligible for sharing.</span></span> <span data-ttu-id="b3f2a-117">Ou seja, se subsequentes chamadas para `OpenScope` passagem no nome de um arquivo que foi aberto anteriormente, o escopo existente é reutilizado e um novo conjunto de estruturas de dados não foi criado.</span><span class="sxs-lookup"><span data-stu-id="b3f2a-117">That is, if subsequent calls to `OpenScope` pass in the name of a file that was previously opened, the existing scope is reused and a new set of data structures is not created.</span></span> <span data-ttu-id="b3f2a-118">No entanto, podem surgir problemas devido a esse compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="b3f2a-118">However, problems can arise due to this sharing.</span></span>  
  
 <span data-ttu-id="b3f2a-119">No .NET Framework versão 2.0, os escopos aberto com `dwOpenFlags` definido como ofRead não são mais compartilhados.</span><span class="sxs-lookup"><span data-stu-id="b3f2a-119">In the .NET Framework version 2.0, scopes opened with `dwOpenFlags` set to ofRead are no longer shared.</span></span> <span data-ttu-id="b3f2a-120">Use o valor de ofReadOnly para permitir que o escopo deve ser compartilhado.</span><span class="sxs-lookup"><span data-stu-id="b3f2a-120">Use the ofReadOnly value to allow the scope to be shared.</span></span> <span data-ttu-id="b3f2a-121">Quando um escopo é compartilhado, as consultas que usam "leitura/gravação" interfaces de metadados falhará.</span><span class="sxs-lookup"><span data-stu-id="b3f2a-121">When a scope is shared, queries that use "read/write" metadata interfaces will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3f2a-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b3f2a-122">Requirements</span></span>  
 <span data-ttu-id="b3f2a-123">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3f2a-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3f2a-124">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b3f2a-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b3f2a-125">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="b3f2a-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b3f2a-126">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3f2a-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3f2a-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b3f2a-127">See Also</span></span>  
 [<span data-ttu-id="b3f2a-128">Interface IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="b3f2a-128">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [<span data-ttu-id="b3f2a-129">Interface IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="b3f2a-129">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="b3f2a-130">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="b3f2a-130">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [<span data-ttu-id="b3f2a-131">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="b3f2a-131">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="b3f2a-132">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="b3f2a-132">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="b3f2a-133">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="b3f2a-133">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="b3f2a-134">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="b3f2a-134">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="b3f2a-135">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="b3f2a-135">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
