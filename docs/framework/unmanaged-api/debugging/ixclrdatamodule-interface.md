---
title: Interface IXCLRDataModule
ms.date: 01/16/2019
api.name:
- IXCLRDataModule Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule Interface
helpviewer.keywords:
- IXCLRDataModule Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 3c2bc771c0a131329b9403c99a33ca7b79023771
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420845"
---
# <a name="ixclrdatamodule-interface"></a><span data-ttu-id="05fd3-102">Interface IXCLRDataModule</span><span class="sxs-lookup"><span data-stu-id="05fd3-102">IXCLRDataModule Interface</span></span>

<span data-ttu-id="05fd3-103">Fornece métodos para consultar informações sobre um módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="05fd3-103">Provides methods for querying information about a loaded module.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="05fd3-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="05fd3-104">Methods</span></span>

| <span data-ttu-id="05fd3-105">Método</span><span class="sxs-lookup"><span data-stu-id="05fd3-105">Method</span></span>                                                                                                                                | <span data-ttu-id="05fd3-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="05fd3-106">Description</span></span>                                                         |
| ------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="05fd3-107">GetMethodDefinitionByToken</span><span class="sxs-lookup"><span data-stu-id="05fd3-107">GetMethodDefinitionByToken</span></span>](ixclrdatamodule-getmethoddefinitionbytoken-method.md) | <span data-ttu-id="05fd3-108">Obtém a definição do método correspondente a um determinado token de metadados.</span><span class="sxs-lookup"><span data-stu-id="05fd3-108">Gets the method definition corresponding to a given metadata token.</span></span> |
| [<span data-ttu-id="05fd3-109">Solicitação</span><span class="sxs-lookup"><span data-stu-id="05fd3-109">Request</span></span>](ixclrdatamodule-request-method.md)                                       | <span data-ttu-id="05fd3-110">Solicitações para popular o buffer fornecido com os dados do módulo.</span><span class="sxs-lookup"><span data-stu-id="05fd3-110">Requests to populate the buffer given with the module's data.</span></span>       |
| [<span data-ttu-id="05fd3-111">GetVersionId</span><span class="sxs-lookup"><span data-stu-id="05fd3-111">GetVersionId</span></span>](ixclrdatamodule-getversionid-method.md)                             | <span data-ttu-id="05fd3-112">Obtém a ID da versão do módulo.</span><span class="sxs-lookup"><span data-stu-id="05fd3-112">Gets the module's version ID.</span></span>                                       |

## <a name="remarks"></a><span data-ttu-id="05fd3-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="05fd3-113">Remarks</span></span>

<span data-ttu-id="05fd3-114">Essa interface reside dentro do tempo de execução e não é exposta por nenhum cabeçalho ou arquivo de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="05fd3-114">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="05fd3-115">No entanto, é uma interface COM que deriva de `IUnknown` com GUID `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` que pode ser obtido por meio dos mecanismos com usuais.</span><span class="sxs-lookup"><span data-stu-id="05fd3-115">However, it's a COM interface that derives from `IUnknown` with GUID `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="05fd3-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="05fd3-116">Requirements</span></span>

<span data-ttu-id="05fd3-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05fd3-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="05fd3-118">**Cabeçalho:** None</span><span class="sxs-lookup"><span data-stu-id="05fd3-118">**Header:** None</span></span>  
<span data-ttu-id="05fd3-119">**Biblioteca:** None</span><span class="sxs-lookup"><span data-stu-id="05fd3-119">**Library:** None</span></span>  
<span data-ttu-id="05fd3-120">**.NET Framework versões:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="05fd3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="05fd3-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="05fd3-121">See also</span></span>

- [<span data-ttu-id="05fd3-122">Depuração</span><span class="sxs-lookup"><span data-stu-id="05fd3-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="05fd3-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="05fd3-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
