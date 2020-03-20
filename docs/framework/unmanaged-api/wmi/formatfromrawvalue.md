---
title: Função FormatFromRawValue (referência de API não gerenciada)
description: A função FormatFromRawValue converte dados de desempenho bruto sumidos para um formato especificado.
ms.date: 11/21/2017
api_name:
- FormatFromRawValue
api_location:
- PerfCounter.dll
api_type:
- DLLExport
f1_keywords:
- FormatFromRawValue
helpviewer_keywords:
- FormatFromRawValue function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 0a7c0b8387f0c8e2b6e2ade94f7efeede75bd758
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176832"
---
# <a name="formatfromrawvalue-function"></a><span data-ttu-id="bce6b-103">Função FormatFromRawValue</span><span class="sxs-lookup"><span data-stu-id="bce6b-103">FormatFromRawValue function</span></span>
<span data-ttu-id="bce6b-104">Converte um valor de dados de desempenho brutos para o formato especificado, ou dois valores de dados de desempenho brutos se a conversão de formato é baseada em tempo.</span><span class="sxs-lookup"><span data-stu-id="bce6b-104">Converts one raw performance data value to the specified format, or two raw performance data values if the format conversion is time-based.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="bce6b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bce6b-105">Syntax</span></span>

```cpp
int FormatFromRawValue (
   [in] uint                    dwCounterType,
   [in] uint                    dwFormat,
   [in] long*                   pTimeBase,
   [in] PDH_RAW_COUNTER*        pRawValue1,
   [in] PDH_RAW_COUNTER*        pRawValue2,
   [out] PDH_FMT_COUNTERVALUE*  pFmtValue
);
```

## <a name="parameters"></a><span data-ttu-id="bce6b-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="bce6b-106">Parameters</span></span>

`dwCounterType`\
<span data-ttu-id="bce6b-107">[em] O tipo de contador.</span><span class="sxs-lookup"><span data-stu-id="bce6b-107">[in] The counter type.</span></span> <span data-ttu-id="bce6b-108">Para obter uma lista de tipos de contador, consulte [Tipos de contador de desempenho WMI](/windows/desktop/WmiSdk/wmi-performance-counter-types).</span><span class="sxs-lookup"><span data-stu-id="bce6b-108">For a list of counter types, see [WMI Performance Counter Types](/windows/desktop/WmiSdk/wmi-performance-counter-types).</span></span> <span data-ttu-id="bce6b-109">`dwCounterType`pode ser qualquer tipo `PERF_LARGE_RAW_FRACTION` `PERF_LARGE_RAW_BASE`de contador, exceto e .</span><span class="sxs-lookup"><span data-stu-id="bce6b-109">`dwCounterType` can be any counter type except for `PERF_LARGE_RAW_FRACTION` and `PERF_LARGE_RAW_BASE`.</span></span>

`dwFormat`\
<span data-ttu-id="bce6b-110">[em] O formato para converter os dados de desempenho bruto.</span><span class="sxs-lookup"><span data-stu-id="bce6b-110">[in] The format to which to convert the raw performance data.</span></span> <span data-ttu-id="bce6b-111">Pode ser um dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="bce6b-111">It can be one of the following values:</span></span>

|<span data-ttu-id="bce6b-112">Constante</span><span class="sxs-lookup"><span data-stu-id="bce6b-112">Constant</span></span>  |<span data-ttu-id="bce6b-113">Valor</span><span class="sxs-lookup"><span data-stu-id="bce6b-113">Value</span></span>  |<span data-ttu-id="bce6b-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="bce6b-114">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |<span data-ttu-id="bce6b-115">0x00000200</span><span class="sxs-lookup"><span data-stu-id="bce6b-115">0x00000200</span></span> | <span data-ttu-id="bce6b-116">Devolva o valor calculado como um valor de ponto flutuante de dupla precisão.</span><span class="sxs-lookup"><span data-stu-id="bce6b-116">Return the calculated value as a double-precision floating point value.</span></span> |
| `PDH_FMT_LARGE` | <span data-ttu-id="bce6b-117">0x00000400</span><span class="sxs-lookup"><span data-stu-id="bce6b-117">0x00000400</span></span> | <span data-ttu-id="bce6b-118">Devolva o valor calculado como um inteiro de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="bce6b-118">Return the calculated value as a 64-bit integer.</span></span> |
| `PDH_FMT_LONG` | <span data-ttu-id="bce6b-119">0x00000100</span><span class="sxs-lookup"><span data-stu-id="bce6b-119">0x00000100</span></span> | <span data-ttu-id="bce6b-120">Devolva o valor calculado como um inteiro de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="bce6b-120">Return the calculated value as a 32-bit integer.</span></span> |

<span data-ttu-id="bce6b-121">Um dos valores anteriores pode ser ORed com uma das seguintes bandeiras de escala:</span><span class="sxs-lookup"><span data-stu-id="bce6b-121">One of the previous values can be ORed with one of the following scaling flags:</span></span>

