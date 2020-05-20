---
title: 'Método IXCLRDataModule:: Request'
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::Request Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::Request Method
helpviewer.keywords:
- IXCLRDataModule::Request Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 3c18fc5c947cbb89fc4e9aed60d3cedcbe22d749
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420806"
---
# <a name="ixclrdatamodulerequest-method"></a><span data-ttu-id="4a703-102">Método IXCLRDataModule:: Request</span><span class="sxs-lookup"><span data-stu-id="4a703-102">IXCLRDataModule::Request Method</span></span>

<span data-ttu-id="4a703-103">Solicitações para popular o buffer fornecido com os dados do módulo.</span><span class="sxs-lookup"><span data-stu-id="4a703-103">Requests to populate the buffer given with the module's data.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="4a703-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4a703-104">Syntax</span></span>

```cpp
HRESULT Request([in] ULONG32 reqCode,
    [in] ULONG32 inBufferSize,
    [in, size_is(inBufferSize)] BYTE* inBuffer,
    [in] ULONG32 outBufferSize,
    [out, size_is(outBufferSize)] BYTE* outBuffer);
```

## <a name="parameters"></a><span data-ttu-id="4a703-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4a703-105">Parameters</span></span>

`reqCode`\
<span data-ttu-id="4a703-106">no Tipo de solicitação a ser enviado.</span><span class="sxs-lookup"><span data-stu-id="4a703-106">[in] Request type to be sent.</span></span>

`inBufferSize`\
<span data-ttu-id="4a703-107">[in] tamanho do buffer de entrada a ser passado.</span><span class="sxs-lookup"><span data-stu-id="4a703-107">[in] size of the input buffer to be passed in.</span></span>

`inBuffer`\
<span data-ttu-id="4a703-108">[in, size_is (InBufferSize)] Ponteiro de buffer para os dados brutos a serem enviados na solicitação.</span><span class="sxs-lookup"><span data-stu-id="4a703-108">[in, size_is(inBufferSize)] Buffer pointer for the raw data to be sent in the request.</span></span>

`outBufferSize`\
<span data-ttu-id="4a703-109">no Tamanho do buffer de saída.</span><span class="sxs-lookup"><span data-stu-id="4a703-109">[in] Size of the output buffer.</span></span>

`outBuffer`\
<span data-ttu-id="4a703-110">[fora, size_is (OutBufferSize)] Ponteiro de buffer a ser usado para armazenar a resposta de solicitação.</span><span class="sxs-lookup"><span data-stu-id="4a703-110">[out, size_is(outBufferSize)] Buffer pointer to used to store the request response.</span></span>

## <a name="remarks"></a><span data-ttu-id="4a703-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="4a703-111">Remarks</span></span>

<span data-ttu-id="4a703-112">O método fornecido faz parte da `IXCLRDataModule` interface e corresponde ao slot 37th da tabela de métodos virtuais.</span><span class="sxs-lookup"><span data-stu-id="4a703-112">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 37th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="4a703-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4a703-113">Requirements</span></span>

<span data-ttu-id="4a703-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a703-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="4a703-115">**Cabeçalho:** Nenhuma **biblioteca:** nenhuma **.NET Framework versões:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4a703-115">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="4a703-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="4a703-116">See also</span></span>

- [<span data-ttu-id="4a703-117">Depuração</span><span class="sxs-lookup"><span data-stu-id="4a703-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="4a703-118">Interface IXCLRDataModule</span><span class="sxs-lookup"><span data-stu-id="4a703-118">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
