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
ms.openlocfilehash: c9b4e6e5b36fe38b6c0ea78f6d1848d155008bcc
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420962"
---
# <a name="isosdacinterface-interface"></a><span data-ttu-id="50ef3-102">Interface ISOSDacInterface</span><span class="sxs-lookup"><span data-stu-id="50ef3-102">ISOSDacInterface Interface</span></span>

<span data-ttu-id="50ef3-103">Fornece métodos auxiliares para acessar dados do `SOS` .</span><span class="sxs-lookup"><span data-stu-id="50ef3-103">Provides helper methods to access data from `SOS`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="50ef3-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="50ef3-104">Methods</span></span>

| <span data-ttu-id="50ef3-105">Método</span><span class="sxs-lookup"><span data-stu-id="50ef3-105">Method</span></span>                                                                                                               | <span data-ttu-id="50ef3-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="50ef3-106">Description</span></span>                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="50ef3-107">GetMethodDescData</span><span class="sxs-lookup"><span data-stu-id="50ef3-107">GetMethodDescData</span></span>](isosdacinterface-getmethoddescdata-method.md) | <span data-ttu-id="50ef3-108">Obtém os dados para o ponteiro MethodDesc fornecido.</span><span class="sxs-lookup"><span data-stu-id="50ef3-108">Gets the data for the given MethodDesc pointer.</span></span> |
| [<span data-ttu-id="50ef3-109">GetMethodDescPtrFromIP</span><span class="sxs-lookup"><span data-stu-id="50ef3-109">GetMethodDescPtrFromIP</span></span>](isosdacinterface-getmethoddescptrfromip-method.md) | <span data-ttu-id="50ef3-110">Recupera o ponteiro do MethodDesc correspondente ao método que contém o endereço de instrução nativo fornecido.</span><span class="sxs-lookup"><span data-stu-id="50ef3-110">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span> |
| [<span data-ttu-id="50ef3-111">GetModuleData</span><span class="sxs-lookup"><span data-stu-id="50ef3-111">GetModuleData</span></span>](isosdacinterface-getmoduledata-method.md)| <span data-ttu-id="50ef3-112">Busca os dados correspondentes ao módulo carregado em um determinado endereço.</span><span class="sxs-lookup"><span data-stu-id="50ef3-112">Fetches the data corresponding to the module loaded at a given address.</span></span> |

## <a name="remarks"></a><span data-ttu-id="50ef3-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="50ef3-113">Remarks</span></span>

<span data-ttu-id="50ef3-114">Essa interface reside dentro do tempo de execução e não é exposta por nenhum cabeçalho ou arquivo de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="50ef3-114">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="50ef3-115">No entanto, é uma interface COM que deriva de `IUnknown` com GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` que pode ser obtido por meio dos mecanismos com usuais.</span><span class="sxs-lookup"><span data-stu-id="50ef3-115">However, it's a COM interface that derives from `IUnknown` with GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="50ef3-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="50ef3-116">Requirements</span></span>

<span data-ttu-id="50ef3-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50ef3-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="50ef3-118">**Cabeçalho:** None</span><span class="sxs-lookup"><span data-stu-id="50ef3-118">**Header:** None</span></span>  
<span data-ttu-id="50ef3-119">**Biblioteca:** None</span><span class="sxs-lookup"><span data-stu-id="50ef3-119">**Library:** None</span></span>  
<span data-ttu-id="50ef3-120">**.NET Framework versões:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="50ef3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="50ef3-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="50ef3-121">See also</span></span>

- [<span data-ttu-id="50ef3-122">Depuração</span><span class="sxs-lookup"><span data-stu-id="50ef3-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="50ef3-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="50ef3-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
