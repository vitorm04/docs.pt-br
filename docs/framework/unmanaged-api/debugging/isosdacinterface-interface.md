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
ms.openlocfilehash: 5e037cf6fb88fff4886733ff4152dca0a827e0a3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491022"
---
# <a name="isosdacinterface-interface"></a><span data-ttu-id="21d6e-102">ISOSDacInterface Interface</span><span class="sxs-lookup"><span data-stu-id="21d6e-102">ISOSDacInterface Interface</span></span>

<span data-ttu-id="21d6e-103">Fornece métodos auxiliares para acessar dados de `SOS`.</span><span class="sxs-lookup"><span data-stu-id="21d6e-103">Provides helper methods to access data from `SOS`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="21d6e-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="21d6e-104">Methods</span></span>

| <span data-ttu-id="21d6e-105">Método</span><span class="sxs-lookup"><span data-stu-id="21d6e-105">Method</span></span>                                                                                                               | <span data-ttu-id="21d6e-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="21d6e-106">Description</span></span>                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="21d6e-107">GetMethodDescData</span><span class="sxs-lookup"><span data-stu-id="21d6e-107">GetMethodDescData</span></span>](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-getmethoddescdata-method.md) | <span data-ttu-id="21d6e-108">Obtém os dados para o determinado [MethodDesc](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).</span><span class="sxs-lookup"><span data-stu-id="21d6e-108">Gets the data for the given [MethodDesc](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).</span></span> |

## <a name="remarks"></a><span data-ttu-id="21d6e-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="21d6e-109">Remarks</span></span>

<span data-ttu-id="21d6e-110">Essa interface reside dentro do tempo de execução e não é exposta por meio de todos os cabeçalhos ou arquivos de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="21d6e-110">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="21d6e-111">No entanto, é uma interface COM que deriva de `IUnknown` com o GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` que pode ser obtido por meio de mecanismos COM usual.</span><span class="sxs-lookup"><span data-stu-id="21d6e-111">However, it's a COM interface that derives from `IUnknown` with GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="21d6e-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="21d6e-112">Requirements</span></span>

<span data-ttu-id="21d6e-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21d6e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="21d6e-114">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="21d6e-114">**Header:** None</span></span>  
<span data-ttu-id="21d6e-115">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="21d6e-115">**Library:** None</span></span>  
<span data-ttu-id="21d6e-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="21d6e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="21d6e-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="21d6e-117">See also</span></span>

- [<span data-ttu-id="21d6e-118">Depuração</span><span class="sxs-lookup"><span data-stu-id="21d6e-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="21d6e-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="21d6e-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
