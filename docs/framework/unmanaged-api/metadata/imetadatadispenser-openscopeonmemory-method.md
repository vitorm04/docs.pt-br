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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f184c04db384c2b9bdbce2d8ae6919c05a2ab425
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a><span data-ttu-id="3ce70-102">Método IMetaDataDispenser::OpenScopeOnMemory</span><span class="sxs-lookup"><span data-stu-id="3ce70-102">IMetaDataDispenser::OpenScopeOnMemory Method</span></span>
<span data-ttu-id="3ce70-103">Abre uma área da memória que contém os metadados existentes.</span><span class="sxs-lookup"><span data-stu-id="3ce70-103">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="3ce70-104">Ou seja, este método abre uma área especificada de memória na qual os dados existentes são tratados como metadados.</span><span class="sxs-lookup"><span data-stu-id="3ce70-104">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ce70-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3ce70-105">Syntax</span></span>  
  
```  
HRESULT OpenScopeOnMemory (  
    [in]  LPCVOID     pData,   
    [in]  ULONG       cbData,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3ce70-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3ce70-106">Parameters</span></span>  
 `pData`  
 <span data-ttu-id="3ce70-107">[in] Um ponteiro que especifica o endereço inicial da área de memória.</span><span class="sxs-lookup"><span data-stu-id="3ce70-107">[in] A pointer that specifies the starting address of the memory area.</span></span>  
  
 `cbData`  
 <span data-ttu-id="3ce70-108">[in] O tamanho da área de memória, em bytes.</span><span class="sxs-lookup"><span data-stu-id="3ce70-108">[in] The size of the memory area, in bytes.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="3ce70-109">[in] Um valor de [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeração para especificar o modo (leitura, gravação e assim por diante) para abrir.</span><span class="sxs-lookup"><span data-stu-id="3ce70-109">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="3ce70-110">[in] O IID da interface de metadados desejados a serem retornadas; o chamador usará a interface para importar (leitura) ou emitir metadados (gravação).</span><span class="sxs-lookup"><span data-stu-id="3ce70-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="3ce70-111">O valor de `riid` deve especificar uma das interfaces de "importação" ou "emissão".</span><span class="sxs-lookup"><span data-stu-id="3ce70-111">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="3ce70-112">Os valores válidos são IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 ou IID_IMetaDataImport2.</span><span class="sxs-lookup"><span data-stu-id="3ce70-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="3ce70-113">[out] O ponteiro para a interface retornado.</span><span class="sxs-lookup"><span data-stu-id="3ce70-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ce70-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="3ce70-114">Remarks</span></span>  
 <span data-ttu-id="3ce70-115">A cópia na memória dos metadados pode ser consultada usando métodos de uma das interfaces de "importação" ou adicionado ao uso de métodos de uma das interfaces "emissão".</span><span class="sxs-lookup"><span data-stu-id="3ce70-115">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="3ce70-116">O `OpenScopeOnMemory` método é semelhante do [Imetadatadispenser](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) método, exceto que os metadados de interesse já existem na memória, em vez de em um arquivo no disco.</span><span class="sxs-lookup"><span data-stu-id="3ce70-116">The `OpenScopeOnMemory` method is similar to the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, except that the metadata of interest already exists in memory, rather than in a file on disk.</span></span>  
  
 <span data-ttu-id="3ce70-117">Se a área de destino de memória não contém metadados comuns de runtime (CLR) do idioma, o `OpenScopeOnMemory` método irá falhar.</span><span class="sxs-lookup"><span data-stu-id="3ce70-117">If the target area of memory does not contain common language runtime (CLR) metadata, the `OpenScopeOnMemory` method will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ce70-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3ce70-118">Requirements</span></span>  
 <span data-ttu-id="3ce70-119">**Plataforma:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ce70-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ce70-120">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3ce70-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3ce70-121">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="3ce70-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3ce70-122">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ce70-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ce70-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3ce70-123">See Also</span></span>  
 [<span data-ttu-id="3ce70-124">Interface IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="3ce70-124">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [<span data-ttu-id="3ce70-125">Interface IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="3ce70-125">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="3ce70-126">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="3ce70-126">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [<span data-ttu-id="3ce70-127">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="3ce70-127">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="3ce70-128">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="3ce70-128">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="3ce70-129">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="3ce70-129">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="3ce70-130">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="3ce70-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="3ce70-131">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="3ce70-131">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
