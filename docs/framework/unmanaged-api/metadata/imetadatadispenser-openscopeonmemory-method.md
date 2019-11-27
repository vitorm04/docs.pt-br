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
ms.openlocfilehash: 04e0fabfc0d70c9d922e0715f32bd07237ce8741
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442315"
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a><span data-ttu-id="cf165-102">Método IMetaDataDispenser::OpenScopeOnMemory</span><span class="sxs-lookup"><span data-stu-id="cf165-102">IMetaDataDispenser::OpenScopeOnMemory Method</span></span>
<span data-ttu-id="cf165-103">Abre uma área de memória que contém os metadados existentes.</span><span class="sxs-lookup"><span data-stu-id="cf165-103">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="cf165-104">Ou seja, esse método abre uma área especificada de memória na qual os dados existentes são tratados como metadados.</span><span class="sxs-lookup"><span data-stu-id="cf165-104">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf165-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cf165-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenScopeOnMemory (  
    [in]  LPCVOID     pData,   
    [in]  ULONG       cbData,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf165-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cf165-106">Parameters</span></span>  
 `pData`  
 <span data-ttu-id="cf165-107">no Um ponteiro que especifica o endereço inicial da área de memória.</span><span class="sxs-lookup"><span data-stu-id="cf165-107">[in] A pointer that specifies the starting address of the memory area.</span></span>  
  
 `cbData`  
 <span data-ttu-id="cf165-108">no O tamanho da área de memória, em bytes.</span><span class="sxs-lookup"><span data-stu-id="cf165-108">[in] The size of the memory area, in bytes.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="cf165-109">no Um valor da enumeração [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) para especificar o modo (leitura, gravação e assim por diante) para abertura.</span><span class="sxs-lookup"><span data-stu-id="cf165-109">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="cf165-110">no A IID da interface de metadados desejada a ser retornada; o chamador usará a interface para importar (ler) ou emitir (gravar) metadados.</span><span class="sxs-lookup"><span data-stu-id="cf165-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="cf165-111">O valor de `riid` deve especificar uma das interfaces "Import" ou "Emit".</span><span class="sxs-lookup"><span data-stu-id="cf165-111">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="cf165-112">Os valores válidos são IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 ou IID_IMetaDataImport2.</span><span class="sxs-lookup"><span data-stu-id="cf165-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="cf165-113">fora O ponteiro para a interface retornada.</span><span class="sxs-lookup"><span data-stu-id="cf165-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf165-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="cf165-114">Remarks</span></span>  
 <span data-ttu-id="cf165-115">A cópia na memória dos metadados pode ser consultada usando métodos de uma das interfaces "Import" ou adicionadas ao uso de métodos de uma das interfaces "Emit".</span><span class="sxs-lookup"><span data-stu-id="cf165-115">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="cf165-116">O método `OpenScopeOnMemory` é semelhante ao método [IMetaDataDispenser:: OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) , exceto que os metadados de interesse já existem na memória, em vez de em um arquivo no disco.</span><span class="sxs-lookup"><span data-stu-id="cf165-116">The `OpenScopeOnMemory` method is similar to the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, except that the metadata of interest already exists in memory, rather than in a file on disk.</span></span>  
  
 <span data-ttu-id="cf165-117">Se a área de destino da memória não contiver metadados de Common Language Runtime (CLR), o método `OpenScopeOnMemory` falhará.</span><span class="sxs-lookup"><span data-stu-id="cf165-117">If the target area of memory does not contain common language runtime (CLR) metadata, the `OpenScopeOnMemory` method will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf165-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cf165-118">Requirements</span></span>  
 <span data-ttu-id="cf165-119">**Plataforma:** Consulte [requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf165-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf165-120">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="cf165-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cf165-121">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cf165-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cf165-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf165-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf165-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf165-123">See also</span></span>

- [<span data-ttu-id="cf165-124">Interface IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="cf165-124">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="cf165-125">Interface IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="cf165-125">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="cf165-126">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="cf165-126">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="cf165-127">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="cf165-127">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="cf165-128">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="cf165-128">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="cf165-129">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="cf165-129">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="cf165-130">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="cf165-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="cf165-131">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="cf165-131">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
