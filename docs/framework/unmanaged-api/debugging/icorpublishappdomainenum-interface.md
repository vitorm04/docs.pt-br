---
title: Interface ICorPublishAppDomainEnum
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomainEnum
helpviewer_keywords:
- ICorPublishAppDomainEnum interface [.NET Framework debugging]
ms.assetid: bb798c56-042e-475d-a245-b6fac36d0c07
topic_type:
- apiref
ms.openlocfilehash: 61cac0922423acabef3d47618d98ddf082d071da
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790672"
---
# <a name="icorpublishappdomainenum-interface"></a><span data-ttu-id="bdf94-102">Interface ICorPublishAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="bdf94-102">ICorPublishAppDomainEnum Interface</span></span>
<span data-ttu-id="bdf94-103">Uma subclasse da interface [ICorPublishEnum](icorpublishenum-interface.md) que fornece métodos para atravessar uma coleção de objetos [ICorPublishAppDomain](icorpublishappdomain-interface.md) que existem atualmente dentro de um processo.</span><span class="sxs-lookup"><span data-stu-id="bdf94-103">A subclass of the [ICorPublishEnum](icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishAppDomain](icorpublishappdomain-interface.md) objects that currently exist within a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bdf94-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="bdf94-104">Methods</span></span>  
  
|<span data-ttu-id="bdf94-105">Método</span><span class="sxs-lookup"><span data-stu-id="bdf94-105">Method</span></span>|<span data-ttu-id="bdf94-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="bdf94-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bdf94-107">Método Next</span><span class="sxs-lookup"><span data-stu-id="bdf94-107">Next Method</span></span>](icorpublishappdomainenum-next-method.md)|<span data-ttu-id="bdf94-108">Obtém o número especificado de instâncias de `ICorPublishAppDomain` da coleção, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="bdf94-108">Gets the specified number of `ICorPublishAppDomain` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bdf94-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="bdf94-109">Remarks</span></span>  
 <span data-ttu-id="bdf94-110">A interface `ICorPublishAppDomainEnum` implementa os métodos da interface abstrata, [ICorPublishEnum](icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="bdf94-110">The `ICorPublishAppDomainEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](icorpublishenum-interface.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdf94-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="bdf94-111">Requirements</span></span>  
 <span data-ttu-id="bdf94-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdf94-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdf94-113">**Cabeçalho:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="bdf94-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="bdf94-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bdf94-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bdf94-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdf94-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdf94-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="bdf94-116">See also</span></span>

- [<span data-ttu-id="bdf94-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="bdf94-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="bdf94-118">Coclass CorpubPublish</span><span class="sxs-lookup"><span data-stu-id="bdf94-118">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
