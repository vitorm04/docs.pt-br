---
title: 'Método IXCLRDataProcess:: GetAppDomainByUniqueId'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::GetAppDomainByUniqueId Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::GetAppDomainByUniqueId Method
helpviewer.keywords:
- IXCLRDataProcess::GetAppDomainByUniqueId Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: bb02ffed09cbcc31e653bfd3165050c247908c5d
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420771"
---
# <a name="ixclrdataprocessgetappdomainbyuniqueid-method"></a><span data-ttu-id="34ed7-102">Método IXCLRDataProcess:: GetAppDomainByUniqueId</span><span class="sxs-lookup"><span data-stu-id="34ed7-102">IXCLRDataProcess::GetAppDomainByUniqueId Method</span></span>

<span data-ttu-id="34ed7-103">Obtém um `AppDomain` em um processo com base em seu identificador exclusivo.</span><span class="sxs-lookup"><span data-stu-id="34ed7-103">Gets an `AppDomain` in a process based on its unique identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="34ed7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="34ed7-104">Syntax</span></span>

```cpp
HRESULT GetAppDomainByUniqueID(
    [in] ULONG64               id,
    [out] IXCLRDataAppDomain **appDomain
);
```

## <a name="parameters"></a><span data-ttu-id="34ed7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34ed7-105">Parameters</span></span>

`id`\
<span data-ttu-id="34ed7-106">no O identificador exclusivo do AppDomain</span><span class="sxs-lookup"><span data-stu-id="34ed7-106">[in] The unique identifier of the AppDomain</span></span>

`appDomain`\
<span data-ttu-id="34ed7-107">fora O AppDomain</span><span class="sxs-lookup"><span data-stu-id="34ed7-107">[out] The AppDomain</span></span>

## <a name="remarks"></a><span data-ttu-id="34ed7-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="34ed7-108">Remarks</span></span>

<span data-ttu-id="34ed7-109">O método fornecido faz parte da `IXCLRDataProcess` interface e corresponde ao slot 20 da tabela de métodos virtuais.</span><span class="sxs-lookup"><span data-stu-id="34ed7-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 20th slot of the virtual method table.</span></span> <span data-ttu-id="34ed7-110">O `IXCLRDataAppDomain*` retornado é usado para interação com outras APIs.</span><span class="sxs-lookup"><span data-stu-id="34ed7-110">The `IXCLRDataAppDomain*` returned is used for interaction with other APIs.</span></span>

## <a name="requirements"></a><span data-ttu-id="34ed7-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="34ed7-111">Requirements</span></span>

<span data-ttu-id="34ed7-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34ed7-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="34ed7-113">**Cabeçalho:** Nenhuma **biblioteca:** nenhuma **.NET Framework versões:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="34ed7-113">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="34ed7-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="34ed7-114">See also</span></span>

- [<span data-ttu-id="34ed7-115">Depuração</span><span class="sxs-lookup"><span data-stu-id="34ed7-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="34ed7-116">Interface IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="34ed7-116">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
