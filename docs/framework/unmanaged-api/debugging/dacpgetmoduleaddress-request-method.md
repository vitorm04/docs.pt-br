---
title: Método DacpGetModuleAddress::Request
ms.date: 01/16/2019
api.name:
- DacpGetModuleAddress::Request Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpGetModuleAddress::Request Method
helpviewer.keywords:
- DacpGetModuleAddress::Request Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 1755526636bed6d78663112e4c2ad5ab7c3f731c
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860843"
---
# <a name="dacpgetmoduleaddressrequest-method"></a><span data-ttu-id="35acb-102">Método DacpGetModuleAddress::Request</span><span class="sxs-lookup"><span data-stu-id="35acb-102">DacpGetModuleAddress::Request Method</span></span>

<span data-ttu-id="35acb-103">Executa uma solicitação para popular a estrutura da estrutura de tempo de execução fornecida.</span><span class="sxs-lookup"><span data-stu-id="35acb-103">Performs a request to populate the structure from the given runtime structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="35acb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="35acb-104">Syntax</span></span>

```cpp
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a><span data-ttu-id="35acb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="35acb-105">Parameters</span></span>

`pDataModule`\
<span data-ttu-id="35acb-106">no Um ponteiro para o módulo de dados de semente.</span><span class="sxs-lookup"><span data-stu-id="35acb-106">[in] A pointer to the seed data module.</span></span>

## <a name="remarks"></a><span data-ttu-id="35acb-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="35acb-107">Remarks</span></span>

<span data-ttu-id="35acb-108">Essa estrutura reside dentro do tempo de execução e não é exposta por nenhum cabeçalho ou arquivo de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="35acb-108">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="35acb-109">Para usá-lo, a maneira mais fácil é imitar a implementação:</span><span class="sxs-lookup"><span data-stu-id="35acb-109">To use it, the easiest way is to mimic the implementation:</span></span>

- <span data-ttu-id="35acb-110">Retorne o valor obtido da chamada `Request` do método no `IXCLRDataModule*` parâmetro com os seguintes parâmetros:`((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span><span class="sxs-lookup"><span data-stu-id="35acb-110">Return the value obtained from calling the `Request` method on the `IXCLRDataModule*` parameter with the following parameters: `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span></span>

## <a name="requirements"></a><span data-ttu-id="35acb-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="35acb-111">Requirements</span></span>

<span data-ttu-id="35acb-112">**Plataformas:** Consulte [os requisitos do sistema](../../get-started/system-requirements.md)</span><span class="sxs-lookup"><span data-stu-id="35acb-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md)</span></span>\
<span data-ttu-id="35acb-113">**Cabeçalho:** None</span><span class="sxs-lookup"><span data-stu-id="35acb-113">**Header:** None\</span></span>
<span data-ttu-id="35acb-114">**Biblioteca:** None</span><span class="sxs-lookup"><span data-stu-id="35acb-114">**Library:** None\</span></span>
<span data-ttu-id="35acb-115">**.NET Framework versões:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="35acb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="35acb-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="35acb-116">See also</span></span>

- [<span data-ttu-id="35acb-117">Depuração</span><span class="sxs-lookup"><span data-stu-id="35acb-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="35acb-118">Estrutura DacpGetModuleAddress</span><span class="sxs-lookup"><span data-stu-id="35acb-118">DacpGetModuleAddress structure</span></span>](dacpgetmoduleaddress-structure.md)
