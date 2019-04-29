---
title: Método IXCLRDataMethodInstance::GetRepresentativeEntryAddress
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
ms.openlocfilehash: 6f204e2ed9cb1409d53432355467bb11946f8809
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775519"
---
# <a name="ixclrdatamethodinstancegetrepresentativeentryaddress-method"></a><span data-ttu-id="3acd3-102">Método IXCLRDataMethodInstance::GetRepresentativeEntryAddress</span><span class="sxs-lookup"><span data-stu-id="3acd3-102">IXCLRDataMethodInstance::GetRepresentativeEntryAddress Method</span></span>

<span data-ttu-id="3acd3-103">Obtém o endereço do ponto de entrada mais representativo para a compilação nativa de todos os pontos de entrada possíveis para um método.</span><span class="sxs-lookup"><span data-stu-id="3acd3-103">Gets the most representative entry point address for the native compilation of all the possible entry points for a method.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="3acd3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3acd3-104">Syntax</span></span>

```
HRESULT GetRepresentativeEntryAddress(
    [out] CLRDATA_ADDRESS* addr
);
```

## <a name="parameters"></a><span data-ttu-id="3acd3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3acd3-105">Parameters</span></span>

`addr`\
<span data-ttu-id="3acd3-106">[out] O endereço do ponto de entrada nativo mais representativo para o método.</span><span class="sxs-lookup"><span data-stu-id="3acd3-106">[out] The address of the most representative native entry point for the method.</span></span>

## <a name="remarks"></a><span data-ttu-id="3acd3-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="3acd3-107">Remarks</span></span>

<span data-ttu-id="3acd3-108">O método fornecido faz parte de [ `IXCLRDataMethodInstance` interface](ixclrdatamethodinstance-interface.md) e corresponde ao slot de 19 da tabela de método virtual.</span><span class="sxs-lookup"><span data-stu-id="3acd3-108">The provided method is part of the [`IXCLRDataMethodInstance` interface](ixclrdatamethodinstance-interface.md) and corresponds to the 19th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="3acd3-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3acd3-109">Requirements</span></span>

<span data-ttu-id="3acd3-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3acd3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="3acd3-111">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="3acd3-111">**Header:** None</span></span>  
<span data-ttu-id="3acd3-112">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="3acd3-112">**Library:** None</span></span>  
<span data-ttu-id="3acd3-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3acd3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="3acd3-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3acd3-114">See also</span></span>

- [<span data-ttu-id="3acd3-115">Depuração</span><span class="sxs-lookup"><span data-stu-id="3acd3-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="3acd3-116">Interface IXCLRDataMethodInstance</span><span class="sxs-lookup"><span data-stu-id="3acd3-116">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
