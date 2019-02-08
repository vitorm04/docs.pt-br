---
title: ISOSDacInterface Interface
ms.date: 02/01/2019
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
ms.openlocfilehash: ccaf479fc4fb90007b4999e95ee03bdd0529321e
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55827923"
---
# <a name="isosdacinterface-interface"></a><span data-ttu-id="666bf-102">ISOSDacInterface Interface</span><span class="sxs-lookup"><span data-stu-id="666bf-102">ISOSDacInterface Interface</span></span>

<span data-ttu-id="666bf-103">Fornece métodos auxiliares para acessar dados de `SOS`.</span><span class="sxs-lookup"><span data-stu-id="666bf-103">Provides helper methods to access data from `SOS`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="666bf-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="666bf-104">Methods</span></span>

| <span data-ttu-id="666bf-105">Método</span><span class="sxs-lookup"><span data-stu-id="666bf-105">Method</span></span>                                                                                                               | <span data-ttu-id="666bf-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="666bf-106">Description</span></span>                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="666bf-107">GetMethodDescData</span><span class="sxs-lookup"><span data-stu-id="666bf-107">GetMethodDescData</span></span>](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-getmethoddescdata-method.md) | <span data-ttu-id="666bf-108">Obtém os dados para o ponteiro de MethodDesc determinado.</span><span class="sxs-lookup"><span data-stu-id="666bf-108">Gets the data for the given MethodDesc pointer.</span></span> |
| [<span data-ttu-id="666bf-109">GetMethodDescPtrFromIP</span><span class="sxs-lookup"><span data-stu-id="666bf-109">GetMethodDescPtrFromIP</span></span>](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-getmethoddescptrfromip-method.md) | <span data-ttu-id="666bf-110">Recupera o ponteiro do MethodDesc correspondente o método que contém o endereço de determinada instrução nativos.</span><span class="sxs-lookup"><span data-stu-id="666bf-110">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span> |
| [<span data-ttu-id="666bf-111">GetModuleData</span><span class="sxs-lookup"><span data-stu-id="666bf-111">GetModuleData</span></span>](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-getmoduledata-method.md)| <span data-ttu-id="666bf-112">Busca os dados correspondentes para o módulo carregado em um determinado endereço.</span><span class="sxs-lookup"><span data-stu-id="666bf-112">Fetches the data corresponding to the module loaded at a given address.</span></span> |

## <a name="remarks"></a><span data-ttu-id="666bf-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="666bf-113">Remarks</span></span>

<span data-ttu-id="666bf-114">Essa interface reside dentro do tempo de execução e não é exposta por meio de todos os cabeçalhos ou arquivos de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="666bf-114">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="666bf-115">No entanto, é uma interface COM que deriva de `IUnknown` com o GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` que pode ser obtido por meio de mecanismos COM usual.</span><span class="sxs-lookup"><span data-stu-id="666bf-115">However, it's a COM interface that derives from `IUnknown` with GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="666bf-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="666bf-116">Requirements</span></span>

<span data-ttu-id="666bf-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="666bf-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="666bf-118">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="666bf-118">**Header:** None</span></span>  
<span data-ttu-id="666bf-119">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="666bf-119">**Library:** None</span></span>  
<span data-ttu-id="666bf-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="666bf-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="666bf-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="666bf-121">See also</span></span>

- [<span data-ttu-id="666bf-122">Depuração</span><span class="sxs-lookup"><span data-stu-id="666bf-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="666bf-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="666bf-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
