---
title: Interface IMetaDataFilter
ms.date: 03/30/2017
api_name:
- IMetaDataFilter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter
helpviewer_keywords:
- IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: ec0856ef-8c56-40ba-bf60-86e0ce8b337f
topic_type:
- apiref
ms.openlocfilehash: e8b15f478eb3b94b7cdcab3b69d54e7cc99be13b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440173"
---
# <a name="imetadatafilter-interface"></a><span data-ttu-id="244c9-102">Interface IMetaDataFilter</span><span class="sxs-lookup"><span data-stu-id="244c9-102">IMetaDataFilter Interface</span></span>
<span data-ttu-id="244c9-103">Fornece métodos para marcação e filtragem de tokens de metadados para evitar ações repetidas que já foram realizadas.</span><span class="sxs-lookup"><span data-stu-id="244c9-103">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="244c9-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="244c9-104">Methods</span></span>  
  
|<span data-ttu-id="244c9-105">Método</span><span class="sxs-lookup"><span data-stu-id="244c9-105">Method</span></span>|<span data-ttu-id="244c9-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="244c9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="244c9-107">Método IsTokenMarked</span><span class="sxs-lookup"><span data-stu-id="244c9-107">IsTokenMarked Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-istokenmarked-method.md)|<span data-ttu-id="244c9-108">Obtém um valor que indica se o token de metadados especificado foi processado.</span><span class="sxs-lookup"><span data-stu-id="244c9-108">Gets a value indicating whether the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="244c9-109">Método MarkToken</span><span class="sxs-lookup"><span data-stu-id="244c9-109">MarkToken Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-marktoken-method.md)|<span data-ttu-id="244c9-110">Define um valor que indica que o token de metadados especificado foi processado.</span><span class="sxs-lookup"><span data-stu-id="244c9-110">Sets a value indicating that the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="244c9-111">Método UnmarkAll</span><span class="sxs-lookup"><span data-stu-id="244c9-111">UnmarkAll Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-unmarkall-method.md)|<span data-ttu-id="244c9-112">Remove as marcas de processamento de todos os tokens no escopo de metadados atual.</span><span class="sxs-lookup"><span data-stu-id="244c9-112">Removes the processing marks from all the tokens in the current metadata scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="244c9-113">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="244c9-113">Requirements</span></span>  
 <span data-ttu-id="244c9-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="244c9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="244c9-115">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="244c9-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="244c9-116">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="244c9-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="244c9-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="244c9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="244c9-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="244c9-118">See also</span></span>

- [<span data-ttu-id="244c9-119">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="244c9-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
