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
ms.openlocfilehash: 642391bce99328f3700d1783054943b6a450b22b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789026"
---
# <a name="iclrmetadatalocator-interface"></a><span data-ttu-id="f8501-102">Interface ICLRMetadataLocator</span><span class="sxs-lookup"><span data-stu-id="f8501-102">ICLRMetadataLocator Interface</span></span>
<span data-ttu-id="f8501-103">Usado pela camada de serviços de acesso a dados para localizar metadados de assemblies em um processo de destino.</span><span class="sxs-lookup"><span data-stu-id="f8501-103">Used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f8501-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="f8501-104">Methods</span></span>  
  
|<span data-ttu-id="f8501-105">Método</span><span class="sxs-lookup"><span data-stu-id="f8501-105">Method</span></span>|<span data-ttu-id="f8501-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="f8501-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f8501-107">Método GetMetadata</span><span class="sxs-lookup"><span data-stu-id="f8501-107">GetMetadata Method</span></span>](iclrmetadatalocator-getmetadata-method.md)|<span data-ttu-id="f8501-108">Recupera os metadados de uma imagem do processo de destino.</span><span class="sxs-lookup"><span data-stu-id="f8501-108">Retrieves the metadata of an image from the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8501-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="f8501-109">Remarks</span></span>  
 <span data-ttu-id="f8501-110">O cliente da API (ou seja, o depurador) deve implementar a interface conforme o apropriado para o processo de destino específico.</span><span class="sxs-lookup"><span data-stu-id="f8501-110">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="f8501-111">Por exemplo, a implementação de um processo ao vivo seria diferente da de um despejo de memória.</span><span class="sxs-lookup"><span data-stu-id="f8501-111">For example, the implementation for a live process would be different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8501-112">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="f8501-112">Requirements</span></span>  
 <span data-ttu-id="f8501-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8501-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8501-114">**Cabeçalho:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="f8501-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="f8501-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8501-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8501-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8501-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8501-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="f8501-117">See also</span></span>

- [<span data-ttu-id="f8501-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="f8501-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
