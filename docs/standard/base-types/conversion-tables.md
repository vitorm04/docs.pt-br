---
title: "Tabelas de conversão de tipos no .NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- widening conversions
- narrowing conversions
- type conversion, table
- converting types, narrowing conversions
- converting types, widening conversions
- base types, converting
- tables [.NET Framework], type conversions
- data types [.NET Framework], converting
ms.assetid: 0ea65c59-85eb-4a52-94ca-c36d3bd13058
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 327469f9a151b6ef7e1c42f6669c0a9dae7016fd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="type-conversion-tables-in-net"></a><span data-ttu-id="ed753-102">Tabelas de conversão de tipos no .NET</span><span class="sxs-lookup"><span data-stu-id="ed753-102">Type Conversion Tables in .NET</span></span>
<span data-ttu-id="ed753-103">Conversões de expansão ocorrem quando um valor de um tipo é convertido em outro tipo de tamanho igual ou maior.</span><span class="sxs-lookup"><span data-stu-id="ed753-103">Widening conversion occurs when a value of one type is converted to another type that is of equal or greater size.</span></span> <span data-ttu-id="ed753-104">Conversões de redução ocorrem quando um valor de um tipo é convertido em um valor de outro tipo de tamanho menor.</span><span class="sxs-lookup"><span data-stu-id="ed753-104">A narrowing conversion occurs when a value of one type is converted to a value of another type that is of a smaller size.</span></span> <span data-ttu-id="ed753-105">As tabelas neste tópico ilustram os comportamentos exibidos por ambos os tipos de conversões.</span><span class="sxs-lookup"><span data-stu-id="ed753-105">The tables in this topic illustrate the behaviors exhibited by both types of conversions.</span></span>  
  
## <a name="widening-conversions"></a><span data-ttu-id="ed753-106">Conversões de expansão</span><span class="sxs-lookup"><span data-stu-id="ed753-106">Widening Conversions</span></span>  
 <span data-ttu-id="ed753-107">A tabela a seguir descreve as conversões ampliadoras que podem ser executadas sem a perda de informações.</span><span class="sxs-lookup"><span data-stu-id="ed753-107">The following table describes the widening conversions that can be performed without the loss of information.</span></span>  
  
|<span data-ttu-id="ed753-108">Tipo</span><span class="sxs-lookup"><span data-stu-id="ed753-108">Type</span></span>|<span data-ttu-id="ed753-109">Pode ser convertido sem perda de dados para</span><span class="sxs-lookup"><span data-stu-id="ed753-109">Can be converted without data loss to</span></span>|  
|----------|-------------------------------------------|  
|<xref:System.Byte>|<span data-ttu-id="ed753-110"><xref:System.UInt16>, <xref:System.Int16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="ed753-110"><xref:System.UInt16>, <xref:System.Int16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.SByte>|<span data-ttu-id="ed753-111"><xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="ed753-111"><xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.Int16>|<span data-ttu-id="ed753-112"><xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="ed753-112"><xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.UInt16>|<span data-ttu-id="ed753-113"><xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="ed753-113"><xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.Char>|<span data-ttu-id="ed753-114"><xref:System.UInt16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="ed753-114"><xref:System.UInt16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.Int32>|<span data-ttu-id="ed753-115"><xref:System.Int64>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="ed753-115"><xref:System.Int64>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.UInt32>|<span data-ttu-id="ed753-116"><xref:System.Int64>, <xref:System.UInt64>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="ed753-116"><xref:System.Int64>, <xref:System.UInt64>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.Int64>|<xref:System.Decimal>|  
|<xref:System.UInt64>|<xref:System.Decimal>|  
|<xref:System.Single>|<xref:System.Double>|  
  
 <span data-ttu-id="ed753-117">Algumas conversões de ampliação <xref:System.Single> ou <xref:System.Double> pode causar perda de precisão.</span><span class="sxs-lookup"><span data-stu-id="ed753-117">Some widening conversions to <xref:System.Single> or <xref:System.Double> can cause a loss of precision.</span></span> <span data-ttu-id="ed753-118">A tabela a seguir descreve as conversões de expansão que, às vezes, resultam em perda de informações.</span><span class="sxs-lookup"><span data-stu-id="ed753-118">The following table describes the widening conversions that sometimes result in a loss of information.</span></span>  
  
