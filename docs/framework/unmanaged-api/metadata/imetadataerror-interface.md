---
title: Interface IMetaDataError
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4df7aa7400a180151de5420effc8738955d51c26
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataerror-interface"></a><span data-ttu-id="6cc6d-102">Interface IMetaDataError</span><span class="sxs-lookup"><span data-stu-id="6cc6d-102">IMetaDataError Interface</span></span>
<span data-ttu-id="6cc6d-103">Fornece um mecanismo de retorno de chamada para o relatório de erros durante a mesclagem de metadados.</span><span class="sxs-lookup"><span data-stu-id="6cc6d-103">Provides a callback mechanism for reporting errors during the metadata merge.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6cc6d-104">O `IMetaDataError` interface deve ser implementada pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="6cc6d-104">The `IMetaDataError` interface must be implemented by the client.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6cc6d-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="6cc6d-105">Methods</span></span>  
  
|<span data-ttu-id="6cc6d-106">Método</span><span class="sxs-lookup"><span data-stu-id="6cc6d-106">Method</span></span>|<span data-ttu-id="6cc6d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="6cc6d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6cc6d-108">Método OnError</span><span class="sxs-lookup"><span data-stu-id="6cc6d-108">OnError Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-onerror-method.md)|<span data-ttu-id="6cc6d-109">Fornece notificação de erros que ocorrem durante a mesclagem de metadados.</span><span class="sxs-lookup"><span data-stu-id="6cc6d-109">Provides notification of errors that occur during the metadata merge.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6cc6d-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6cc6d-110">Requirements</span></span>  
 <span data-ttu-id="6cc6d-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cc6d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cc6d-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6cc6d-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6cc6d-113">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="6cc6d-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6cc6d-114">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cc6d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cc6d-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6cc6d-115">See Also</span></span>  
 [<span data-ttu-id="6cc6d-116">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="6cc6d-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
