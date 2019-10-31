---
title: Função GetHashFromBlob
ms.date: 03/30/2017
api_name:
- GetHashFromBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromBlob
helpviewer_keywords:
- GetHashFromBlob function [.NET Framework strong naming]
ms.assetid: b712d862-f2d0-4b55-87d4-65bbeadef982
topic_type:
- apiref
ms.openlocfilehash: d1027aea1d800bda1654b223fec992aa70efd4b7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140716"
---
# <a name="gethashfromblob-function"></a><span data-ttu-id="ac74f-102">Função GetHashFromBlob</span><span class="sxs-lookup"><span data-stu-id="ac74f-102">GetHashFromBlob Function</span></span>

<span data-ttu-id="ac74f-103">Obtém um hash do assembly no endereço de memória especificado, usando o algoritmo de hash especificado.</span><span class="sxs-lookup"><span data-stu-id="ac74f-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>

<span data-ttu-id="ac74f-104">Esta função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="ac74f-104">This function has been deprecated.</span></span> <span data-ttu-id="ac74f-105">Em vez disso, use o método [ICLRStrongName:: GetHashFromBlob](../hosting/iclrstrongname-gethashfromblob-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ac74f-105">Use the [ICLRStrongName::GetHashFromBlob](../hosting/iclrstrongname-gethashfromblob-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="ac74f-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ac74f-106">Syntax</span></span>

```cpp
HRESULT GetHashFromBlob (
    [in]  BYTE    *pbBlob,
    [in]  DWORD   cchBlob,
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE    *pbHash,
    [in]  DWORD   cchHash,
    [out] DWORD   *pchHash
);
```

## <a name="parameters"></a><span data-ttu-id="ac74f-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ac74f-107">Parameters</span></span>

`pbBlob`\
<span data-ttu-id="ac74f-108">no Um ponteiro para o endereço do bloco de memória com hash.</span><span class="sxs-lookup"><span data-stu-id="ac74f-108">[in] A pointer to the address of the memory block to be hashed.</span></span>

`cchBlob`\
<span data-ttu-id="ac74f-109">no O comprimento, em bytes, do bloco de memória.</span><span class="sxs-lookup"><span data-stu-id="ac74f-109">[in] The length, in bytes, of the memory block.</span></span>

`piHashAlg`\
<span data-ttu-id="ac74f-110">[entrada, saída] Uma constante que especifica o algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="ac74f-110">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="ac74f-111">Use zero para o algoritmo padrão.</span><span class="sxs-lookup"><span data-stu-id="ac74f-111">Use zero for the default algorithm.</span></span>

`pbHash`\
<span data-ttu-id="ac74f-112">fora O buffer de hash retornado.</span><span class="sxs-lookup"><span data-stu-id="ac74f-112">[out] The returned hash buffer.</span></span>

`cchHash`\
<span data-ttu-id="ac74f-113">no O tamanho máximo solicitado de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="ac74f-113">[in] The requested maximum size of `pbHash`.</span></span>

`pchHash`\
<span data-ttu-id="ac74f-114">fora O tamanho, em bytes, do `pbHash`retornado.</span><span class="sxs-lookup"><span data-stu-id="ac74f-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>

## <a name="requirements"></a><span data-ttu-id="ac74f-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ac74f-115">Requirements</span></span>

<span data-ttu-id="ac74f-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac74f-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="ac74f-117">**Cabeçalho:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="ac74f-117">**Header:** StrongName.h</span></span>

<span data-ttu-id="ac74f-118">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ac74f-118">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="ac74f-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac74f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ac74f-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac74f-120">See also</span></span>

- [<span data-ttu-id="ac74f-121">Método GetHashFromBlob</span><span class="sxs-lookup"><span data-stu-id="ac74f-121">GetHashFromBlob Method</span></span>](../hosting/iclrstrongname-gethashfromblob-method.md)
- [<span data-ttu-id="ac74f-122">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="ac74f-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
