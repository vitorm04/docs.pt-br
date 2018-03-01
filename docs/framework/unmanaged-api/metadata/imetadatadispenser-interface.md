---
title: Interface IMetaDataDispenser
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataDispenser
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser
helpviewer_keywords:
- IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 989840b3-9822-4ce5-a6c5-b375d3340a7a
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 678796357b36beb26ebbf34edc713ff6f15a7c40
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatadispenser-interface"></a><span data-ttu-id="bc8b5-102">Interface IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="bc8b5-102">IMetaDataDispenser Interface</span></span>
<span data-ttu-id="bc8b5-103">Fornece métodos para criar um novo escopo de metadados, ou abrir um existente.</span><span class="sxs-lookup"><span data-stu-id="bc8b5-103">Provides methods to create a new metadata scope, or open an existing one.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bc8b5-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="bc8b5-104">Methods</span></span>  
  
|<span data-ttu-id="bc8b5-105">Método</span><span class="sxs-lookup"><span data-stu-id="bc8b5-105">Method</span></span>|<span data-ttu-id="bc8b5-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="bc8b5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bc8b5-107">Método DefineScope</span><span class="sxs-lookup"><span data-stu-id="bc8b5-107">DefineScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-definescope-method.md)|<span data-ttu-id="bc8b5-108">Cria uma nova área na qual você pode criar novos metadados de memória.</span><span class="sxs-lookup"><span data-stu-id="bc8b5-108">Creates a new area in memory where you can create new metadata.</span></span>|  
|[<span data-ttu-id="bc8b5-109">Método OpenScope</span><span class="sxs-lookup"><span data-stu-id="bc8b5-109">OpenScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)|<span data-ttu-id="bc8b5-110">Abre um arquivo existente no disco e mapeia os metadados na memória.</span><span class="sxs-lookup"><span data-stu-id="bc8b5-110">Opens an existing, on-disk file and maps its metadata into memory.</span></span>|  
|[<span data-ttu-id="bc8b5-111">Método OpenScopeOnMemory</span><span class="sxs-lookup"><span data-stu-id="bc8b5-111">OpenScopeOnMemory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md)|<span data-ttu-id="bc8b5-112">Abre uma área da memória que contém os metadados existentes.</span><span class="sxs-lookup"><span data-stu-id="bc8b5-112">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="bc8b5-113">Ou seja, este método abre uma área especificada de memória na qual os dados existentes são tratados como metadados.</span><span class="sxs-lookup"><span data-stu-id="bc8b5-113">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bc8b5-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bc8b5-114">Requirements</span></span>  
 <span data-ttu-id="bc8b5-115">**Plataforma:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc8b5-115">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc8b5-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bc8b5-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bc8b5-117">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="bc8b5-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bc8b5-118">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc8b5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc8b5-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bc8b5-119">See Also</span></span>  
 [<span data-ttu-id="bc8b5-120">Interface IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="bc8b5-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="bc8b5-121">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="bc8b5-121">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
