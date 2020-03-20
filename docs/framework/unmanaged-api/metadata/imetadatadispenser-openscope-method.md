---
title: Método IMetaDataDispenser::OpenScope
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScope
helpviewer_keywords:
- IMetaDataDispenser::OpenScope method [.NET Framework metadata]
- OpenScope method, IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 65063ad5-e0d9-4c01-8f8b-9a5950109fa6
topic_type:
- apiref
ms.openlocfilehash: 5185fb6663910c85ce5dae1225b9b10c5dd8bb28
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175935"
---
# <a name="imetadatadispenseropenscope-method"></a><span data-ttu-id="26435-102">Método IMetaDataDispenser::OpenScope</span><span class="sxs-lookup"><span data-stu-id="26435-102">IMetaDataDispenser::OpenScope Method</span></span>
<span data-ttu-id="26435-103">Abre um arquivo existente no disco e mapeia seus metadados na memória.</span><span class="sxs-lookup"><span data-stu-id="26435-103">Opens an existing, on-disk file and maps its metadata into memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26435-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="26435-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,
    [in]  DWORD       dwOpenFlags,
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26435-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="26435-105">Parameters</span></span>  
 `szScope`  
 <span data-ttu-id="26435-106">[em] O nome do arquivo a ser aberto.</span><span class="sxs-lookup"><span data-stu-id="26435-106">[in] The name of the file to be opened.</span></span> <span data-ttu-id="26435-107">O arquivo deve conter metadados de tempo de execução de idioma comum (CLR).</span><span class="sxs-lookup"><span data-stu-id="26435-107">The file must contain common language runtime (CLR) metadata.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="26435-108">[em] Um valor da enumeração [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) para especificar o modo (ler, gravar e assim por diante) para abertura.</span><span class="sxs-lookup"><span data-stu-id="26435-108">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="26435-109">[em] O IID da interface de metadados desejada a ser devolvida; o chamador usará a interface para importar (ler) ou emitir metadados (gravar).</span><span class="sxs-lookup"><span data-stu-id="26435-109">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="26435-110">O valor `riid` de deve especificar uma das interfaces "importação" ou "emitir".</span><span class="sxs-lookup"><span data-stu-id="26435-110">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="26435-111">Os valores válidos são IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 ou IID_IMetaDataImport2.</span><span class="sxs-lookup"><span data-stu-id="26435-111">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="26435-112">[fora] O ponteiro para a interface retornada.</span><span class="sxs-lookup"><span data-stu-id="26435-112">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26435-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="26435-113">Remarks</span></span>  
 <span data-ttu-id="26435-114">A cópia na memória dos metadados pode ser consultada usando métodos de uma das interfaces de "importação" ou adicionada ao uso de métodos a partir de uma das interfaces "emitidas".</span><span class="sxs-lookup"><span data-stu-id="26435-114">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="26435-115">Se o arquivo de destino não contiver metadados CLR, o `OpenScope` método falhará.</span><span class="sxs-lookup"><span data-stu-id="26435-115">If the target file does not contain CLR metadata, the `OpenScope` method will fail.</span></span>  
  
 <span data-ttu-id="26435-116">Na versão .NET Framework 1.0 e versão 1.1, `dwOpenFlags` se um escopo for aberto com set de Read, ele é elegível para compartilhar.</span><span class="sxs-lookup"><span data-stu-id="26435-116">In the .NET Framework version 1.0 and version 1.1, if a scope is opened with `dwOpenFlags` set to ofRead, it is eligible for sharing.</span></span> <span data-ttu-id="26435-117">Ou seja, se `OpenScope` chamadas subseqüentes para passar em nome de um arquivo que foi aberta anteriormente, o escopo existente é reutilizado e um novo conjunto de estruturas de dados não é criado.</span><span class="sxs-lookup"><span data-stu-id="26435-117">That is, if subsequent calls to `OpenScope` pass in the name of a file that was previously opened, the existing scope is reused and a new set of data structures is not created.</span></span> <span data-ttu-id="26435-118">No entanto, problemas podem surgir devido a esse compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="26435-118">However, problems can arise due to this sharing.</span></span>  
  
 <span data-ttu-id="26435-119">Na versão .NET Framework 2.0, `dwOpenFlags` os escopos abertos com set de read não são mais compartilhados.</span><span class="sxs-lookup"><span data-stu-id="26435-119">In the .NET Framework version 2.0, scopes opened with `dwOpenFlags` set to ofRead are no longer shared.</span></span> <span data-ttu-id="26435-120">Use o valor de ReadOnly para permitir que o escopo seja compartilhado.</span><span class="sxs-lookup"><span data-stu-id="26435-120">Use the ofReadOnly value to allow the scope to be shared.</span></span> <span data-ttu-id="26435-121">Quando um escopo é compartilhado, as consultas que usam interfaces de metadados "ler/gravar" falharão.</span><span class="sxs-lookup"><span data-stu-id="26435-121">When a scope is shared, queries that use "read/write" metadata interfaces will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26435-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="26435-122">Requirements</span></span>  
 <span data-ttu-id="26435-123">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26435-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26435-124">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="26435-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="26435-125">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="26435-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="26435-126">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26435-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26435-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="26435-127">See also</span></span>

- [<span data-ttu-id="26435-128">Interface IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="26435-128">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="26435-129">Interface IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="26435-129">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="26435-130">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="26435-130">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="26435-131">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="26435-131">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="26435-132">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="26435-132">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="26435-133">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="26435-133">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="26435-134">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="26435-134">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="26435-135">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="26435-135">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
