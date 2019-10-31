---
title: Função FormatFromRawValue (referência de API não gerenciada)
description: A função FormatFromRawValue converte dados brutos de desempenho em um formato especificado.
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
ms.openlocfilehash: 5097cfe43ae785461a1e2af1217bcbd5e8c4b79c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120282"
---
# <a name="formatfromrawvalue-function"></a><span data-ttu-id="e8984-103">Função FormatFromRawValue</span><span class="sxs-lookup"><span data-stu-id="e8984-103">FormatFromRawValue function</span></span>
<span data-ttu-id="e8984-104">Converte um valor de dados de desempenho brutos para o formato especificado, ou dois valores de dados de desempenho brutos se a conversão de formato é baseada em tempo.</span><span class="sxs-lookup"><span data-stu-id="e8984-104">Converts one raw performance data value to the specified format, or two raw performance data values if the format conversion is time-based.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="e8984-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e8984-105">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="e8984-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e8984-106">Parameters</span></span>

`dwCounterType`\
<span data-ttu-id="e8984-107">no O tipo de contador.</span><span class="sxs-lookup"><span data-stu-id="e8984-107">[in] The counter type.</span></span> <span data-ttu-id="e8984-108">Para obter uma lista de tipos de contadores, consulte [tipos de contador de desempenho WMI](/windows/desktop/WmiSdk/wmi-performance-counter-types).</span><span class="sxs-lookup"><span data-stu-id="e8984-108">For a list of counter types, see [WMI Performance Counter Types](/windows/desktop/WmiSdk/wmi-performance-counter-types).</span></span> <span data-ttu-id="e8984-109">`dwCounterType` pode ser qualquer tipo de contador, exceto `PERF_LARGE_RAW_FRACTION` e `PERF_LARGE_RAW_BASE`.</span><span class="sxs-lookup"><span data-stu-id="e8984-109">`dwCounterType` can be any counter type except for `PERF_LARGE_RAW_FRACTION` and `PERF_LARGE_RAW_BASE`.</span></span> 

`dwFormat`\
<span data-ttu-id="e8984-110">no O formato para o qual converter os dados de desempenho brutos.</span><span class="sxs-lookup"><span data-stu-id="e8984-110">[in] The format to which to convert the raw performance data.</span></span> <span data-ttu-id="e8984-111">Pode ser um dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="e8984-111">It can be one of the following values:</span></span>

|<span data-ttu-id="e8984-112">Constante</span><span class="sxs-lookup"><span data-stu-id="e8984-112">Constant</span></span>  |<span data-ttu-id="e8984-113">Valor</span><span class="sxs-lookup"><span data-stu-id="e8984-113">Value</span></span>  |<span data-ttu-id="e8984-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="e8984-114">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |<span data-ttu-id="e8984-115">0x00000200</span><span class="sxs-lookup"><span data-stu-id="e8984-115">0x00000200</span></span> | <span data-ttu-id="e8984-116">Retorna o valor calculado como um valor de ponto flutuante de precisão dupla.</span><span class="sxs-lookup"><span data-stu-id="e8984-116">Return the calculated value as a double-precision floating point value.</span></span> | 
| `PDH_FMT_LARGE` | <span data-ttu-id="e8984-117">0x00000400</span><span class="sxs-lookup"><span data-stu-id="e8984-117">0x00000400</span></span> | <span data-ttu-id="e8984-118">Retorne o valor calculado como um inteiro de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="e8984-118">Return the calculated value as a 64-bit integer.</span></span> |
| `PDH_FMT_LONG` | <span data-ttu-id="e8984-119">0x00000100</span><span class="sxs-lookup"><span data-stu-id="e8984-119">0x00000100</span></span> | <span data-ttu-id="e8984-120">Retorne o valor calculado como um inteiro de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="e8984-120">Return the calculated value as a 32-bit integer.</span></span> |

<span data-ttu-id="e8984-121">Um dos valores anteriores pode ser vinculada com um dos seguintes sinalizadores de dimensionamento:</span><span class="sxs-lookup"><span data-stu-id="e8984-121">One of the previous values can be ORed with one of the following scaling flags:</span></span>

|<span data-ttu-id="e8984-122">Constante</span><span class="sxs-lookup"><span data-stu-id="e8984-122">Constant</span></span>  |<span data-ttu-id="e8984-123">Valor</span><span class="sxs-lookup"><span data-stu-id="e8984-123">Value</span></span>  |<span data-ttu-id="e8984-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="e8984-124">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | <span data-ttu-id="e8984-125">0x00001000</span><span class="sxs-lookup"><span data-stu-id="e8984-125">0x00001000</span></span> | <span data-ttu-id="e8984-126">Não aplique os fatores de dimensionamento do contador.</span><span class="sxs-lookup"><span data-stu-id="e8984-126">Do not apply the counter's scaling factors.</span></span> |
| `PDH_FMT_1000` | <span data-ttu-id="e8984-127">0x00002000</span><span class="sxs-lookup"><span data-stu-id="e8984-127">0x00002000</span></span> | <span data-ttu-id="e8984-128">Multiplique o valor final por 1.000.</span><span class="sxs-lookup"><span data-stu-id="e8984-128">Multiply the final value by 1,000.</span></span> | 

