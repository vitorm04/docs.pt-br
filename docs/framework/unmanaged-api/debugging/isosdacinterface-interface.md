---
title: ISOSDacInterface Interface
ms.date: 01/16/2019
api.name:
- ISOSDacInterface Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface Interface
helpviewer.keywords:
- ISOSDacInterface Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 745ecfbffaad841e1ceb9216802644ba9dd5b94e
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416257"
---
# <a name="isosdacinterface-interface"></a><span data-ttu-id="ce344-102">ISOSDacInterface Interface</span><span class="sxs-lookup"><span data-stu-id="ce344-102">ISOSDacInterface Interface</span></span>

<span data-ttu-id="ce344-103">Fornece métodos auxiliares para acessar dados de `SOS`.</span><span class="sxs-lookup"><span data-stu-id="ce344-103">Provides helper methods to access data from `SOS`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="ce344-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="ce344-104">Methods</span></span>

| <span data-ttu-id="ce344-105">Método</span><span class="sxs-lookup"><span data-stu-id="ce344-105">Method</span></span>                                                                                                               | <span data-ttu-id="ce344-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="ce344-106">Description</span></span>                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="ce344-107">GetMethodDescData</span><span class="sxs-lookup"><span data-stu-id="ce344-107">GetMethodDescData</span></span>](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-getmethoddescdata-method.md) | <span data-ttu-id="ce344-108">Obtém os dados para o determinado [MethodDesc](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).</span><span class="sxs-lookup"><span data-stu-id="ce344-108">Gets the data for the given [MethodDesc](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).</span></span> |

## <a name="remarks"></a><span data-ttu-id="ce344-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="ce344-109">Remarks</span></span>

<span data-ttu-id="ce344-110">Essa interface reside dentro do tempo de execução e não é exposta por meio de todos os cabeçalhos ou arquivos de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="ce344-110">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="ce344-111">No entanto, é uma interface COM que deriva de `IUnknown` com o GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` que pode ser obtido por meio de mecanismos COM usual.</span><span class="sxs-lookup"><span data-stu-id="ce344-111">However, it's a COM interface that derives from `IUnknown` with GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="ce344-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ce344-112">Requirements</span></span>

<span data-ttu-id="ce344-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce344-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="ce344-114">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="ce344-114">**Header:** None</span></span>  
<span data-ttu-id="ce344-115">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="ce344-115">**Library:** None</span></span>  
<span data-ttu-id="ce344-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ce344-116">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ce344-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ce344-117">See Also</span></span>

- [<span data-ttu-id="ce344-118">Depuração</span><span class="sxs-lookup"><span data-stu-id="ce344-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="ce344-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="ce344-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
