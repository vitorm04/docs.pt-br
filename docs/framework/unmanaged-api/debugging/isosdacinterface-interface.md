---
title: Interface ISOSDacInterface
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
ms.openlocfilehash: 94349a3f7b18c8ce29bb3a71cb9d10ee4eac8036
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790473"
---
# <a name="isosdacinterface-interface"></a><span data-ttu-id="21182-102">Interface ISOSDacInterface</span><span class="sxs-lookup"><span data-stu-id="21182-102">ISOSDacInterface Interface</span></span>

<span data-ttu-id="21182-103">Fornece métodos auxiliares para acessar dados de `SOS`.</span><span class="sxs-lookup"><span data-stu-id="21182-103">Provides helper methods to access data from `SOS`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="21182-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="21182-104">Methods</span></span>

| <span data-ttu-id="21182-105">Método</span><span class="sxs-lookup"><span data-stu-id="21182-105">Method</span></span>                                                                                                               | <span data-ttu-id="21182-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="21182-106">Description</span></span>                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="21182-107">GetMethodDescData</span><span class="sxs-lookup"><span data-stu-id="21182-107">GetMethodDescData</span></span>](isosdacinterface-getmethoddescdata-method.md) | <span data-ttu-id="21182-108">Obtém os dados para o ponteiro MethodDesc fornecido.</span><span class="sxs-lookup"><span data-stu-id="21182-108">Gets the data for the given MethodDesc pointer.</span></span> |
| [<span data-ttu-id="21182-109">GetMethodDescPtrFromIP</span><span class="sxs-lookup"><span data-stu-id="21182-109">GetMethodDescPtrFromIP</span></span>](isosdacinterface-getmethoddescptrfromip-method.md) | <span data-ttu-id="21182-110">Recupera o ponteiro do MethodDesc correspondente ao método que contém o endereço de instrução nativo fornecido.</span><span class="sxs-lookup"><span data-stu-id="21182-110">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span> |
| [<span data-ttu-id="21182-111">GetModuleData</span><span class="sxs-lookup"><span data-stu-id="21182-111">GetModuleData</span></span>](isosdacinterface-getmoduledata-method.md)| <span data-ttu-id="21182-112">Busca os dados correspondentes ao módulo carregado em um determinado endereço.</span><span class="sxs-lookup"><span data-stu-id="21182-112">Fetches the data corresponding to the module loaded at a given address.</span></span> |

## <a name="remarks"></a><span data-ttu-id="21182-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="21182-113">Remarks</span></span>

<span data-ttu-id="21182-114">Essa interface reside dentro do tempo de execução e não é exposta por nenhum cabeçalho ou arquivo de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="21182-114">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="21182-115">No entanto, é uma interface COM que deriva de `IUnknown` com `436f00f2-b42a-4b9f-870c-e73db66ae930` de GUID que pode ser obtida por meio dos mecanismos COM usuais.</span><span class="sxs-lookup"><span data-stu-id="21182-115">However, it's a COM interface that derives from `IUnknown` with GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="21182-116">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="21182-116">Requirements</span></span>

<span data-ttu-id="21182-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21182-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="21182-118">**Cabeçalho:** None</span><span class="sxs-lookup"><span data-stu-id="21182-118">**Header:** None</span></span>  
<span data-ttu-id="21182-119">**Biblioteca:** None</span><span class="sxs-lookup"><span data-stu-id="21182-119">**Library:** None</span></span>  
<span data-ttu-id="21182-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="21182-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="21182-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="21182-121">See also</span></span>

- [<span data-ttu-id="21182-122">Depuração</span><span class="sxs-lookup"><span data-stu-id="21182-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="21182-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="21182-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
