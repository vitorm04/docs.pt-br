---
title: DacpGetModuleAddress::Método de solicitação
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
ms.openlocfilehash: 4dbe6a2c295e5afae1b6761f0c7b695fdb906428
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102901"
---
# <a name="dacpgetmoduleaddressrequest-method"></a><span data-ttu-id="022a2-102">DacpGetModuleAddress::Método de solicitação</span><span class="sxs-lookup"><span data-stu-id="022a2-102">DacpGetModuleAddress::Request Method</span></span>

<span data-ttu-id="022a2-103">Realiza uma solicitação para preencher a estrutura a partir da estrutura de tempo de execução dada.</span><span class="sxs-lookup"><span data-stu-id="022a2-103">Performs a request to populate the structure from the given runtime structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="022a2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="022a2-104">Syntax</span></span>

```cpp
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a><span data-ttu-id="022a2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="022a2-105">Parameters</span></span>

`pDataModule`\
<span data-ttu-id="022a2-106">[em] Um ponteiro para o módulo de dados de sementes.</span><span class="sxs-lookup"><span data-stu-id="022a2-106">[in] A pointer to the seed data module.</span></span>

## <a name="remarks"></a><span data-ttu-id="022a2-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="022a2-107">Remarks</span></span>

<span data-ttu-id="022a2-108">Esta estrutura vive dentro do tempo de execução e não é exposta através de nenhum cabeçalho ou arquivos de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="022a2-108">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="022a2-109">Para usá-lo, a maneira mais fácil é imitar a implementação:</span><span class="sxs-lookup"><span data-stu-id="022a2-109">To use it, the easiest way is to mimic the implementation:</span></span>

- <span data-ttu-id="022a2-110">Devolva o valor `Request` obtido ao `IXCLRDataModule*` ligar para o método no parâmetro com os seguintes parâmetros:`((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span><span class="sxs-lookup"><span data-stu-id="022a2-110">Return the value obtained from calling the `Request` method on the `IXCLRDataModule*` parameter with the following parameters: `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span></span>

## <a name="requirements"></a><span data-ttu-id="022a2-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="022a2-111">Requirements</span></span>

<span data-ttu-id="022a2-112">**Plataformas:** Ver [requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md)</span><span class="sxs-lookup"><span data-stu-id="022a2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md)</span></span>\
<span data-ttu-id="022a2-113">**Cabeçalho:** Nenhum.</span><span class="sxs-lookup"><span data-stu-id="022a2-113">**Header:** None\</span></span>
<span data-ttu-id="022a2-114">**Biblioteca:** Nenhum.</span><span class="sxs-lookup"><span data-stu-id="022a2-114">**Library:** None\</span></span>
<span data-ttu-id="022a2-115">**.NET Framework Versions:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="022a2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="022a2-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="022a2-116">See also</span></span>

- [<span data-ttu-id="022a2-117">Depuração</span><span class="sxs-lookup"><span data-stu-id="022a2-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="022a2-118">Estrutura de endereço sinuosa</span><span class="sxs-lookup"><span data-stu-id="022a2-118">DacpGetModuleAddress structure</span></span>](dacpgetmoduleaddress-structure.md)
