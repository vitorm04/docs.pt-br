---
title: Interface ICorPublishProcessEnum
ms.date: 03/30/2017
api_name:
- ICorPublishProcessEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum
helpviewer_keywords:
- ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: aac8fcf9-ac09-437c-bd5c-2fda14ae1007
topic_type:
- apiref
ms.openlocfilehash: 188ff8feabd704d828256a09aca20f9db2227f2c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790502"
---
# <a name="icorpublishprocessenum-interface"></a><span data-ttu-id="a84ee-102">Interface ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="a84ee-102">ICorPublishProcessEnum Interface</span></span>
<span data-ttu-id="a84ee-103">Uma subclasse da interface [ICorPublishEnum](icorpublishenum-interface.md) que fornece métodos para atravessar uma coleção de objetos [ICorPublishProcess](icorpublishprocess-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="a84ee-103">A subclass of the [ICorPublishEnum](icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishProcess](icorpublishprocess-interface.md) objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a84ee-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="a84ee-104">Methods</span></span>  
  
|<span data-ttu-id="a84ee-105">Método</span><span class="sxs-lookup"><span data-stu-id="a84ee-105">Method</span></span>|<span data-ttu-id="a84ee-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="a84ee-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a84ee-107">Método Next</span><span class="sxs-lookup"><span data-stu-id="a84ee-107">Next Method</span></span>](icorpublishprocessenum-next-method.md)|<span data-ttu-id="a84ee-108">Obtém o número especificado de instâncias de `ICorPublishProcess` da coleção, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="a84ee-108">Gets the specified number of `ICorPublishProcess` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a84ee-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="a84ee-109">Remarks</span></span>  
 <span data-ttu-id="a84ee-110">A interface `ICorPublishProcessEnum` implementa os métodos da interface abstrata, [ICorPublishEnum](icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="a84ee-110">The `ICorPublishProcessEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](icorpublishenum-interface.md).</span></span>  
  
 <span data-ttu-id="a84ee-111">Uma instância de `ICorPublishProcessEnum` é criada pelo método [ICorPublish:: EnumProcesses](icorpublish-enumprocesses-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a84ee-111">An `ICorPublishProcessEnum` instance is created by the [ICorPublish::EnumProcesses](icorpublish-enumprocesses-method.md) method.</span></span> <span data-ttu-id="a84ee-112">A passagem da coleção de objetos de `ICorPublishProcess` é baseada nos critérios de filtro fornecidos no momento em que a instância de `ICorPublishProcessEnum` foi criada.</span><span class="sxs-lookup"><span data-stu-id="a84ee-112">The traversal of the collection of `ICorPublishProcess` objects is based on the filter criteria given at the time the `ICorPublishProcessEnum` instance was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a84ee-113">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="a84ee-113">Requirements</span></span>  
 <span data-ttu-id="a84ee-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a84ee-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a84ee-115">**Cabeçalho:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="a84ee-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="a84ee-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a84ee-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a84ee-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a84ee-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a84ee-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="a84ee-118">See also</span></span>

- [<span data-ttu-id="a84ee-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="a84ee-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="a84ee-120">Coclass CorpubPublish</span><span class="sxs-lookup"><span data-stu-id="a84ee-120">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
