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
ms.openlocfilehash: 0eef69cea9f59911b5076f56579b0192be357431
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659105"
---
# <a name="ixclrdatamethodinstance-interface"></a><span data-ttu-id="2f061-102">Interface IXCLRDataMethodInstance</span><span class="sxs-lookup"><span data-stu-id="2f061-102">IXCLRDataMethodInstance Interface</span></span>

<span data-ttu-id="2f061-103">Fornece métodos para consultar informações sobre uma instância de método.</span><span class="sxs-lookup"><span data-stu-id="2f061-103">Provides methods for querying information about a method instance.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="2f061-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="2f061-104">Methods</span></span>

| <span data-ttu-id="2f061-105">Método</span><span class="sxs-lookup"><span data-stu-id="2f061-105">Method</span></span>                                                                                                                  | <span data-ttu-id="2f061-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="2f061-106">Description</span></span>                                 |
| ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| [<span data-ttu-id="2f061-107">GetILAddressMap</span><span class="sxs-lookup"><span data-stu-id="2f061-107">GetILAddressMap</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-getiladdressmap-method.md) | <span data-ttu-id="2f061-108">Obtém a IL às informações de mapeamento de endereço.</span><span class="sxs-lookup"><span data-stu-id="2f061-108">Gets the IL to address mapping information.</span></span> |

## <a name="remarks"></a><span data-ttu-id="2f061-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="2f061-109">Remarks</span></span>

<span data-ttu-id="2f061-110">Essa interface reside dentro do tempo de execução e não é exposta por meio de todos os cabeçalhos ou arquivos de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="2f061-110">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="2f061-111">No entanto, é uma interface COM que deriva de `IUnknown` com o GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` que pode ser obtido por meio de mecanismos COM usual.</span><span class="sxs-lookup"><span data-stu-id="2f061-111">However, it's a COM interface that derives from `IUnknown` with GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="2f061-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2f061-112">Requirements</span></span>

<span data-ttu-id="2f061-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f061-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="2f061-114">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="2f061-114">**Header:** None</span></span>  
<span data-ttu-id="2f061-115">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="2f061-115">**Library:** None</span></span>  
<span data-ttu-id="2f061-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2f061-116">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="2f061-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2f061-117">See also</span></span>

- [<span data-ttu-id="2f061-118">Depuração</span><span class="sxs-lookup"><span data-stu-id="2f061-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="2f061-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="2f061-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
