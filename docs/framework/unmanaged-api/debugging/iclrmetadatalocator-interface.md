---
title: Interface ICLRMetadataLocator
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetadataLocator
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRMetadataLocator
helpviewer_keywords: ICLRMetadataLocator interface [.NET Framework debugging]
ms.assetid: 43c944f4-406a-4df6-981e-0eabb33dd5d0
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 955bd6bffe56a166b4c9c313fcb730ce714bf24b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrmetadatalocator-interface"></a><span data-ttu-id="7b7a4-102">Interface ICLRMetadataLocator</span><span class="sxs-lookup"><span data-stu-id="7b7a4-102">ICLRMetadataLocator Interface</span></span>
<span data-ttu-id="7b7a4-103">Usado pela camada de serviços de acesso a dados para localizar metadados de assemblies em um processo de destino.</span><span class="sxs-lookup"><span data-stu-id="7b7a4-103">Used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7b7a4-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="7b7a4-104">Methods</span></span>  
  
|<span data-ttu-id="7b7a4-105">Método</span><span class="sxs-lookup"><span data-stu-id="7b7a4-105">Method</span></span>|<span data-ttu-id="7b7a4-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="7b7a4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7b7a4-107">Método GetMetadata</span><span class="sxs-lookup"><span data-stu-id="7b7a4-107">GetMetadata Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-getmetadata-method.md)|<span data-ttu-id="7b7a4-108">Recupera os metadados de uma imagem do processo de destino.</span><span class="sxs-lookup"><span data-stu-id="7b7a4-108">Retrieves the metadata of an image from the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b7a4-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="7b7a4-109">Remarks</span></span>  
 <span data-ttu-id="7b7a4-110">O cliente da API (ou seja, o depurador) deve implementar a interface conforme o apropriado para o processo de destino específico.</span><span class="sxs-lookup"><span data-stu-id="7b7a4-110">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="7b7a4-111">Por exemplo, a implementação de um processo em tempo real deve ser diferente de um despejo de memória.</span><span class="sxs-lookup"><span data-stu-id="7b7a4-111">For example, the implementation for a live process would be different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b7a4-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7b7a4-112">Requirements</span></span>  
 <span data-ttu-id="7b7a4-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b7a4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b7a4-114">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="7b7a4-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="7b7a4-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b7a4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b7a4-116">**.**</span><span class="sxs-lookup"><span data-stu-id="7b7a4-116">**.**</span></span> <span data-ttu-id="7b7a4-117">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b7a4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b7a4-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7b7a4-118">See Also</span></span>  
 [<span data-ttu-id="7b7a4-119">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="7b7a4-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
