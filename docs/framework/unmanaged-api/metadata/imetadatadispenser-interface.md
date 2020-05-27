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
ms.openlocfilehash: 2bdfe65dbf923ec61d91a259b5257d892fef53da
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007332"
---
# <a name="imetadatadispenser-interface"></a><span data-ttu-id="9ff79-102">Interface IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="9ff79-102">IMetaDataDispenser Interface</span></span>
<span data-ttu-id="9ff79-103">Fornece métodos para criar um novo escopo de metadados ou abrir um existente.</span><span class="sxs-lookup"><span data-stu-id="9ff79-103">Provides methods to create a new metadata scope, or open an existing one.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9ff79-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="9ff79-104">Methods</span></span>  
  
|<span data-ttu-id="9ff79-105">Método</span><span class="sxs-lookup"><span data-stu-id="9ff79-105">Method</span></span>|<span data-ttu-id="9ff79-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ff79-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9ff79-107">Método DefineScope</span><span class="sxs-lookup"><span data-stu-id="9ff79-107">DefineScope Method</span></span>](imetadatadispenser-definescope-method.md)|<span data-ttu-id="9ff79-108">Cria uma nova área na memória na qual você pode criar novos metadados.</span><span class="sxs-lookup"><span data-stu-id="9ff79-108">Creates a new area in memory where you can create new metadata.</span></span>|  
|[<span data-ttu-id="9ff79-109">Método OpenScope</span><span class="sxs-lookup"><span data-stu-id="9ff79-109">OpenScope Method</span></span>](imetadatadispenser-openscope-method.md)|<span data-ttu-id="9ff79-110">Abre um arquivo existente em disco e mapeia seus metadados na memória.</span><span class="sxs-lookup"><span data-stu-id="9ff79-110">Opens an existing, on-disk file and maps its metadata into memory.</span></span>|  
|[<span data-ttu-id="9ff79-111">Método OpenScopeOnMemory</span><span class="sxs-lookup"><span data-stu-id="9ff79-111">OpenScopeOnMemory Method</span></span>](imetadatadispenser-openscopeonmemory-method.md)|<span data-ttu-id="9ff79-112">Abre uma área de memória que contém os metadados existentes.</span><span class="sxs-lookup"><span data-stu-id="9ff79-112">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="9ff79-113">Ou seja, esse método abre uma área especificada de memória na qual os dados existentes são tratados como metadados.</span><span class="sxs-lookup"><span data-stu-id="9ff79-113">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9ff79-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9ff79-114">Requirements</span></span>  
 <span data-ttu-id="9ff79-115">**Plataforma:** Consulte [requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ff79-115">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ff79-116">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9ff79-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9ff79-117">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9ff79-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9ff79-118">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ff79-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ff79-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="9ff79-119">See also</span></span>

- [<span data-ttu-id="9ff79-120">Interface IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="9ff79-120">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="9ff79-121">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="9ff79-121">Metadata Interfaces</span></span>](metadata-interfaces.md)
