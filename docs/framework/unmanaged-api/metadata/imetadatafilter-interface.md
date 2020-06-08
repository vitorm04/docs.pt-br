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
ms.openlocfilehash: 821936d20a421739e8eb3d5df228888df7f022e3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503777"
---
# <a name="imetadatafilter-interface"></a><span data-ttu-id="b11e7-102">Interface IMetaDataFilter</span><span class="sxs-lookup"><span data-stu-id="b11e7-102">IMetaDataFilter Interface</span></span>
<span data-ttu-id="b11e7-103">Fornece métodos para marcação e filtragem de tokens de metadados para evitar ações repetidas que já foram realizadas.</span><span class="sxs-lookup"><span data-stu-id="b11e7-103">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b11e7-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="b11e7-104">Methods</span></span>  
  
|<span data-ttu-id="b11e7-105">Método</span><span class="sxs-lookup"><span data-stu-id="b11e7-105">Method</span></span>|<span data-ttu-id="b11e7-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="b11e7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b11e7-107">Método IsTokenMarked</span><span class="sxs-lookup"><span data-stu-id="b11e7-107">IsTokenMarked Method</span></span>](imetadatafilter-istokenmarked-method.md)|<span data-ttu-id="b11e7-108">Obtém um valor que indica se o token de metadados especificado foi processado.</span><span class="sxs-lookup"><span data-stu-id="b11e7-108">Gets a value indicating whether the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="b11e7-109">Método MarkToken</span><span class="sxs-lookup"><span data-stu-id="b11e7-109">MarkToken Method</span></span>](imetadatafilter-marktoken-method.md)|<span data-ttu-id="b11e7-110">Define um valor que indica que o token de metadados especificado foi processado.</span><span class="sxs-lookup"><span data-stu-id="b11e7-110">Sets a value indicating that the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="b11e7-111">Método UnmarkAll</span><span class="sxs-lookup"><span data-stu-id="b11e7-111">UnmarkAll Method</span></span>](imetadatafilter-unmarkall-method.md)|<span data-ttu-id="b11e7-112">Remove as marcas de processamento de todos os tokens no escopo de metadados atual.</span><span class="sxs-lookup"><span data-stu-id="b11e7-112">Removes the processing marks from all the tokens in the current metadata scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b11e7-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b11e7-113">Requirements</span></span>  
 <span data-ttu-id="b11e7-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b11e7-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b11e7-115">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b11e7-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b11e7-116">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b11e7-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b11e7-117">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b11e7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b11e7-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="b11e7-118">See also</span></span>

- [<span data-ttu-id="b11e7-119">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="b11e7-119">Metadata Interfaces</span></span>](metadata-interfaces.md)