|<span data-ttu-id="bce6b-122">Constante</span><span class="sxs-lookup"><span data-stu-id="bce6b-122">Constant</span></span>  |<span data-ttu-id="bce6b-123">Valor</span><span class="sxs-lookup"><span data-stu-id="bce6b-123">Value</span></span>  |<span data-ttu-id="bce6b-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="bce6b-124">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | <span data-ttu-id="bce6b-125">0x00001000</span><span class="sxs-lookup"><span data-stu-id="bce6b-125">0x00001000</span></span> | <span data-ttu-id="bce6b-126">Não aplique os fatores de dimensionamento do contador.</span><span class="sxs-lookup"><span data-stu-id="bce6b-126">Do not apply the counter's scaling factors.</span></span> |
| `PDH_FMT_1000` | <span data-ttu-id="bce6b-127">0x00002000</span><span class="sxs-lookup"><span data-stu-id="bce6b-127">0x00002000</span></span> | <span data-ttu-id="bce6b-128">Multiplique o valor final por 1.000.</span><span class="sxs-lookup"><span data-stu-id="bce6b-128">Multiply the final value by 1,000.</span></span> |

`pTimeBase`\
<span data-ttu-id="bce6b-129">[em] Um ponteiro para a base de tempo, se necessário para a conversão de formato.</span><span class="sxs-lookup"><span data-stu-id="bce6b-129">[in] A pointer to the time base, if necessary for the format conversion.</span></span> <span data-ttu-id="bce6b-130">Se as informações da base de tempo não forem necessárias para a conversão do formato, o valor deste parâmetro será ignorado.</span><span class="sxs-lookup"><span data-stu-id="bce6b-130">If time base information is not necessary for the format conversion, the value of this parameter is ignored.</span></span>

`pRawValue1`\
<span data-ttu-id="bce6b-131">[em] Um ponteiro [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) para uma estrutura que representa um valor bruto de desempenho.</span><span class="sxs-lookup"><span data-stu-id="bce6b-131">[in] A pointer to a [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) structure that represents a raw performance value.</span></span>

`pRawValue2`\
<span data-ttu-id="bce6b-132">[em] Um ponteiro [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) para uma estrutura que representa um segundo valor bruto de desempenho.</span><span class="sxs-lookup"><span data-stu-id="bce6b-132">[in] A pointer to a [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) structure that represents a second raw performance value.</span></span> <span data-ttu-id="bce6b-133">Se um segundo valor de desempenho bruto não `null`for necessário, este parâmetro deve ser .</span><span class="sxs-lookup"><span data-stu-id="bce6b-133">If a second raw performance value is not necessary, this parameter should be `null`.</span></span>

`pFmtValue`\
<span data-ttu-id="bce6b-134">[fora] Um ponteiro [`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue) para uma estrutura que recebe o valor de desempenho formatado.</span><span class="sxs-lookup"><span data-stu-id="bce6b-134">[out] A pointer to a [`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue) structure that receives the formatted performance value.</span></span>

## <a name="return-value"></a><span data-ttu-id="bce6b-135">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="bce6b-135">Return value</span></span>

<span data-ttu-id="bce6b-136">Os seguintes valores são retornados por esta função:</span><span class="sxs-lookup"><span data-stu-id="bce6b-136">The following values are returned by this function:</span></span>

|<span data-ttu-id="bce6b-137">Constante</span><span class="sxs-lookup"><span data-stu-id="bce6b-137">Constant</span></span>  |<span data-ttu-id="bce6b-138">Valor</span><span class="sxs-lookup"><span data-stu-id="bce6b-138">Value</span></span>  |<span data-ttu-id="bce6b-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="bce6b-139">Description</span></span>  |
|---------|---------|---------|
| `ERROR_SUCCESS` | <span data-ttu-id="bce6b-140">0</span><span class="sxs-lookup"><span data-stu-id="bce6b-140">0</span></span> | <span data-ttu-id="bce6b-141">A chamada de função é bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="bce6b-141">The function call is successful.</span></span> |
| `PDH_INVALID_ARGUMENT` | <span data-ttu-id="bce6b-142">0xC0000BBD</span><span class="sxs-lookup"><span data-stu-id="bce6b-142">0xC0000BBD</span></span> | <span data-ttu-id="bce6b-143">Um argumento necessário está faltando ou incorreto.</span><span class="sxs-lookup"><span data-stu-id="bce6b-143">A required argument is missing or incorrect.</span></span> |
| `PDH_INVALID_HANDLE` | <span data-ttu-id="bce6b-144">0xC0000BBC</span><span class="sxs-lookup"><span data-stu-id="bce6b-144">0xC0000BBC</span></span> | <span data-ttu-id="bce6b-145">A alça não é um objeto PDH válido.</span><span class="sxs-lookup"><span data-stu-id="bce6b-145">The handle is not a valid PDH object.</span></span> |

## <a name="remarks"></a><span data-ttu-id="bce6b-146">Comentários</span><span class="sxs-lookup"><span data-stu-id="bce6b-146">Remarks</span></span>

<span data-ttu-id="bce6b-147">Esta função envolve uma chamada para a função [FormatFromRawValue.](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="bce6b-147">This function wraps a call to the [FormatFromRawValue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85)) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="bce6b-148">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bce6b-148">Requirements</span></span>

 <span data-ttu-id="bce6b-149">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bce6b-149">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="bce6b-150">**Biblioteca:** PerfCounter.dll</span><span class="sxs-lookup"><span data-stu-id="bce6b-150">**Library:** PerfCounter.dll</span></span>

 <span data-ttu-id="bce6b-151">**.NET Framework Versions:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bce6b-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="bce6b-152">Confira também</span><span class="sxs-lookup"><span data-stu-id="bce6b-152">See also</span></span>

- [<span data-ttu-id="bce6b-153">WMI e Contadores de Desempenho (Referência de API Não Gerenciada)</span><span class="sxs-lookup"><span data-stu-id="bce6b-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
