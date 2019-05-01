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
ms.openlocfilehash: 4196ff2cb2d4ebc401076f603a8a7fdc9b9c76ea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049954"
---
# <a name="imetadatafilter-interface"></a><span data-ttu-id="88210-102">Interface IMetaDataFilter</span><span class="sxs-lookup"><span data-stu-id="88210-102">IMetaDataFilter Interface</span></span>
<span data-ttu-id="88210-103">Fornece métodos para marcar e filtrar os tokens de metadados para evitar a repetição de ações que já foram realizadas.</span><span class="sxs-lookup"><span data-stu-id="88210-103">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="88210-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="88210-104">Methods</span></span>  
  
|<span data-ttu-id="88210-105">Método</span><span class="sxs-lookup"><span data-stu-id="88210-105">Method</span></span>|<span data-ttu-id="88210-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="88210-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="88210-107">Método IsTokenMarked</span><span class="sxs-lookup"><span data-stu-id="88210-107">IsTokenMarked Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-istokenmarked-method.md)|<span data-ttu-id="88210-108">Obtém um valor que indica se o token de metadados especificado foi processado.</span><span class="sxs-lookup"><span data-stu-id="88210-108">Gets a value indicating whether the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="88210-109">Método MarkToken</span><span class="sxs-lookup"><span data-stu-id="88210-109">MarkToken Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-marktoken-method.md)|<span data-ttu-id="88210-110">Define um valor que indica que o token de metadados especificado foi processado.</span><span class="sxs-lookup"><span data-stu-id="88210-110">Sets a value indicating that the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="88210-111">Método UnmarkAll</span><span class="sxs-lookup"><span data-stu-id="88210-111">UnmarkAll Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-unmarkall-method.md)|<span data-ttu-id="88210-112">Remove as marcas de processamento de todos os tokens no escopo atual de metadados.</span><span class="sxs-lookup"><span data-stu-id="88210-112">Removes the processing marks from all the tokens in the current metadata scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="88210-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="88210-113">Requirements</span></span>  
 <span data-ttu-id="88210-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88210-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88210-115">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="88210-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="88210-116">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="88210-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="88210-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88210-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88210-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="88210-118">See also</span></span>

- [<span data-ttu-id="88210-119">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="88210-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
