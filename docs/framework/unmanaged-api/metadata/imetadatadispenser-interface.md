---
title: Interface IMetaDataDispenser
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dda284fc86f0a82472c59d6bab08fd4a87364723
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61904752"
---
# <a name="imetadatadispenser-interface"></a><span data-ttu-id="0257b-102">Interface IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="0257b-102">IMetaDataDispenser Interface</span></span>
<span data-ttu-id="0257b-103">Fornece métodos para criar um novo escopo de metadados, ou abra um existente.</span><span class="sxs-lookup"><span data-stu-id="0257b-103">Provides methods to create a new metadata scope, or open an existing one.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0257b-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="0257b-104">Methods</span></span>  
  
|<span data-ttu-id="0257b-105">Método</span><span class="sxs-lookup"><span data-stu-id="0257b-105">Method</span></span>|<span data-ttu-id="0257b-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="0257b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0257b-107">Método DefineScope</span><span class="sxs-lookup"><span data-stu-id="0257b-107">DefineScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-definescope-method.md)|<span data-ttu-id="0257b-108">Cria uma nova área na memória em que você pode criar novos metadados.</span><span class="sxs-lookup"><span data-stu-id="0257b-108">Creates a new area in memory where you can create new metadata.</span></span>|  
|[<span data-ttu-id="0257b-109">Método OpenScope</span><span class="sxs-lookup"><span data-stu-id="0257b-109">OpenScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)|<span data-ttu-id="0257b-110">Abre um arquivo existente, em disco e mapeia seus metadados na memória.</span><span class="sxs-lookup"><span data-stu-id="0257b-110">Opens an existing, on-disk file and maps its metadata into memory.</span></span>|  
|[<span data-ttu-id="0257b-111">Método OpenScopeOnMemory</span><span class="sxs-lookup"><span data-stu-id="0257b-111">OpenScopeOnMemory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md)|<span data-ttu-id="0257b-112">Abre uma área da memória que contém os metadados existentes.</span><span class="sxs-lookup"><span data-stu-id="0257b-112">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="0257b-113">Ou seja, este método abre uma área especificada de memória no qual os dados existentes são tratados como metadados.</span><span class="sxs-lookup"><span data-stu-id="0257b-113">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0257b-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0257b-114">Requirements</span></span>  
 <span data-ttu-id="0257b-115">**Plataforma:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0257b-115">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0257b-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0257b-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0257b-117">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="0257b-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0257b-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0257b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0257b-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0257b-119">See also</span></span>

- [<span data-ttu-id="0257b-120">Interface IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="0257b-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="0257b-121">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="0257b-121">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
