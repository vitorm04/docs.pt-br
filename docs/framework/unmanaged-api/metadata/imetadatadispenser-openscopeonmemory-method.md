---
title: Método IMetaDataDispenser::OpenScopeOnMemory
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScopeOnMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScopeOnMemory
helpviewer_keywords:
- OpenScopeOnMemory method [.NET Framework metadata]
- IMetaDataDispenser::OpenScopeOnMemory method [.NET Framework metadata]
ms.assetid: 14218249-bdec-48ae-b5fc-9f57f7ca8501
topic_type:
- apiref
ms.openlocfilehash: 492c37540ad68b5b134520218eedc59013c68519
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175922"
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a><span data-ttu-id="6aa1d-102">Método IMetaDataDispenser::OpenScopeOnMemory</span><span class="sxs-lookup"><span data-stu-id="6aa1d-102">IMetaDataDispenser::OpenScopeOnMemory Method</span></span>
<span data-ttu-id="6aa1d-103">Abre uma área de memória que contém metadados existentes.</span><span class="sxs-lookup"><span data-stu-id="6aa1d-103">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="6aa1d-104">Ou seja, este método abre uma área especificada de memória na qual os dados existentes são tratados como metadados.</span><span class="sxs-lookup"><span data-stu-id="6aa1d-104">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6aa1d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6aa1d-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenScopeOnMemory (  
    [in]  LPCVOID     pData,
    [in]  ULONG       cbData,
    [in]  DWORD       dwOpenFlags,
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6aa1d-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="6aa1d-106">Parameters</span></span>  
 `pData`  
 <span data-ttu-id="6aa1d-107">[em] Um ponteiro que especifica o endereço inicial da área de memória.</span><span class="sxs-lookup"><span data-stu-id="6aa1d-107">[in] A pointer that specifies the starting address of the memory area.</span></span>  
  
 `cbData`  
 <span data-ttu-id="6aa1d-108">[em] O tamanho da área de memória, em bytes.</span><span class="sxs-lookup"><span data-stu-id="6aa1d-108">[in] The size of the memory area, in bytes.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="6aa1d-109">[em] Um valor da enumeração [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) para especificar o modo (ler, gravar e assim por diante) para abertura.</span><span class="sxs-lookup"><span data-stu-id="6aa1d-109">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="6aa1d-110">[em] O IID da interface de metadados desejada a ser devolvida; o chamador usará a interface para importar (ler) ou emitir metadados (gravar).</span><span class="sxs-lookup"><span data-stu-id="6aa1d-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="6aa1d-111">O valor `riid` de deve especificar uma das interfaces "importação" ou "emitir".</span><span class="sxs-lookup"><span data-stu-id="6aa1d-111">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="6aa1d-112">Os valores válidos são IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 ou IID_IMetaDataImport2.</span><span class="sxs-lookup"><span data-stu-id="6aa1d-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="6aa1d-113">[fora] O ponteiro para a interface retornada.</span><span class="sxs-lookup"><span data-stu-id="6aa1d-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6aa1d-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="6aa1d-114">Remarks</span></span>  
 <span data-ttu-id="6aa1d-115">A cópia na memória dos metadados pode ser consultada usando métodos de uma das interfaces de "importação" ou adicionada ao uso de métodos a partir de uma das interfaces "emitidas".</span><span class="sxs-lookup"><span data-stu-id="6aa1d-115">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="6aa1d-116">O `OpenScopeOnMemory` método é semelhante ao [método IMetaDataDispenser::OpenScope,](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) exceto que os metadados de interesse já existem na memória, em vez de em um arquivo em disco.</span><span class="sxs-lookup"><span data-stu-id="6aa1d-116">The `OpenScopeOnMemory` method is similar to the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, except that the metadata of interest already exists in memory, rather than in a file on disk.</span></span>  
  
 <span data-ttu-id="6aa1d-117">Se a área de destino da memória não contiver metadados `OpenScopeOnMemory` de tempo de execução de linguagem comum (CLR), o método falhará.</span><span class="sxs-lookup"><span data-stu-id="6aa1d-117">If the target area of memory does not contain common language runtime (CLR) metadata, the `OpenScopeOnMemory` method will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6aa1d-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6aa1d-118">Requirements</span></span>  
 <span data-ttu-id="6aa1d-119">**Plataforma:** Consulte [os requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6aa1d-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6aa1d-120">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6aa1d-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6aa1d-121">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6aa1d-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6aa1d-122">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6aa1d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6aa1d-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="6aa1d-123">See also</span></span>

- [<span data-ttu-id="6aa1d-124">Interface IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="6aa1d-124">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="6aa1d-125">Interface IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="6aa1d-125">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="6aa1d-126">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="6aa1d-126">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="6aa1d-127">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="6aa1d-127">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="6aa1d-128">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="6aa1d-128">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="6aa1d-129">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="6aa1d-129">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="6aa1d-130">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="6aa1d-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="6aa1d-131">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="6aa1d-131">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
