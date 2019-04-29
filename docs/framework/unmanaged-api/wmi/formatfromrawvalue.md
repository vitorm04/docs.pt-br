---
title: Função FormatFromRawValue (referência de API não gerenciada)
description: A função FormatFromRawValue converte dados de desempenho bruto em um formato especificado.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 44a84b03c85cc1332c07ffbaf53187b7f01d0236
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609042"
---
# <a name="formatfromrawvalue-function"></a><span data-ttu-id="e8877-103">Função FormatFromRawValue</span><span class="sxs-lookup"><span data-stu-id="e8877-103">FormatFromRawValue function</span></span>
<span data-ttu-id="e8877-104">Converte um valor de dados de desempenho brutos para o formato especificado, ou dois valores de dados de desempenho brutos se a conversão de formato é baseada em tempo.</span><span class="sxs-lookup"><span data-stu-id="e8877-104">Converts one raw performance data value to the specified format, or two raw performance data values if the format conversion is time-based.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="e8877-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e8877-105">Syntax</span></span>

```
int FormatFromRawValue (
   [in] uint                    dwCounterType, 
   [in] uint                    dwFormat, 
   [in] long*                   pTimeBase,
   [in] PDH_RAW_COUNTER*        pRawValue1,
   [in] PDH_RAW_COUNTER*        pRawValue2,
   [out] PDH_FMT_COUNTERVALUE*  pFmtValue
); 
```

## <a name="parameters"></a><span data-ttu-id="e8877-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e8877-106">Parameters</span></span>

`dwCounterType`\
<span data-ttu-id="e8877-107">[in] O tipo de contador.</span><span class="sxs-lookup"><span data-stu-id="e8877-107">[in] The counter type.</span></span> <span data-ttu-id="e8877-108">Para obter uma lista dos tipos de contador, consulte [tipos de contador de desempenho WMI](/windows/desktop/WmiSdk/wmi-performance-counter-types).</span><span class="sxs-lookup"><span data-stu-id="e8877-108">For a list of counter types, see [WMI Performance Counter Types](/windows/desktop/WmiSdk/wmi-performance-counter-types).</span></span> <span data-ttu-id="e8877-109">`dwCounterType` pode ser qualquer tipo de contador, exceto `PERF_LARGE_RAW_FRACTION` e `PERF_LARGE_RAW_BASE`.</span><span class="sxs-lookup"><span data-stu-id="e8877-109">`dwCounterType` can be any counter type except for `PERF_LARGE_RAW_FRACTION` and `PERF_LARGE_RAW_BASE`.</span></span> 

`dwFormat`\
<span data-ttu-id="e8877-110">[in] O formato para o qual converter os dados de desempenho bruto.</span><span class="sxs-lookup"><span data-stu-id="e8877-110">[in] The format to which to convert the raw performance data.</span></span> <span data-ttu-id="e8877-111">Ele pode ser um dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="e8877-111">It can be one of the following values:</span></span>

|<span data-ttu-id="e8877-112">Constante</span><span class="sxs-lookup"><span data-stu-id="e8877-112">Constant</span></span>  |<span data-ttu-id="e8877-113">Valor</span><span class="sxs-lookup"><span data-stu-id="e8877-113">Value</span></span>  |<span data-ttu-id="e8877-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="e8877-114">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |<span data-ttu-id="e8877-115">0x00000200</span><span class="sxs-lookup"><span data-stu-id="e8877-115">0x00000200</span></span> | <span data-ttu-id="e8877-116">Retorna o valor calculado como um valor de ponto flutuante de precisão dupla.</span><span class="sxs-lookup"><span data-stu-id="e8877-116">Return the calculated value as a double-precision floating point value.</span></span> | 
| `PDH_FMT_LARGE` | <span data-ttu-id="e8877-117">0x00000400</span><span class="sxs-lookup"><span data-stu-id="e8877-117">0x00000400</span></span> | <span data-ttu-id="e8877-118">Retorna o valor calculado como um inteiro de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="e8877-118">Return the calculated value as a 64-bit integer.</span></span> |
| `PDH_FMT_LONG` | <span data-ttu-id="e8877-119">0x00000100</span><span class="sxs-lookup"><span data-stu-id="e8877-119">0x00000100</span></span> | <span data-ttu-id="e8877-120">Retorna o valor calculado como um inteiro de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="e8877-120">Return the calculated value as a 32-bit integer.</span></span> |

<span data-ttu-id="e8877-121">Um dos valores anteriores pode estar ORed com um dos seguintes sinalizadores de colocação em escala:</span><span class="sxs-lookup"><span data-stu-id="e8877-121">One of the previous values can be ORed with one of the following scaling flags:</span></span>

|<span data-ttu-id="e8877-122">Constante</span><span class="sxs-lookup"><span data-stu-id="e8877-122">Constant</span></span>  |<span data-ttu-id="e8877-123">Valor</span><span class="sxs-lookup"><span data-stu-id="e8877-123">Value</span></span>  |<span data-ttu-id="e8877-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="e8877-124">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | <span data-ttu-id="e8877-125">0x00001000</span><span class="sxs-lookup"><span data-stu-id="e8877-125">0x00001000</span></span> | <span data-ttu-id="e8877-126">Não se aplicam os fatores de dimensionamento do contador.</span><span class="sxs-lookup"><span data-stu-id="e8877-126">Do not apply the counter's scaling factors.</span></span> |
| `PDH_FMT_1000` | <span data-ttu-id="e8877-127">0x00002000</span><span class="sxs-lookup"><span data-stu-id="e8877-127">0x00002000</span></span> | <span data-ttu-id="e8877-128">Multiplique o valor final por 1.000.</span><span class="sxs-lookup"><span data-stu-id="e8877-128">Multiply the final value by 1,000.</span></span> | 

