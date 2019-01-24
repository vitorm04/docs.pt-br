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
ms.openlocfilehash: 1b69a3385743e948dd52dee75be2f975066c5f85
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54542594"
---
# <a name="dacpgetmoduleaddressrequest-method"></a><span data-ttu-id="82eda-102">Método DacpGetModuleAddress::Request</span><span class="sxs-lookup"><span data-stu-id="82eda-102">DacpGetModuleAddress::Request Method</span></span>

<span data-ttu-id="82eda-103">Executa uma solicitação para preencher a estrutura da estrutura de determinado tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="82eda-103">Performs a request to populate the structure from the given runtime structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="82eda-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="82eda-104">Syntax</span></span>

```
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

### <a name="parameters"></a><span data-ttu-id="82eda-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="82eda-105">Parameters</span></span>

<span data-ttu-id="82eda-106">`pDataModule` [in] Um ponteiro para o módulo de dados de semente.</span><span class="sxs-lookup"><span data-stu-id="82eda-106">`pDataModule` [in] A pointer to the seed data module.</span></span>

## <a name="remarks"></a><span data-ttu-id="82eda-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="82eda-107">Remarks</span></span>

<span data-ttu-id="82eda-108">Essa estrutura reside dentro do tempo de execução e não é exposta por meio de todos os cabeçalhos ou arquivos de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="82eda-108">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="82eda-109">Para usá-lo, a maneira mais fácil é imitar a implementação:</span><span class="sxs-lookup"><span data-stu-id="82eda-109">To use it, the easiest way is to mimic the implementation:</span></span>

- <span data-ttu-id="82eda-110">Retornar o valor obtido na chamada a `Request` método no `IXCLRDataModule*` parâmetro com os seguintes parâmetros: `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span><span class="sxs-lookup"><span data-stu-id="82eda-110">Return the value obtained from calling the `Request` method on the `IXCLRDataModule*` parameter with the following parameters: `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span></span>


## <a name="requirements"></a><span data-ttu-id="82eda-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="82eda-111">Requirements</span></span>

<span data-ttu-id="82eda-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82eda-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="82eda-113">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="82eda-113">**Header:** None</span></span>     
<span data-ttu-id="82eda-114">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="82eda-114">**Library:** None</span></span>  
<span data-ttu-id="82eda-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="82eda-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="82eda-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82eda-116">See also</span></span>

- [<span data-ttu-id="82eda-117">Depuração</span><span class="sxs-lookup"><span data-stu-id="82eda-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="82eda-118">Interface DacpGetModuleAddress</span><span class="sxs-lookup"><span data-stu-id="82eda-118">DacpGetModuleAddress Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md)
