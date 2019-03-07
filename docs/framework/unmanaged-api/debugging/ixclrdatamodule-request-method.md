---
title: Método IXCLRDataModule::Request
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
ms.openlocfilehash: ac7ab7bf207cc1474090bab19818ca17fc068d3a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479214"
---
# <a name="ixclrdatamodulerequest-method"></a><span data-ttu-id="057b6-102">Método IXCLRDataModule::Request</span><span class="sxs-lookup"><span data-stu-id="057b6-102">IXCLRDataModule::Request Method</span></span>

<span data-ttu-id="057b6-103">Solicitações para preencher o buffer fornecido com os dados do módulo.</span><span class="sxs-lookup"><span data-stu-id="057b6-103">Requests to populate the buffer given with the module's data.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="057b6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="057b6-104">Syntax</span></span>
```
HRESULT Request([in] ULONG32 reqCode,
    [in] ULONG32 inBufferSize,
    [in, size_is(inBufferSize)] BYTE* inBuffer,
    [in] ULONG32 outBufferSize,
    [out, size_is(outBufferSize)] BYTE* outBuffer);
```

## <a name="parameters"></a><span data-ttu-id="057b6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="057b6-105">Parameters</span></span>

`reqCode`\
<span data-ttu-id="057b6-106">[in] Tipo a ser enviado de solicitação.</span><span class="sxs-lookup"><span data-stu-id="057b6-106">[in] Request type to be sent.</span></span>

`inBufferSize`\
<span data-ttu-id="057b6-107">[in] o tamanho do buffer de entrada a ser passado.</span><span class="sxs-lookup"><span data-stu-id="057b6-107">[in] size of the input buffer to be passed in.</span></span>

`inBuffer`\
<span data-ttu-id="057b6-108">[in, size_is(inBufferSize)] Ponteiro de buffer para os dados brutos a serem enviados na solicitação.</span><span class="sxs-lookup"><span data-stu-id="057b6-108">[in, size_is(inBufferSize)] Buffer pointer for the raw data to be sent in the request.</span></span>

`outBufferSize`\
<span data-ttu-id="057b6-109">[in] Tamanho do buffer de saída.</span><span class="sxs-lookup"><span data-stu-id="057b6-109">[in] Size of the output buffer.</span></span>

`outBuffer`\
<span data-ttu-id="057b6-110">[out, size_is(outBufferSize)] Ponteiro de buffer usado para armazenar a resposta da solicitação.</span><span class="sxs-lookup"><span data-stu-id="057b6-110">[out, size_is(outBufferSize)] Buffer pointer to used to store the request response.</span></span>

## <a name="remarks"></a><span data-ttu-id="057b6-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="057b6-111">Remarks</span></span>

<span data-ttu-id="057b6-112">O método fornecido é parte do `IXCLRDataModule` de interface e corresponde ao slot de 36 ª da tabela de método virtual.</span><span class="sxs-lookup"><span data-stu-id="057b6-112">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 36th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="057b6-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="057b6-113">Requirements</span></span>

<span data-ttu-id="057b6-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="057b6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="057b6-115">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="057b6-115">**Header:** None</span></span>   
<span data-ttu-id="057b6-116">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="057b6-116">**Library:** None</span></span>  
<span data-ttu-id="057b6-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="057b6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="057b6-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="057b6-118">See also</span></span>
- [<span data-ttu-id="057b6-119">Depuração</span><span class="sxs-lookup"><span data-stu-id="057b6-119">Debugging</span></span>](index.md)
- [<span data-ttu-id="057b6-120">Interface IXCLRDataModule</span><span class="sxs-lookup"><span data-stu-id="057b6-120">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)