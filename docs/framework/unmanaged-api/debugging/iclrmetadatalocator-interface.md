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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ddc0429a6fa921e8e6ba3c55f3efe5373bea9576
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697843"
---
# <a name="iclrmetadatalocator-interface"></a><span data-ttu-id="fb058-102">Interface ICLRMetadataLocator</span><span class="sxs-lookup"><span data-stu-id="fb058-102">ICLRMetadataLocator Interface</span></span>
<span data-ttu-id="fb058-103">Usado pela camada de serviços de acesso a dados para localizar os metadados dos assemblies em um processo de destino.</span><span class="sxs-lookup"><span data-stu-id="fb058-103">Used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fb058-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="fb058-104">Methods</span></span>  
  
|<span data-ttu-id="fb058-105">Método</span><span class="sxs-lookup"><span data-stu-id="fb058-105">Method</span></span>|<span data-ttu-id="fb058-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="fb058-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fb058-107">Método GetMetadata</span><span class="sxs-lookup"><span data-stu-id="fb058-107">GetMetadata Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-getmetadata-method.md)|<span data-ttu-id="fb058-108">Recupera os metadados de uma imagem do processo de destino.</span><span class="sxs-lookup"><span data-stu-id="fb058-108">Retrieves the metadata of an image from the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb058-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="fb058-109">Remarks</span></span>  
 <span data-ttu-id="fb058-110">O cliente da API (ou seja, o depurador) deve implementar a interface conforme o apropriado para o processo de destino específico.</span><span class="sxs-lookup"><span data-stu-id="fb058-110">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="fb058-111">Por exemplo, a implementação de um processo dinâmico seria diferente de um despejo de memória.</span><span class="sxs-lookup"><span data-stu-id="fb058-111">For example, the implementation for a live process would be different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb058-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fb058-112">Requirements</span></span>  
 <span data-ttu-id="fb058-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb058-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb058-114">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="fb058-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="fb058-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb058-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb058-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb058-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb058-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fb058-117">See also</span></span>

- [<span data-ttu-id="fb058-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="fb058-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
