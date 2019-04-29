---
title: Interface IXCLRDataMethodInstance
ms.date: 02/01/2019
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
ms.openlocfilehash: f62cbdc4b3e73f0c27492f7ed20b35378654d399
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775487"
---
# <a name="ixclrdatamethodinstance-interface"></a><span data-ttu-id="4bc05-102">Interface IXCLRDataMethodInstance</span><span class="sxs-lookup"><span data-stu-id="4bc05-102">IXCLRDataMethodInstance Interface</span></span>

<span data-ttu-id="4bc05-103">Fornece métodos para consultar informações sobre uma instância de método.</span><span class="sxs-lookup"><span data-stu-id="4bc05-103">Provides methods for querying information about a method instance.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="4bc05-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="4bc05-104">Methods</span></span>

| <span data-ttu-id="4bc05-105">Método</span><span class="sxs-lookup"><span data-stu-id="4bc05-105">Method</span></span>                                                                                                                  | <span data-ttu-id="4bc05-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="4bc05-106">Description</span></span>                                 |
| ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| [<span data-ttu-id="4bc05-107">GetILAddressMap</span><span class="sxs-lookup"><span data-stu-id="4bc05-107">GetILAddressMap</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-getiladdressmap-method.md) | <span data-ttu-id="4bc05-108">Obtém a IL às informações de mapeamento de endereço.</span><span class="sxs-lookup"><span data-stu-id="4bc05-108">Gets the IL to address mapping information.</span></span> |
| [<span data-ttu-id="4bc05-109">GetRepresentativeEntryAddress</span><span class="sxs-lookup"><span data-stu-id="4bc05-109">GetRepresentativeEntryAddress</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-getrepresentativeentryaddress-method.md) | <span data-ttu-id="4bc05-110">Obtém o endereço do ponto de entrada mais representativo para a compilação nativa de todos os pontos de entrada possíveis para um método.</span><span class="sxs-lookup"><span data-stu-id="4bc05-110">Gets the most representative entry point address for the native compilation of all the possible entry points for a method.</span></span> |

## <a name="remarks"></a><span data-ttu-id="4bc05-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="4bc05-111">Remarks</span></span>

<span data-ttu-id="4bc05-112">Essa interface reside dentro do tempo de execução e não é exposta por meio de todos os cabeçalhos ou arquivos de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="4bc05-112">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="4bc05-113">No entanto, é uma interface COM que deriva de `IUnknown` com o GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` que pode ser obtido por meio de mecanismos COM usual.</span><span class="sxs-lookup"><span data-stu-id="4bc05-113">However, it's a COM interface that derives from `IUnknown` with GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="4bc05-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4bc05-114">Requirements</span></span>

<span data-ttu-id="4bc05-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bc05-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="4bc05-116">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="4bc05-116">**Header:** None</span></span>  
<span data-ttu-id="4bc05-117">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="4bc05-117">**Library:** None</span></span>  
<span data-ttu-id="4bc05-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4bc05-118">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="4bc05-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4bc05-119">See also</span></span>

- [<span data-ttu-id="4bc05-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="4bc05-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="4bc05-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="4bc05-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
