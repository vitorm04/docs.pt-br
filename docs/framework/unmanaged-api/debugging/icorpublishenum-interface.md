---
title: Interface ICorPublishEnum
ms.date: 03/30/2017
api_name:
- ICorPublishEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum
helpviewer_keywords:
- ICorPublishEnum interface [.NET Framework debugging]
ms.assetid: 76a136b5-e444-417a-8ade-f1596d597dc7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1eac0b9fe252e476f8ff781f2181a203886d3beb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993532"
---
# <a name="icorpublishenum-interface"></a><span data-ttu-id="63cb4-102">Interface ICorPublishEnum</span><span class="sxs-lookup"><span data-stu-id="63cb4-102">ICorPublishEnum Interface</span></span>
<span data-ttu-id="63cb4-103">Serve como a interface base abstrata para os enumeradores que são usados na publicação de informações sobre processos e domínios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="63cb4-103">Serves as the abstract base interface for the enumerators that are used in the publishing of information about processes and application domains.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="63cb4-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="63cb4-104">Methods</span></span>  
  
|<span data-ttu-id="63cb4-105">Método</span><span class="sxs-lookup"><span data-stu-id="63cb4-105">Method</span></span>|<span data-ttu-id="63cb4-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="63cb4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="63cb4-107">Método Clone</span><span class="sxs-lookup"><span data-stu-id="63cb4-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-clone-method.md)|<span data-ttu-id="63cb4-108">Cria uma cópia deste objeto `ICorPublishEnum`.</span><span class="sxs-lookup"><span data-stu-id="63cb4-108">Creates a copy of this `ICorPublishEnum` object.</span></span>|  
|[<span data-ttu-id="63cb4-109">Método GetCount</span><span class="sxs-lookup"><span data-stu-id="63cb4-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-getcount-method.md)|<span data-ttu-id="63cb4-110">Obtém o número de itens na enumeração.</span><span class="sxs-lookup"><span data-stu-id="63cb4-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="63cb4-111">Método Reset</span><span class="sxs-lookup"><span data-stu-id="63cb4-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-reset-method.md)|<span data-ttu-id="63cb4-112">Move o cursor de para o início da enumeração.</span><span class="sxs-lookup"><span data-stu-id="63cb4-112">Moves the cursor of to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="63cb4-113">Método Skip</span><span class="sxs-lookup"><span data-stu-id="63cb4-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-skip-method.md)|<span data-ttu-id="63cb4-114">Move o cursor para frente na enumeração pelo número especificado de itens.</span><span class="sxs-lookup"><span data-stu-id="63cb4-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63cb4-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="63cb4-115">Remarks</span></span>  
 <span data-ttu-id="63cb4-116">Os enumeradores seguintes derivam `ICorPublishEnum`:</span><span class="sxs-lookup"><span data-stu-id="63cb4-116">The following enumerators derive from `ICorPublishEnum`:</span></span>  
  
- [<span data-ttu-id="63cb4-117">ICorPublishAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="63cb4-117">ICorPublishAppDomainEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
  
- [<span data-ttu-id="63cb4-118">ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="63cb4-118">ICorPublishProcessEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a><span data-ttu-id="63cb4-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="63cb4-119">Requirements</span></span>  
 <span data-ttu-id="63cb4-120">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63cb4-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63cb4-121">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="63cb4-121">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="63cb4-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63cb4-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63cb4-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63cb4-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63cb4-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="63cb4-124">See also</span></span>

- [<span data-ttu-id="63cb4-125">Coclass CorpubPublish</span><span class="sxs-lookup"><span data-stu-id="63cb4-125">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
- [<span data-ttu-id="63cb4-126">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="63cb4-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
