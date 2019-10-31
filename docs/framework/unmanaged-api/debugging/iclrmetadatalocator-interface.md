---
title: Interface ICLRMetadataLocator
ms.date: 03/30/2017
api_name:
- ICLRMetadataLocator
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRMetadataLocator
helpviewer_keywords:
- ICLRMetadataLocator interface [.NET Framework debugging]
ms.assetid: 43c944f4-406a-4df6-981e-0eabb33dd5d0
topic_type:
- apiref
ms.openlocfilehash: ec92214e33cd1acda8b2702d93deba1f0fb2aaa2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73111022"
---
# <a name="iclrmetadatalocator-interface"></a><span data-ttu-id="0d5dd-102">Interface ICLRMetadataLocator</span><span class="sxs-lookup"><span data-stu-id="0d5dd-102">ICLRMetadataLocator Interface</span></span>
<span data-ttu-id="0d5dd-103">Usado pela camada de serviços de acesso a dados para localizar metadados de assemblies em um processo de destino.</span><span class="sxs-lookup"><span data-stu-id="0d5dd-103">Used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0d5dd-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="0d5dd-104">Methods</span></span>  
  
|<span data-ttu-id="0d5dd-105">Método</span><span class="sxs-lookup"><span data-stu-id="0d5dd-105">Method</span></span>|<span data-ttu-id="0d5dd-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d5dd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0d5dd-107">Método GetMetadata</span><span class="sxs-lookup"><span data-stu-id="0d5dd-107">GetMetadata Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-getmetadata-method.md)|<span data-ttu-id="0d5dd-108">Recupera os metadados de uma imagem do processo de destino.</span><span class="sxs-lookup"><span data-stu-id="0d5dd-108">Retrieves the metadata of an image from the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d5dd-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="0d5dd-109">Remarks</span></span>  
 <span data-ttu-id="0d5dd-110">O cliente da API (ou seja, o depurador) deve implementar a interface conforme o apropriado para o processo de destino específico.</span><span class="sxs-lookup"><span data-stu-id="0d5dd-110">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="0d5dd-111">Por exemplo, a implementação de um processo ao vivo seria diferente da de um despejo de memória.</span><span class="sxs-lookup"><span data-stu-id="0d5dd-111">For example, the implementation for a live process would be different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d5dd-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0d5dd-112">Requirements</span></span>  
 <span data-ttu-id="0d5dd-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d5dd-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d5dd-114">**Cabeçalho:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="0d5dd-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="0d5dd-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d5dd-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d5dd-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d5dd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d5dd-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0d5dd-117">See also</span></span>

- [<span data-ttu-id="0d5dd-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="0d5dd-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