|<span data-ttu-id="ed753-119">Tipo</span><span class="sxs-lookup"><span data-stu-id="ed753-119">Type</span></span>|<span data-ttu-id="ed753-120">Pode ser convertido para</span><span class="sxs-lookup"><span data-stu-id="ed753-120">Can be converted to</span></span>|  
|----------|-------------------------|  
|<xref:System.Int32>|<xref:System.Single>|  
|<xref:System.UInt32>|<xref:System.Single>|  
|<xref:System.Int64>|<span data-ttu-id="ed753-121"><xref:System.Single>, <xref:System.Double></span><span class="sxs-lookup"><span data-stu-id="ed753-121"><xref:System.Single>, <xref:System.Double></span></span>|  
|<xref:System.UInt64>|<span data-ttu-id="ed753-122"><xref:System.Single>, <xref:System.Double></span><span class="sxs-lookup"><span data-stu-id="ed753-122"><xref:System.Single>, <xref:System.Double></span></span>|  
|<xref:System.Decimal>|<span data-ttu-id="ed753-123"><xref:System.Single>, <xref:System.Double></span><span class="sxs-lookup"><span data-stu-id="ed753-123"><xref:System.Single>, <xref:System.Double></span></span>|  
  
## <a name="narrowing-conversions"></a><span data-ttu-id="ed753-124">Conversões de redução</span><span class="sxs-lookup"><span data-stu-id="ed753-124">Narrowing Conversions</span></span>  
 <span data-ttu-id="ed753-125">Uma conversão redutora para <xref:System.Single> ou <xref:System.Double> pode causar perda de informações.</span><span class="sxs-lookup"><span data-stu-id="ed753-125">A narrowing conversion to <xref:System.Single> or <xref:System.Double> can cause a loss of information.</span></span> <span data-ttu-id="ed753-126">Se o tipo de destino não puder expressar corretamente a magnitude da origem, o tipo resultante será definido como a constante `PositiveInfinity` ou `NegativeInfinity`.</span><span class="sxs-lookup"><span data-stu-id="ed753-126">If the target type cannot properly express the magnitude of the source, the resulting type is set to the constant `PositiveInfinity` or `NegativeInfinity`.</span></span> <span data-ttu-id="ed753-127">`PositiveInfinity`resultados de divisão de um número positivo por zero e também é retornado quando o valor de um <xref:System.Single> ou <xref:System.Double> excede o valor da `MaxValue` campo.</span><span class="sxs-lookup"><span data-stu-id="ed753-127">`PositiveInfinity` results from dividing a positive number by zero and is also returned when the value of a <xref:System.Single> or <xref:System.Double> exceeds the value of the `MaxValue` field.</span></span> <span data-ttu-id="ed753-128">`NegativeInfinity`resultados de divisão por zero de um número negativo e também é retornado quando o valor de um <xref:System.Single> ou <xref:System.Double> cai abaixo do valor da `MinValue` campo.</span><span class="sxs-lookup"><span data-stu-id="ed753-128">`NegativeInfinity` results from dividing a negative number by zero and is also returned when the value of a <xref:System.Single> or <xref:System.Double> falls below the value of the `MinValue` field.</span></span> <span data-ttu-id="ed753-129">Uma conversão de um <xref:System.Double> para um <xref:System.Single> pode resultar em `PositiveInfinity` ou `NegativeInfinity`.</span><span class="sxs-lookup"><span data-stu-id="ed753-129">A conversion from a <xref:System.Double> to a <xref:System.Single> might result in `PositiveInfinity` or `NegativeInfinity`.</span></span>  
  
 <span data-ttu-id="ed753-130">Uma conversão de redução também pode resultar em perda de informações para outros tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="ed753-130">A narrowing conversion can also result in a loss of information for other data types.</span></span> <span data-ttu-id="ed753-131">No entanto, um <xref:System.OverflowException> é gerada se o valor de um tipo que está sendo convertido está fora do intervalo especificado, o tipo de destino `MaxValue` e `MinValue` campos e a conversão é verificada pelo tempo de execução para garantir que o valor de destino tipo não exceda seu `MaxValue` ou `MinValue`.</span><span class="sxs-lookup"><span data-stu-id="ed753-131">However, an <xref:System.OverflowException> is thrown if the value of a type that is being converted falls outside of the range specified by the target type's `MaxValue` and `MinValue` fields, and the conversion is checked by the runtime to ensure that the value of the target type does not exceed its `MaxValue` or `MinValue`.</span></span> <span data-ttu-id="ed753-132">Conversões executadas com a <xref:System.Convert?displayProperty=nameWithType> classe sempre são verificadas dessa maneira.</span><span class="sxs-lookup"><span data-stu-id="ed753-132">Conversions that are performed with the <xref:System.Convert?displayProperty=nameWithType> class are always checked in this manner.</span></span>  
  
 <span data-ttu-id="ed753-133">A tabela a seguir lista as conversões que lançam uma <xref:System.OverflowException> usando <xref:System.Convert?displayProperty=nameWithType> ou qualquer selecionada conversão se o valor do tipo que está sendo convertido estiver fora do intervalo definido pelo tipo resultante.</span><span class="sxs-lookup"><span data-stu-id="ed753-133">The following table lists conversions that throw an <xref:System.OverflowException> using <xref:System.Convert?displayProperty=nameWithType> or any checked conversion if the value of the type being converted is outside the defined range of the resulting type.</span></span>  
  
