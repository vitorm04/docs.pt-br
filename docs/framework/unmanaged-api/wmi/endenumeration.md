---
title: Função EndEnumeration (referência de API não gerenciada)
description: A função EndEnumeration encerra uma enumeração.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d5c576cb808ee92452c193c3fbce4f1d2c2cad05
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636779"
---
# <a name="endenumeration-function"></a><span data-ttu-id="1ff7b-103">Função EndEnumeration</span><span class="sxs-lookup"><span data-stu-id="1ff7b-103">EndEnumeration function</span></span>

<span data-ttu-id="1ff7b-104">Encerra uma sequência de enumeração iniciada com uma chamada para o [função BeginEnumeration](beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="1ff7b-104">Terminates an enumeration sequence started with a call to the [BeginEnumeration function](beginenumeration.md).</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="1ff7b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1ff7b-105">Syntax</span></span>

```cpp
HRESULT EndEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr
);
```

## <a name="parameters"></a><span data-ttu-id="1ff7b-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1ff7b-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="1ff7b-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="1ff7b-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="1ff7b-108">[in] Um ponteiro para um [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instância.</span><span class="sxs-lookup"><span data-stu-id="1ff7b-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="1ff7b-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="1ff7b-109">Return value</span></span>

<span data-ttu-id="1ff7b-110">Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="1ff7b-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="1ff7b-111">Constante</span><span class="sxs-lookup"><span data-stu-id="1ff7b-111">Constant</span></span>  |<span data-ttu-id="1ff7b-112">Valor</span><span class="sxs-lookup"><span data-stu-id="1ff7b-112">Value</span></span>  |<span data-ttu-id="1ff7b-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="1ff7b-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="1ff7b-114">0x80041001</span><span class="sxs-lookup"><span data-stu-id="1ff7b-114">0x80041001</span></span> | <span data-ttu-id="1ff7b-115">Houve uma falha geral.</span><span class="sxs-lookup"><span data-stu-id="1ff7b-115">There has been a general failure.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="1ff7b-116">0</span><span class="sxs-lookup"><span data-stu-id="1ff7b-116">0</span></span> | <span data-ttu-id="1ff7b-117">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="1ff7b-117">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="1ff7b-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="1ff7b-118">Remarks</span></span>

<span data-ttu-id="1ff7b-119">Essa função encapsula uma chamada para o [IWbemClassObject::EndEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) método.</span><span class="sxs-lookup"><span data-stu-id="1ff7b-119">This function wraps a call to the [IWbemClassObject::EndEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) method.</span></span>

<span data-ttu-id="1ff7b-120">Uma chamada para o `EndEnumeration` função não é necessária, mas é recomendável porque ele libera recursos associados com a enumeração.</span><span class="sxs-lookup"><span data-stu-id="1ff7b-120">A call to the `EndEnumeration` function is not required, but it is recommended because it releases resources associated with the enumeration.</span></span> <span data-ttu-id="1ff7b-121">No entanto, os recursos são desalocados automaticamente quando a próxima enumeração for iniciada ou o objeto seja liberado.</span><span class="sxs-lookup"><span data-stu-id="1ff7b-121">However, the resources are deallocated automatically when the next enumeration is started or the object is released.</span></span>

## <a name="requirements"></a><span data-ttu-id="1ff7b-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1ff7b-122">Requirements</span></span>

<span data-ttu-id="1ff7b-123">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ff7b-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="1ff7b-124">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="1ff7b-124">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="1ff7b-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1ff7b-125">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="1ff7b-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1ff7b-126">See also</span></span>

- [<span data-ttu-id="1ff7b-127">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="1ff7b-127">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
