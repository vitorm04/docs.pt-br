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
ms.openlocfilehash: 8d9de753f1c44338a96e990def80643d591f2a8b
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007462"
---
# <a name="imetadatadispenseropenscope-method"></a><span data-ttu-id="7d74e-102">Método IMetaDataDispenser::OpenScope</span><span class="sxs-lookup"><span data-stu-id="7d74e-102">IMetaDataDispenser::OpenScope Method</span></span>
<span data-ttu-id="7d74e-103">Abre um arquivo existente em disco e mapeia seus metadados na memória.</span><span class="sxs-lookup"><span data-stu-id="7d74e-103">Opens an existing, on-disk file and maps its metadata into memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d74e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7d74e-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,
    [in]  DWORD       dwOpenFlags,
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d74e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7d74e-105">Parameters</span></span>  
 `szScope`  
 <span data-ttu-id="7d74e-106">no O nome do arquivo a ser aberto.</span><span class="sxs-lookup"><span data-stu-id="7d74e-106">[in] The name of the file to be opened.</span></span> <span data-ttu-id="7d74e-107">O arquivo deve conter metadados de Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="7d74e-107">The file must contain common language runtime (CLR) metadata.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="7d74e-108">no Um valor da enumeração [CorOpenFlags](coropenflags-enumeration.md) para especificar o modo (leitura, gravação e assim por diante) para abertura.</span><span class="sxs-lookup"><span data-stu-id="7d74e-108">[in] A value of the [CorOpenFlags](coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="7d74e-109">no A IID da interface de metadados desejada a ser retornada; o chamador usará a interface para importar (ler) ou emitir (gravar) metadados.</span><span class="sxs-lookup"><span data-stu-id="7d74e-109">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="7d74e-110">O valor de `riid` deve especificar uma das interfaces "Import" ou "Emit".</span><span class="sxs-lookup"><span data-stu-id="7d74e-110">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="7d74e-111">Os valores válidos são IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 ou IID_IMetaDataImport2.</span><span class="sxs-lookup"><span data-stu-id="7d74e-111">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="7d74e-112">fora O ponteiro para a interface retornada.</span><span class="sxs-lookup"><span data-stu-id="7d74e-112">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d74e-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="7d74e-113">Remarks</span></span>  
 <span data-ttu-id="7d74e-114">A cópia na memória dos metadados pode ser consultada usando métodos de uma das interfaces "Import" ou adicionadas ao uso de métodos de uma das interfaces "Emit".</span><span class="sxs-lookup"><span data-stu-id="7d74e-114">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="7d74e-115">Se o arquivo de destino não contiver metadados CLR, o `OpenScope` método falhará.</span><span class="sxs-lookup"><span data-stu-id="7d74e-115">If the target file does not contain CLR metadata, the `OpenScope` method will fail.</span></span>  
  
 <span data-ttu-id="7d74e-116">No .NET Framework versão 1,0 e 1,1, se um escopo for aberto com `dwOpenFlags` definido como ofRead, ele será elegível para compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="7d74e-116">In the .NET Framework version 1.0 and version 1.1, if a scope is opened with `dwOpenFlags` set to ofRead, it is eligible for sharing.</span></span> <span data-ttu-id="7d74e-117">Ou seja, se as chamadas subsequentes forem `OpenScope` aprovadas no nome de um arquivo que foi aberto anteriormente, o escopo existente será reutilizado e um novo conjunto de estruturas de dados não será criado.</span><span class="sxs-lookup"><span data-stu-id="7d74e-117">That is, if subsequent calls to `OpenScope` pass in the name of a file that was previously opened, the existing scope is reused and a new set of data structures is not created.</span></span> <span data-ttu-id="7d74e-118">No entanto, podem surgir problemas devido a esse compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="7d74e-118">However, problems can arise due to this sharing.</span></span>  
  
 <span data-ttu-id="7d74e-119">No .NET Framework versão 2,0, os escopos abertos com `dwOpenFlags` set como ofRead não são mais compartilhados.</span><span class="sxs-lookup"><span data-stu-id="7d74e-119">In the .NET Framework version 2.0, scopes opened with `dwOpenFlags` set to ofRead are no longer shared.</span></span> <span data-ttu-id="7d74e-120">Use o valor ofReadOnly para permitir que o escopo seja compartilhado.</span><span class="sxs-lookup"><span data-stu-id="7d74e-120">Use the ofReadOnly value to allow the scope to be shared.</span></span> <span data-ttu-id="7d74e-121">Quando um escopo é compartilhado, as consultas que usam interfaces de metadados de "leitura/gravação" falharão.</span><span class="sxs-lookup"><span data-stu-id="7d74e-121">When a scope is shared, queries that use "read/write" metadata interfaces will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d74e-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7d74e-122">Requirements</span></span>  
 <span data-ttu-id="7d74e-123">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d74e-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d74e-124">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7d74e-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7d74e-125">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7d74e-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7d74e-126">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d74e-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d74e-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="7d74e-127">See also</span></span>

- [<span data-ttu-id="7d74e-128">Interface IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="7d74e-128">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
- [<span data-ttu-id="7d74e-129">Interface IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="7d74e-129">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="7d74e-130">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="7d74e-130">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="7d74e-131">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="7d74e-131">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="7d74e-132">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="7d74e-132">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="7d74e-133">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="7d74e-133">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="7d74e-134">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="7d74e-134">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="7d74e-135">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="7d74e-135">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