|<span data-ttu-id="ed753-134">Tipo</span><span class="sxs-lookup"><span data-stu-id="ed753-134">Type</span></span>|<span data-ttu-id="ed753-135">Pode ser convertido para</span><span class="sxs-lookup"><span data-stu-id="ed753-135">Can be converted to</span></span>|  
|----------|-------------------------|  
|<xref:System.Byte>|<xref:System.SByte>|  
|<xref:System.SByte>|<span data-ttu-id="ed753-136"><xref:System.Byte>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="ed753-136"><xref:System.Byte>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64></span></span>|  
|<xref:System.Int16>|<span data-ttu-id="ed753-137"><xref:System.Byte>, <xref:System.SByte>, <xref:System.UInt16></span><span class="sxs-lookup"><span data-stu-id="ed753-137"><xref:System.Byte>, <xref:System.SByte>, <xref:System.UInt16></span></span>|  
|<xref:System.UInt16>|<span data-ttu-id="ed753-138"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16></span><span class="sxs-lookup"><span data-stu-id="ed753-138"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16></span></span>|  
|<xref:System.Int32>|<span data-ttu-id="ed753-139"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>,<xref:System.UInt32></span><span class="sxs-lookup"><span data-stu-id="ed753-139"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>,<xref:System.UInt32></span></span>|  
|<xref:System.UInt32>|<span data-ttu-id="ed753-140"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="ed753-140"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32></span></span>|  
|<xref:System.Int64>|<span data-ttu-id="ed753-141"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>,<xref:System.UInt32>,<xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="ed753-141"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>,<xref:System.UInt32>,<xref:System.UInt64></span></span>|  
|<xref:System.UInt64>|<span data-ttu-id="ed753-142"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64></span><span class="sxs-lookup"><span data-stu-id="ed753-142"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64></span></span>|  
|<xref:System.Decimal>|<span data-ttu-id="ed753-143"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="ed753-143"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span></span>|  
|<xref:System.Single>|<span data-ttu-id="ed753-144"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="ed753-144"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span></span>|  
|<xref:System.Double>|<span data-ttu-id="ed753-145"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="ed753-145"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ed753-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ed753-146">See Also</span></span>  
 <xref:System.Convert?displayProperty=nameWithType>  
 [<span data-ttu-id="ed753-147">Conversão de tipo no .NET</span><span class="sxs-lookup"><span data-stu-id="ed753-147">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)
