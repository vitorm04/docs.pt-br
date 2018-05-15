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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ad77aba02c819749794534ca2ecd478661bc363f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="imetadatafilter-interface"></a><span data-ttu-id="9c8f0-102">Interface IMetaDataFilter</span><span class="sxs-lookup"><span data-stu-id="9c8f0-102">IMetaDataFilter Interface</span></span>
<span data-ttu-id="9c8f0-103">Fornece métodos para a marcação e a filtragem de tokens de metadados para evitar a repetição de ações que já foi usadas.</span><span class="sxs-lookup"><span data-stu-id="9c8f0-103">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9c8f0-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="9c8f0-104">Methods</span></span>  
  
|<span data-ttu-id="9c8f0-105">Método</span><span class="sxs-lookup"><span data-stu-id="9c8f0-105">Method</span></span>|<span data-ttu-id="9c8f0-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="9c8f0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9c8f0-107">Método IsTokenMarked</span><span class="sxs-lookup"><span data-stu-id="9c8f0-107">IsTokenMarked Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-istokenmarked-method.md)|<span data-ttu-id="9c8f0-108">Obtém um valor que indica se o token de metadados especificado foi processado.</span><span class="sxs-lookup"><span data-stu-id="9c8f0-108">Gets a value indicating whether the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="9c8f0-109">Método MarkToken</span><span class="sxs-lookup"><span data-stu-id="9c8f0-109">MarkToken Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-marktoken-method.md)|<span data-ttu-id="9c8f0-110">Define um valor que indica se o token de metadados especificado foi processado.</span><span class="sxs-lookup"><span data-stu-id="9c8f0-110">Sets a value indicating that the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="9c8f0-111">Método UnmarkAll</span><span class="sxs-lookup"><span data-stu-id="9c8f0-111">UnmarkAll Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-unmarkall-method.md)|<span data-ttu-id="9c8f0-112">Remove as marcas de processamento de todos os tokens no escopo atual de metadados.</span><span class="sxs-lookup"><span data-stu-id="9c8f0-112">Removes the processing marks from all the tokens in the current metadata scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9c8f0-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9c8f0-113">Requirements</span></span>  
 <span data-ttu-id="9c8f0-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c8f0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c8f0-115">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9c8f0-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9c8f0-116">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="9c8f0-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9c8f0-117">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c8f0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c8f0-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9c8f0-118">See Also</span></span>  
 [<span data-ttu-id="9c8f0-119">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="9c8f0-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
