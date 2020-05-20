---
title: 'Método IXCLRDataMethodInstance:: GetRepresentativeEntryAddress'
ms.date: 02/01/2019
api.name:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress
helpviewer.keywords:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: d546cda5c68732e75550a3de286089f7df261c91
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420897"
---
# <a name="ixclrdatamethodinstancegetrepresentativeentryaddress-method"></a><span data-ttu-id="4c63a-102">Método IXCLRDataMethodInstance:: GetRepresentativeEntryAddress</span><span class="sxs-lookup"><span data-stu-id="4c63a-102">IXCLRDataMethodInstance::GetRepresentativeEntryAddress Method</span></span>

<span data-ttu-id="4c63a-103">Obtém o endereço de ponto de entrada mais representativo para a compilação nativa de todos os pontos de entrada possíveis para um método.</span><span class="sxs-lookup"><span data-stu-id="4c63a-103">Gets the most representative entry point address for the native compilation of all the possible entry points for a method.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="4c63a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4c63a-104">Syntax</span></span>

```cpp
HRESULT GetRepresentativeEntryAddress(
    [out] CLRDATA_ADDRESS* addr
);
```

## <a name="parameters"></a><span data-ttu-id="4c63a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4c63a-105">Parameters</span></span>

`addr`\
<span data-ttu-id="4c63a-106">fora O endereço do ponto de entrada nativo mais representativo para o método.</span><span class="sxs-lookup"><span data-stu-id="4c63a-106">[out] The address of the most representative native entry point for the method.</span></span>

## <a name="remarks"></a><span data-ttu-id="4c63a-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="4c63a-107">Remarks</span></span>

<span data-ttu-id="4c63a-108">O método fornecido faz parte da [ `IXCLRDataMethodInstance` interface](ixclrdatamethodinstance-interface.md) e corresponde ao slot 20 da tabela de métodos virtuais.</span><span class="sxs-lookup"><span data-stu-id="4c63a-108">The provided method is part of the [`IXCLRDataMethodInstance` interface](ixclrdatamethodinstance-interface.md) and corresponds to the 20th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="4c63a-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4c63a-109">Requirements</span></span>

<span data-ttu-id="4c63a-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c63a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="4c63a-111">**Cabeçalho:** None</span><span class="sxs-lookup"><span data-stu-id="4c63a-111">**Header:** None</span></span>  
<span data-ttu-id="4c63a-112">**Biblioteca:** None</span><span class="sxs-lookup"><span data-stu-id="4c63a-112">**Library:** None</span></span>  
<span data-ttu-id="4c63a-113">**.NET Framework versões:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4c63a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="4c63a-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="4c63a-114">See also</span></span>

- [<span data-ttu-id="4c63a-115">Depuração</span><span class="sxs-lookup"><span data-stu-id="4c63a-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="4c63a-116">Interface IXCLRDataMethodInstance</span><span class="sxs-lookup"><span data-stu-id="4c63a-116">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
