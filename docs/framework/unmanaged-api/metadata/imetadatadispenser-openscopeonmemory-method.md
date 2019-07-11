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
ms.openlocfilehash: 204e5660e95434f8d0c44d54f4fdbb1c2acc1e5d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777777"
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a><span data-ttu-id="47ead-102">Método IMetaDataDispenser::OpenScopeOnMemory</span><span class="sxs-lookup"><span data-stu-id="47ead-102">IMetaDataDispenser::OpenScopeOnMemory Method</span></span>
<span data-ttu-id="47ead-103">Abre uma área da memória que contém os metadados existentes.</span><span class="sxs-lookup"><span data-stu-id="47ead-103">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="47ead-104">Ou seja, este método abre uma área especificada de memória no qual os dados existentes são tratados como metadados.</span><span class="sxs-lookup"><span data-stu-id="47ead-104">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47ead-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="47ead-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenScopeOnMemory (  
    [in]  LPCVOID     pData,   
    [in]  ULONG       cbData,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47ead-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="47ead-106">Parameters</span></span>  
 `pData`  
 <span data-ttu-id="47ead-107">[in] Um ponteiro que especifica o endereço inicial da área de memória.</span><span class="sxs-lookup"><span data-stu-id="47ead-107">[in] A pointer that specifies the starting address of the memory area.</span></span>  
  
 `cbData`  
 <span data-ttu-id="47ead-108">[in] O tamanho da área de memória, em bytes.</span><span class="sxs-lookup"><span data-stu-id="47ead-108">[in] The size of the memory area, in bytes.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="47ead-109">[in] Um valor igual a [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeração para especificar o modo (ler, gravar e assim por diante) para abrir.</span><span class="sxs-lookup"><span data-stu-id="47ead-109">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="47ead-110">[in] O IID da interface de metadados desejados a serem retornadas; o chamador usará a interface para importar (leitura) ou emitir metadados (gravação).</span><span class="sxs-lookup"><span data-stu-id="47ead-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="47ead-111">O valor de `riid` deve especificar uma das interfaces "importar" ou "emite".</span><span class="sxs-lookup"><span data-stu-id="47ead-111">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="47ead-112">Valores válidos são IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 ou IID_IMetaDataImport2.</span><span class="sxs-lookup"><span data-stu-id="47ead-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="47ead-113">[out] O ponteiro para a interface retornada.</span><span class="sxs-lookup"><span data-stu-id="47ead-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47ead-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="47ead-114">Remarks</span></span>  
 <span data-ttu-id="47ead-115">A cópia na memória dos metadados pode ser consultada usando métodos de uma das interfaces de "importação" ou adicionados ao usar métodos das interfaces "emite".</span><span class="sxs-lookup"><span data-stu-id="47ead-115">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="47ead-116">O `OpenScopeOnMemory` método é semelhante de [imetadatadispenser:: Openscope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) método, exceto que os metadados de interesse já existem na memória, em vez de em um arquivo no disco.</span><span class="sxs-lookup"><span data-stu-id="47ead-116">The `OpenScopeOnMemory` method is similar to the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, except that the metadata of interest already exists in memory, rather than in a file on disk.</span></span>  
  
 <span data-ttu-id="47ead-117">Se a área de destino de memória não contém metadados de tempo de execução (CLR) do common language, o `OpenScopeOnMemory` método falhará.</span><span class="sxs-lookup"><span data-stu-id="47ead-117">If the target area of memory does not contain common language runtime (CLR) metadata, the `OpenScopeOnMemory` method will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47ead-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="47ead-118">Requirements</span></span>  
 <span data-ttu-id="47ead-119">**Plataforma:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47ead-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47ead-120">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="47ead-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="47ead-121">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="47ead-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="47ead-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47ead-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47ead-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="47ead-123">See also</span></span>

- [<span data-ttu-id="47ead-124">Interface IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="47ead-124">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="47ead-125">Interface IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="47ead-125">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="47ead-126">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="47ead-126">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="47ead-127">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="47ead-127">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="47ead-128">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="47ead-128">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="47ead-129">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="47ead-129">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="47ead-130">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="47ead-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="47ead-131">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="47ead-131">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
