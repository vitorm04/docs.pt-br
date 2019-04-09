---
title: Interface IMetaDataError
ms.date: 03/30/2017
api_name:
- IMetaDataError
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataError
helpviewer_keywords:
- IMetaDataError interface [.NET Framework metadata]
ms.assetid: 0020b62c-ea88-40c7-a9ee-16b064f81624
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 37f1f6055ec8fa68fe804780d2893d20c978e6bd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59188624"
---
# <a name="imetadataerror-interface"></a><span data-ttu-id="d3875-102">Interface IMetaDataError</span><span class="sxs-lookup"><span data-stu-id="d3875-102">IMetaDataError Interface</span></span>
<span data-ttu-id="d3875-103">Fornece um mecanismo de retorno de chamada para relatar erros durante a mesclagem de metadados.</span><span class="sxs-lookup"><span data-stu-id="d3875-103">Provides a callback mechanism for reporting errors during the metadata merge.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3875-104">O `IMetaDataError` interface deve ser implementada pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="d3875-104">The `IMetaDataError` interface must be implemented by the client.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d3875-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="d3875-105">Methods</span></span>  
  
|<span data-ttu-id="d3875-106">Método</span><span class="sxs-lookup"><span data-stu-id="d3875-106">Method</span></span>|<span data-ttu-id="d3875-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d3875-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d3875-108">Método OnError</span><span class="sxs-lookup"><span data-stu-id="d3875-108">OnError Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-onerror-method.md)|<span data-ttu-id="d3875-109">Fornece notificação de erros que ocorrem durante a mesclagem de metadados.</span><span class="sxs-lookup"><span data-stu-id="d3875-109">Provides notification of errors that occur during the metadata merge.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d3875-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d3875-110">Requirements</span></span>  
 <span data-ttu-id="d3875-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3875-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3875-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d3875-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d3875-113">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="d3875-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="d3875-114">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="d3875-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d3875-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d3875-115">See also</span></span>

- [<span data-ttu-id="d3875-116">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="d3875-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
