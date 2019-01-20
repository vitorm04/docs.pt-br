---
title: Interface IXCLRDataMethodInstance
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodInstance Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance Interface
helpviewer.keywords:
- IXCLRDataMethodInstance Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 5bf724bc76591ae59c073b5b9a788ca065f51dc0
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416260"
---
# <a name="ixclrdatamethodinstance-interface"></a><span data-ttu-id="3889a-102">Interface IXCLRDataMethodInstance</span><span class="sxs-lookup"><span data-stu-id="3889a-102">IXCLRDataMethodInstance Interface</span></span>

<span data-ttu-id="3889a-103">Fornece métodos para consultar informações sobre uma instância de método.</span><span class="sxs-lookup"><span data-stu-id="3889a-103">Provides methods for querying information about a method instance.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="3889a-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="3889a-104">Methods</span></span>

| <span data-ttu-id="3889a-105">Método</span><span class="sxs-lookup"><span data-stu-id="3889a-105">Method</span></span>                                                                                                                  | <span data-ttu-id="3889a-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="3889a-106">Description</span></span>                                 |
| ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| [<span data-ttu-id="3889a-107">GetILAddressMap</span><span class="sxs-lookup"><span data-stu-id="3889a-107">GetILAddressMap</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-getiladdressmap-method.md) | <span data-ttu-id="3889a-108">Obtém a IL às informações de mapeamento de endereço.</span><span class="sxs-lookup"><span data-stu-id="3889a-108">Gets the IL to address mapping information.</span></span> |

## <a name="remarks"></a><span data-ttu-id="3889a-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="3889a-109">Remarks</span></span>

<span data-ttu-id="3889a-110">Essa interface reside dentro do tempo de execução e não é exposta por meio de todos os cabeçalhos ou arquivos de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="3889a-110">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="3889a-111">No entanto, é uma interface COM que deriva de `IUnknown` com o GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` que pode ser obtido por meio de mecanismos COM usual.</span><span class="sxs-lookup"><span data-stu-id="3889a-111">However, it's a COM interface that derives from `IUnknown` with GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="3889a-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3889a-112">Requirements</span></span>

<span data-ttu-id="3889a-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3889a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="3889a-114">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="3889a-114">**Header:** None</span></span>  
<span data-ttu-id="3889a-115">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="3889a-115">**Library:** None</span></span>  
<span data-ttu-id="3889a-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3889a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="3889a-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3889a-117">See Also</span></span>

- [<span data-ttu-id="3889a-118">Depuração</span><span class="sxs-lookup"><span data-stu-id="3889a-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="3889a-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="3889a-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