`pTimeBase`\
<span data-ttu-id="e8877-129">[in] Um ponteiro para a base de tempo, se necessário para a conversão de formato.</span><span class="sxs-lookup"><span data-stu-id="e8877-129">[in] A pointer to the time base, if necessary for the format conversion.</span></span> <span data-ttu-id="e8877-130">Se as informações de base de tempo não são necessárias para a conversão de formato, o valor desse parâmetro é ignorado.</span><span class="sxs-lookup"><span data-stu-id="e8877-130">If time base information is not necessary for the format conversion, the value of this parameter is ignored.</span></span>

<span data-ttu-id="e8877-131">`pRawValue1`\ [in] um ponteiro para um [ `PDH_RAW_COUNTER` ](/windows/desktop/api/pdh/ns-pdh-_pdh_raw_counter) estrutura que representa um valor de desempenho bruto.</span><span class="sxs-lookup"><span data-stu-id="e8877-131">`pRawValue1`\ [in] A pointer to a [`PDH_RAW_COUNTER`](/windows/desktop/api/pdh/ns-pdh-_pdh_raw_counter) structure that represents a raw performance value.</span></span>

`pRawValue2`\
<span data-ttu-id="e8877-132">[in] Um ponteiro para um [ `PDH_RAW_COUNTER` ](/windows/desktop/api/pdh/ns-pdh-_pdh_raw_counter) estrutura que representa um segundo valor de desempenho bruto.</span><span class="sxs-lookup"><span data-stu-id="e8877-132">[in] A pointer to a [`PDH_RAW_COUNTER`](/windows/desktop/api/pdh/ns-pdh-_pdh_raw_counter) structure that represents a second raw performance value.</span></span> <span data-ttu-id="e8877-133">Se um segundo valor de desempenho bruto não é necessário, esse parâmetro deve ser `null`.</span><span class="sxs-lookup"><span data-stu-id="e8877-133">If a second raw performance value is not necessary, this parameter should be `null`.</span></span>

`pFmtValue`\
<span data-ttu-id="e8877-134">[out] Um ponteiro para um [ `PDH_FMT_COUNTERVALUE` ](/windows/desktop/api/pdh/ns-pdh-_pdh_fmt_countervalue) estrutura que recebe o valor formatado de desempenho.</span><span class="sxs-lookup"><span data-stu-id="e8877-134">[out] A pointer to a [`PDH_FMT_COUNTERVALUE`](/windows/desktop/api/pdh/ns-pdh-_pdh_fmt_countervalue) structure that receives the formatted performance value.</span></span>

## <a name="return-value"></a><span data-ttu-id="e8877-135">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="e8877-135">Return value</span></span>

<span data-ttu-id="e8877-136">Os seguintes valores são retornados por essa função:</span><span class="sxs-lookup"><span data-stu-id="e8877-136">The following values are returned by this function:</span></span>

|<span data-ttu-id="e8877-137">Constante</span><span class="sxs-lookup"><span data-stu-id="e8877-137">Constant</span></span>  |<span data-ttu-id="e8877-138">Valor</span><span class="sxs-lookup"><span data-stu-id="e8877-138">Value</span></span>  |<span data-ttu-id="e8877-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="e8877-139">Description</span></span>  |
|---------|---------|---------|
| `ERROR_SUCCESS` | <span data-ttu-id="e8877-140">0</span><span class="sxs-lookup"><span data-stu-id="e8877-140">0</span></span> | <span data-ttu-id="e8877-141">A chamada de função for bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="e8877-141">The function call is successful.</span></span> |
| `PDH_INVALID_ARGUMENT` | <span data-ttu-id="e8877-142">0xC0000BBD</span><span class="sxs-lookup"><span data-stu-id="e8877-142">0xC0000BBD</span></span> | <span data-ttu-id="e8877-143">Um argumento necessário está ausente ou incorreto.</span><span class="sxs-lookup"><span data-stu-id="e8877-143">A required argument is missing or incorrect.</span></span> | 
| `PDH_INVALID_HANDLE` | <span data-ttu-id="e8877-144">0xC0000BBC</span><span class="sxs-lookup"><span data-stu-id="e8877-144">0xC0000BBC</span></span> | <span data-ttu-id="e8877-145">O identificador não é um objeto PDH válido.</span><span class="sxs-lookup"><span data-stu-id="e8877-145">The handle is not a valid PDH object.</span></span> |

## <a name="remarks"></a><span data-ttu-id="e8877-146">Comentários</span><span class="sxs-lookup"><span data-stu-id="e8877-146">Remarks</span></span>

<span data-ttu-id="e8877-147">Essa função encapsula uma chamada para o [FormatFromRawValue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85)) função.</span><span class="sxs-lookup"><span data-stu-id="e8877-147">This function wraps a call to the [FormatFromRawValue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85)) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="e8877-148">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e8877-148">Requirements</span></span>

 <span data-ttu-id="e8877-149">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8877-149">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="e8877-150">**Biblioteca:** PerfCounter.dll</span><span class="sxs-lookup"><span data-stu-id="e8877-150">**Library:** PerfCounter.dll</span></span>

 <span data-ttu-id="e8877-151">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e8877-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e8877-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e8877-152">See also</span></span>

- [<span data-ttu-id="e8877-153">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="e8877-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
