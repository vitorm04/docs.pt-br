---
title: Função endenumeration (referência de API não gerenciada)
description: A função endenumeration encerra uma enumeração.
ms.date: 11/06/2017
api_name:
- EndEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- EndEnumeration
helpviewer_keywords:
- EndEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: b9fd1f094c8fb56c94421a07437aa25a3549c487
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132038"
---
# <a name="endenumeration-function"></a><span data-ttu-id="c9ab8-103">Função EndEnumeration</span><span class="sxs-lookup"><span data-stu-id="c9ab8-103">EndEnumeration function</span></span>

<span data-ttu-id="c9ab8-104">Encerra uma sequência de enumeração iniciada com uma chamada para a [função BeginEnumeration](beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="c9ab8-104">Terminates an enumeration sequence started with a call to the [BeginEnumeration function](beginenumeration.md).</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="c9ab8-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c9ab8-105">Syntax</span></span>

```cpp
HRESULT EndEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr
);
```

## <a name="parameters"></a><span data-ttu-id="c9ab8-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c9ab8-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="c9ab8-107">no Este parâmetro não é usado.</span><span class="sxs-lookup"><span data-stu-id="c9ab8-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="c9ab8-108">no Um ponteiro para uma instância de [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="c9ab8-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="c9ab8-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="c9ab8-109">Return value</span></span>

<span data-ttu-id="c9ab8-110">Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="c9ab8-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="c9ab8-111">Constante</span><span class="sxs-lookup"><span data-stu-id="c9ab8-111">Constant</span></span>  |<span data-ttu-id="c9ab8-112">Valor</span><span class="sxs-lookup"><span data-stu-id="c9ab8-112">Value</span></span>  |<span data-ttu-id="c9ab8-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9ab8-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="c9ab8-114">0x80041001</span><span class="sxs-lookup"><span data-stu-id="c9ab8-114">0x80041001</span></span> | <span data-ttu-id="c9ab8-115">Houve uma falha geral.</span><span class="sxs-lookup"><span data-stu-id="c9ab8-115">There has been a general failure.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="c9ab8-116">0</span><span class="sxs-lookup"><span data-stu-id="c9ab8-116">0</span></span> | <span data-ttu-id="c9ab8-117">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="c9ab8-117">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="c9ab8-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="c9ab8-118">Remarks</span></span>

<span data-ttu-id="c9ab8-119">Essa função encapsula uma chamada para o método [IWbemClassObject:: endenumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="c9ab8-119">This function wraps a call to the [IWbemClassObject::EndEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) method.</span></span>

<span data-ttu-id="c9ab8-120">Uma chamada para a função `EndEnumeration` não é necessária, mas é recomendada porque libera recursos associados à enumeração.</span><span class="sxs-lookup"><span data-stu-id="c9ab8-120">A call to the `EndEnumeration` function is not required, but it is recommended because it releases resources associated with the enumeration.</span></span> <span data-ttu-id="c9ab8-121">No entanto, os recursos são desalocados automaticamente quando a próxima enumeração é iniciada ou o objeto é liberado.</span><span class="sxs-lookup"><span data-stu-id="c9ab8-121">However, the resources are deallocated automatically when the next enumeration is started or the object is released.</span></span>

## <a name="requirements"></a><span data-ttu-id="c9ab8-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c9ab8-122">Requirements</span></span>

<span data-ttu-id="c9ab8-123">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9ab8-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="c9ab8-124">**Cabeçalho:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="c9ab8-124">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="c9ab8-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c9ab8-125">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="c9ab8-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9ab8-126">See also</span></span>

- [<span data-ttu-id="c9ab8-127">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="c9ab8-127">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