`pTimeBase`\
<span data-ttu-id="e8984-129">no Um ponteiro para a base de tempo, se necessário para a conversão de formato.</span><span class="sxs-lookup"><span data-stu-id="e8984-129">[in] A pointer to the time base, if necessary for the format conversion.</span></span> <span data-ttu-id="e8984-130">Se as informações de base de tempo não forem necessárias para a conversão de formato, o valor desse parâmetro será ignorado.</span><span class="sxs-lookup"><span data-stu-id="e8984-130">If time base information is not necessary for the format conversion, the value of this parameter is ignored.</span></span>

<span data-ttu-id="e8984-131">`pRawValue1`\ [in] um ponteiro para uma estrutura de [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) que representa um valor de desempenho bruto.</span><span class="sxs-lookup"><span data-stu-id="e8984-131">`pRawValue1`\ [in] A pointer to a [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) structure that represents a raw performance value.</span></span>

`pRawValue2`\
<span data-ttu-id="e8984-132">no Um ponteiro para uma estrutura de [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) que representa um segundo valor de desempenho bruto.</span><span class="sxs-lookup"><span data-stu-id="e8984-132">[in] A pointer to a [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) structure that represents a second raw performance value.</span></span> <span data-ttu-id="e8984-133">Se um segundo valor de desempenho bruto não for necessário, esse parâmetro deverá ser `null`.</span><span class="sxs-lookup"><span data-stu-id="e8984-133">If a second raw performance value is not necessary, this parameter should be `null`.</span></span>

`pFmtValue`\
<span data-ttu-id="e8984-134">fora Um ponteiro para uma estrutura de [`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue) que recebe o valor de desempenho formatado.</span><span class="sxs-lookup"><span data-stu-id="e8984-134">[out] A pointer to a [`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue) structure that receives the formatted performance value.</span></span>

## <a name="return-value"></a><span data-ttu-id="e8984-135">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="e8984-135">Return value</span></span>

<span data-ttu-id="e8984-136">Os valores a seguir são retornados por essa função:</span><span class="sxs-lookup"><span data-stu-id="e8984-136">The following values are returned by this function:</span></span>

|<span data-ttu-id="e8984-137">Constante</span><span class="sxs-lookup"><span data-stu-id="e8984-137">Constant</span></span>  |<span data-ttu-id="e8984-138">Valor</span><span class="sxs-lookup"><span data-stu-id="e8984-138">Value</span></span>  |<span data-ttu-id="e8984-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="e8984-139">Description</span></span>  |
|---------|---------|---------|
| `ERROR_SUCCESS` | <span data-ttu-id="e8984-140">0</span><span class="sxs-lookup"><span data-stu-id="e8984-140">0</span></span> | <span data-ttu-id="e8984-141">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="e8984-141">The function call is successful.</span></span> |
| `PDH_INVALID_ARGUMENT` | <span data-ttu-id="e8984-142">0xC0000BBD</span><span class="sxs-lookup"><span data-stu-id="e8984-142">0xC0000BBD</span></span> | <span data-ttu-id="e8984-143">Um argumento necessário está ausente ou incorreto.</span><span class="sxs-lookup"><span data-stu-id="e8984-143">A required argument is missing or incorrect.</span></span> | 
| `PDH_INVALID_HANDLE` | <span data-ttu-id="e8984-144">0xC0000BBC</span><span class="sxs-lookup"><span data-stu-id="e8984-144">0xC0000BBC</span></span> | <span data-ttu-id="e8984-145">O identificador não é um objeto PDH válido.</span><span class="sxs-lookup"><span data-stu-id="e8984-145">The handle is not a valid PDH object.</span></span> |

## <a name="remarks"></a><span data-ttu-id="e8984-146">Comentários</span><span class="sxs-lookup"><span data-stu-id="e8984-146">Remarks</span></span>

<span data-ttu-id="e8984-147">Essa função encapsula uma chamada para a função [FormatFromRawValue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85)) .</span><span class="sxs-lookup"><span data-stu-id="e8984-147">This function wraps a call to the [FormatFromRawValue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85)) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="e8984-148">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e8984-148">Requirements</span></span>

 <span data-ttu-id="e8984-149">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8984-149">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="e8984-150">**Biblioteca:** PerfCounter. dll</span><span class="sxs-lookup"><span data-stu-id="e8984-150">**Library:** PerfCounter.dll</span></span>

 <span data-ttu-id="e8984-151">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e8984-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e8984-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e8984-152">See also</span></span>

- [<span data-ttu-id="e8984-153">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="e8984-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
