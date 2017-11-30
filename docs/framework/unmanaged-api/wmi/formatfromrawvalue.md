---
title: "Função FormatFromRawValue (referência de API não gerenciada)"
description: "A função FormatFromRawValue converte dados de desempenho bruto em um formato especificado."
ms.date: 11/21/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: FormatFromRawValue
api_location: PerfCounter.dll
api_type: DLLExport
f1_keywords: FormatFromRawValue
helpviewer_keywords: FormatFromRawValue function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c01db47b5362d7048e2e5ecd1b63acfe03eff860
ms.sourcegitcommit: 43c656811dd38a66a6672084c65d10c0cbbf2015
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2017
---
# <a name="formatfromrawvalue-function"></a><span data-ttu-id="d69d1-103">Função FormatFromRawValue</span><span class="sxs-lookup"><span data-stu-id="d69d1-103">FormatFromRawValue function</span></span>
<span data-ttu-id="d69d1-104">Converte um valor de dados de desempenho bruto para o formato especificado ou dois valores de dados de desempenho bruto se a conversão de formato é baseado no tempo.</span><span class="sxs-lookup"><span data-stu-id="d69d1-104">Converts one raw performance data value to the specified format, or two raw performance data values if the format conversion is time-based.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="d69d1-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d69d1-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="d69d1-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d69d1-106">Parameters</span></span>

