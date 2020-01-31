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
ms.openlocfilehash: 8757642db6c4375cf55d1f7288669c4c8a752a38
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790399"
---
# <a name="ixclrdatamodule-interface"></a><span data-ttu-id="6de45-102">Interface IXCLRDataModule</span><span class="sxs-lookup"><span data-stu-id="6de45-102">IXCLRDataModule Interface</span></span>

<span data-ttu-id="6de45-103">Fornece métodos para consultar informações sobre um módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="6de45-103">Provides methods for querying information about a loaded module.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="6de45-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="6de45-104">Methods</span></span>

| <span data-ttu-id="6de45-105">Método</span><span class="sxs-lookup"><span data-stu-id="6de45-105">Method</span></span>                                                                                                                                | <span data-ttu-id="6de45-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="6de45-106">Description</span></span>                                                         |
| ------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="6de45-107">GetMethodDefinitionByToken</span><span class="sxs-lookup"><span data-stu-id="6de45-107">GetMethodDefinitionByToken</span></span>](ixclrdatamodule-getmethoddefinitionbytoken-method.md) | <span data-ttu-id="6de45-108">Obtém a definição do método correspondente a um determinado token de metadados.</span><span class="sxs-lookup"><span data-stu-id="6de45-108">Gets the method definition corresponding to a given metadata token.</span></span> |
| [<span data-ttu-id="6de45-109">Solicitação</span><span class="sxs-lookup"><span data-stu-id="6de45-109">Request</span></span>](ixclrdatamodule-request-method.md)                                       | <span data-ttu-id="6de45-110">Solicitações para popular o buffer fornecido com os dados do módulo.</span><span class="sxs-lookup"><span data-stu-id="6de45-110">Requests to populate the buffer given with the module's data.</span></span>       |
| [<span data-ttu-id="6de45-111">GetVersionId</span><span class="sxs-lookup"><span data-stu-id="6de45-111">GetVersionId</span></span>](ixclrdatamodule-getversionid-method.md)                             | <span data-ttu-id="6de45-112">Obtém a ID da versão do módulo.</span><span class="sxs-lookup"><span data-stu-id="6de45-112">Gets the module's version ID.</span></span>                                       |

## <a name="remarks"></a><span data-ttu-id="6de45-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="6de45-113">Remarks</span></span>

<span data-ttu-id="6de45-114">Essa interface reside dentro do tempo de execução e não é exposta por nenhum cabeçalho ou arquivo de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="6de45-114">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="6de45-115">No entanto, é uma interface COM que deriva de `IUnknown` com `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` de GUID que pode ser obtida por meio dos mecanismos COM usuais.</span><span class="sxs-lookup"><span data-stu-id="6de45-115">However, it's a COM interface that derives from `IUnknown` with GUID `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="6de45-116">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="6de45-116">Requirements</span></span>

<span data-ttu-id="6de45-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6de45-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="6de45-118">**Cabeçalho:** None</span><span class="sxs-lookup"><span data-stu-id="6de45-118">**Header:** None</span></span>  
<span data-ttu-id="6de45-119">**Biblioteca:** None</span><span class="sxs-lookup"><span data-stu-id="6de45-119">**Library:** None</span></span>  
<span data-ttu-id="6de45-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6de45-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="6de45-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="6de45-121">See also</span></span>

- [<span data-ttu-id="6de45-122">Depuração</span><span class="sxs-lookup"><span data-stu-id="6de45-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="6de45-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="6de45-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