`dwCounterType`  
<span data-ttu-id="d69d1-107">[in] O tipo de contador.</span><span class="sxs-lookup"><span data-stu-id="d69d1-107">[in] The counter type.</span></span> <span data-ttu-id="d69d1-108">Para obter uma lista dos tipos de contador, consulte [tipos de contador de desempenho WMI](https://msdn.microsoft.com/library/aa394569(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="d69d1-108">For a list of counter types, see [WMI Performance Counter Types](https://msdn.microsoft.com/library/aa394569(v=vs.85).aspx).</span></span> <span data-ttu-id="d69d1-109">`dwCounterType`pode ser qualquer tipo de contador, exceto para `PERF_LARGE_RAW_FRACTION` e `PERF_LARGE_RAW_BASE`.</span><span class="sxs-lookup"><span data-stu-id="d69d1-109">`dwCounterType` can be any counter type except for `PERF_LARGE_RAW_FRACTION` and `PERF_LARGE_RAW_BASE`.</span></span> 

`dwFormat`  
<span data-ttu-id="d69d1-110">[in] O formato no qual converter os dados de desempenho bruto.</span><span class="sxs-lookup"><span data-stu-id="d69d1-110">[in] The format to which to convert the raw performance data.</span></span> <span data-ttu-id="d69d1-111">Pode ser um dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="d69d1-111">It can be one of the following values:</span></span>

|<span data-ttu-id="d69d1-112">Constante</span><span class="sxs-lookup"><span data-stu-id="d69d1-112">Constant</span></span>  |<span data-ttu-id="d69d1-113">Valor</span><span class="sxs-lookup"><span data-stu-id="d69d1-113">Value</span></span>  |<span data-ttu-id="d69d1-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="d69d1-114">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |<span data-ttu-id="d69d1-115">0x00000200</span><span class="sxs-lookup"><span data-stu-id="d69d1-115">0x00000200</span></span> | <span data-ttu-id="d69d1-116">Retorna o valor calculado como um valor de ponto flutuante de precisão dupla.</span><span class="sxs-lookup"><span data-stu-id="d69d1-116">Return the calculated value as a double-precision floating point value.</span></span> | 
| `PDH_FMT_LARGE` | <span data-ttu-id="d69d1-117">0x00000400</span><span class="sxs-lookup"><span data-stu-id="d69d1-117">0x00000400</span></span> | <span data-ttu-id="d69d1-118">Retorna o valor calculado como um inteiro de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="d69d1-118">Return the calculated value as a 64-bit integer.</span></span> |
| `PDH_FMT_LONG` | <span data-ttu-id="d69d1-119">0x00000100</span><span class="sxs-lookup"><span data-stu-id="d69d1-119">0x00000100</span></span> | <span data-ttu-id="d69d1-120">Retorna o valor calculado como um inteiro de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="d69d1-120">Return the calculated value as a 32-bit integer.</span></span> |

<span data-ttu-id="d69d1-121">Um dos valores anteriores pode ser ORed com um dos seguintes sinalizadores de dimensionamento:</span><span class="sxs-lookup"><span data-stu-id="d69d1-121">One of the previous values can be ORed with one of the following scaling flags:</span></span>

|<span data-ttu-id="d69d1-122">Constante</span><span class="sxs-lookup"><span data-stu-id="d69d1-122">Constant</span></span>  |<span data-ttu-id="d69d1-123">Valor</span><span class="sxs-lookup"><span data-stu-id="d69d1-123">Value</span></span>  |<span data-ttu-id="d69d1-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="d69d1-124">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | <span data-ttu-id="d69d1-125">0x00001000</span><span class="sxs-lookup"><span data-stu-id="d69d1-125">0x00001000</span></span> | <span data-ttu-id="d69d1-126">Não aplique os fatores de dimensionamento do contador.</span><span class="sxs-lookup"><span data-stu-id="d69d1-126">Do not apply the counter's scaling factors.</span></span> |
| `PDH_FMT_1000` | <span data-ttu-id="d69d1-127">0x00002000</span><span class="sxs-lookup"><span data-stu-id="d69d1-127">0x00002000</span></span> | <span data-ttu-id="d69d1-128">Multiplica o valor final por 1.000.</span><span class="sxs-lookup"><span data-stu-id="d69d1-128">Multiply the final value by 1,000.</span></span> | 

`pTimeBase`  
<span data-ttu-id="d69d1-129">[in] Um ponteiro para a base de tempo para a conversão de formato, se necessário.</span><span class="sxs-lookup"><span data-stu-id="d69d1-129">[in] A pointer to the time base, if necessary for the format conversion.</span></span> <span data-ttu-id="d69d1-130">Se as informações de base de tempo não são necessárias para a conversão de formato, o valor desse parâmetro é ignorado.</span><span class="sxs-lookup"><span data-stu-id="d69d1-130">If time base information is not necessary for the format conversion, the value of this parameter is ignored.</span></span>

<span data-ttu-id="d69d1-131">`pRawValue1`[in] Um ponteiro para um [ `PDH_RAW_COUNTER` ](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) estrutura que representa um valor de desempenho bruto.</span><span class="sxs-lookup"><span data-stu-id="d69d1-131">`pRawValue1` [in] A pointer to a [`PDH_RAW_COUNTER`](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) structure that represents a raw performance value.</span></span>

<span data-ttu-id="d69d1-132">`pRawValue2`[in] Um ponteiro para um [ `PDH_RAW_COUNTER` ](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) estrutura que representa um segundo valor de desempenho bruto.</span><span class="sxs-lookup"><span data-stu-id="d69d1-132">`pRawValue2` [in] A pointer to a [`PDH_RAW_COUNTER`](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) structure that represents a second raw performance value.</span></span> <span data-ttu-id="d69d1-133">Se um segundo valor de desempenho bruto não é necessário, esse parâmetro deve ser `null`.</span><span class="sxs-lookup"><span data-stu-id="d69d1-133">If a second raw performance value is not necessary, this parameter should be `null`.</span></span>

<span data-ttu-id="d69d1-134">`pFmtValue`[out] Um ponteiro para um [ `PDH_FMT_COUNTERVALUE` ](https://msdn.microsoft.com/library/windows/desktop/aa373050(v=vs.85).aspx) estrutura que recebe o valor formatado de desempenho.</span><span class="sxs-lookup"><span data-stu-id="d69d1-134">`pFmtValue` [out] A pointer to a [`PDH_FMT_COUNTERVALUE`](https://msdn.microsoft.com/library/windows/desktop/aa373050(v=vs.85).aspx) structure that receives the formatted performance value.</span></span>

## <a name="return-value"></a><span data-ttu-id="d69d1-135">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="d69d1-135">Return value</span></span>

<span data-ttu-id="d69d1-136">Os seguintes valores são retornados por essa função:</span><span class="sxs-lookup"><span data-stu-id="d69d1-136">The following values are returned by this function:</span></span>

|<span data-ttu-id="d69d1-137">Constante</span><span class="sxs-lookup"><span data-stu-id="d69d1-137">Constant</span></span>  |<span data-ttu-id="d69d1-138">Valor</span><span class="sxs-lookup"><span data-stu-id="d69d1-138">Value</span></span>  |<span data-ttu-id="d69d1-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="d69d1-139">Description</span></span>  |
|---------|---------|---------|
| `ERROR_SUCCESS` | <span data-ttu-id="d69d1-140">0</span><span class="sxs-lookup"><span data-stu-id="d69d1-140">0</span></span> | <span data-ttu-id="d69d1-141">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="d69d1-141">The function call is successful.</span></span> |
| `PDH_INVALID_ARGUMENT` | <span data-ttu-id="d69d1-142">0xC0000BBD</span><span class="sxs-lookup"><span data-stu-id="d69d1-142">0xC0000BBD</span></span> | <span data-ttu-id="d69d1-143">Um argumento necessário está ausente ou incorreto.</span><span class="sxs-lookup"><span data-stu-id="d69d1-143">A required argument is missing or incorrect.</span></span> | 
| `PDH_INVALID_HANDLE` | <span data-ttu-id="d69d1-144">0xC0000BBC</span><span class="sxs-lookup"><span data-stu-id="d69d1-144">0xC0000BBC</span></span> | <span data-ttu-id="d69d1-145">O identificador não é um objeto PDH válido.</span><span class="sxs-lookup"><span data-stu-id="d69d1-145">The handle is not a valid PDH object.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="d69d1-146">Comentários</span><span class="sxs-lookup"><span data-stu-id="d69d1-146">Remarks</span></span>

<span data-ttu-id="d69d1-147">Essa função encapsula uma chamada para o [FormatFromRawValue](https://msdn.microsoft.com/library/ms231047(v=vs.85).aspx) função.</span><span class="sxs-lookup"><span data-stu-id="d69d1-147">This function wraps a call to the [FormatFromRawValue](https://msdn.microsoft.com/library/ms231047(v=vs.85).aspx) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="d69d1-148">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d69d1-148">Requirements</span></span>  
 <span data-ttu-id="d69d1-149">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d69d1-149">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d69d1-150">**Biblioteca:** PerfCounter.dll</span><span class="sxs-lookup"><span data-stu-id="d69d1-150">**Library:** PerfCounter.dll</span></span>  
  
 <span data-ttu-id="d69d1-151">**Versões do .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d69d1-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d69d1-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d69d1-152">See also</span></span>  
[<span data-ttu-id="d69d1-153">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="d69d1-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
