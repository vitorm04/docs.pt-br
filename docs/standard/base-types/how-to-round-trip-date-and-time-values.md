---
title: Como aplicar uma viagem de ida e volta a valores de data e hora
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- round-trip date and time values
- dates [.NET Framework], round-trip values
- time zones [.NET Framework], round-trip date and time values
- time [.NET Framework], round-trip values
- formatting strings [.NET Framework], round-trip values
ms.assetid: b609b277-edc6-4c74-b03e-ea73324ecbdb
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 515a29e279cfa8fc100e0612fc19df7abc6a3b36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-round-trip-date-and-time-values"></a><span data-ttu-id="fc077-102">Como aplicar uma viagem de ida e volta a valores de data e hora</span><span class="sxs-lookup"><span data-stu-id="fc077-102">How to: Round-trip Date and Time Values</span></span>
<span data-ttu-id="fc077-103">Em muitos aplicativos, um valor de data e hora destina-se a identificar sem ambiguidade um único ponto no tempo.</span><span class="sxs-lookup"><span data-stu-id="fc077-103">In many applications, a date and time value is intended to unambiguously identify a single point in time.</span></span> <span data-ttu-id="fc077-104">Este tópico mostra como salvar e restaurar um <xref:System.DateTime> valor, uma <xref:System.DateTimeOffset> informações de zona valor e um valor de data e hora com o tempo para que o valor restaurado identifique o mesmo tempo que o valor salvo.</span><span class="sxs-lookup"><span data-stu-id="fc077-104">This topic shows how to save and restore a <xref:System.DateTime> value, a <xref:System.DateTimeOffset> value, and a date and time value with time zone information so that the restored value identifies the same time as the saved value.</span></span>  
  
### <a name="to-round-trip-a-datetime-value"></a><span data-ttu-id="fc077-105">Para fazer uma viagem de ida e volta de um valor DateTime</span><span class="sxs-lookup"><span data-stu-id="fc077-105">To round-trip a DateTime value</span></span>  
  
1.  <span data-ttu-id="fc077-106">Converter o <xref:System.DateTime> valor em sua representação de cadeia de caracteres ao chamar o <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> método com o especificador de formato "o".</span><span class="sxs-lookup"><span data-stu-id="fc077-106">Convert the <xref:System.DateTime> value to its string representation by calling the <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>  
  
2.  <span data-ttu-id="fc077-107">Salve a representação de cadeia de caracteres da <xref:System.DateTime> valor para um arquivo, ou passe-o por um processo, domínio de aplicativo ou fronteira de máquina.</span><span class="sxs-lookup"><span data-stu-id="fc077-107">Save the string representation of the <xref:System.DateTime> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>  
  
3.  <span data-ttu-id="fc077-108">Recuperar a cadeia de caracteres que representa o <xref:System.DateTime> valor.</span><span class="sxs-lookup"><span data-stu-id="fc077-108">Retrieve the string that represents the <xref:System.DateTime> value.</span></span>  
  
4.  <span data-ttu-id="fc077-109">Chamar o <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> método e passe <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> como o valor da `styles` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="fc077-109">Call the <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>  
  
 <span data-ttu-id="fc077-110">O exemplo a seguir ilustra como viagem um <xref:System.DateTime> valor.</span><span class="sxs-lookup"><span data-stu-id="fc077-110">The following example illustrates how to round-trip a <xref:System.DateTime> value.</span></span>  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
 [!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]  
  
 <span data-ttu-id="fc077-111">Quando ciclo um <xref:System.DateTime> valor, essa técnica preserva com êxito a hora para todos os horários locais e universais.</span><span class="sxs-lookup"><span data-stu-id="fc077-111">When round-tripping a <xref:System.DateTime> value, this technique successfully preserves the time for all local and universal times.</span></span> <span data-ttu-id="fc077-112">Por exemplo, se um local <xref:System.DateTime> valor é salvo em um sistema nos EUA. o fuso horário padrão do Pacífico será restaurado em um sistema no fuso horário padrão da região central dos EUA; a data e hora restauradas estarão duas horas à frente da hora original, o que reflete a diferença de hora entre os dois fusos horários.</span><span class="sxs-lookup"><span data-stu-id="fc077-112">For example, if a local <xref:System.DateTime> value is saved on a system in the U.S. Pacific Standard Time zone and is restored on a system in the U.S. Central Standard Time zone, the restored date and time will be two hours later than the original time, which reflects the time difference between the two time zones.</span></span> <span data-ttu-id="fc077-113">No entanto, essa técnica não é necessariamente exata para horários não especificados.</span><span class="sxs-lookup"><span data-stu-id="fc077-113">However, this technique is not necessarily accurate for unspecified times.</span></span> <span data-ttu-id="fc077-114">Todos os <xref:System.DateTime> valores cujos <xref:System.DateTime.Kind%2A> é de propriedade <xref:System.DateTimeKind.Unspecified> são tratados como se eles fossem horas locais.</span><span class="sxs-lookup"><span data-stu-id="fc077-114">All <xref:System.DateTime> values whose <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Unspecified> are treated as if they are local times.</span></span> <span data-ttu-id="fc077-115">Se não for o caso, o <xref:System.DateTime> não identificará com êxito o ponto correto no tempo.</span><span class="sxs-lookup"><span data-stu-id="fc077-115">If this is not the case, the <xref:System.DateTime> will not successfully identify the correct point in time.</span></span> <span data-ttu-id="fc077-116">A solução alternativa para essa limitação é acoplar rigorosamente um valor de data e hora com seu fuso horário para salvar e restaurar a operação.</span><span class="sxs-lookup"><span data-stu-id="fc077-116">The workaround for this limitation is to tightly couple a date and time value with its time zone for the save and restore operation.</span></span>  
  
### <a name="to-round-trip-a-datetimeoffset-value"></a><span data-ttu-id="fc077-117">Para fazer uma viagem de ida e volta de um valor DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="fc077-117">To round-trip a DateTimeOffset value</span></span>  
  
1.  <span data-ttu-id="fc077-118">Converter o <xref:System.DateTimeOffset> valor em sua representação de cadeia de caracteres ao chamar o <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> método com o especificador de formato "o".</span><span class="sxs-lookup"><span data-stu-id="fc077-118">Convert the <xref:System.DateTimeOffset> value to its string representation by calling the <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>  
  
2.  <span data-ttu-id="fc077-119">Salve a representação de cadeia de caracteres da <xref:System.DateTimeOffset> valor para um arquivo, ou passe-o por um processo, domínio de aplicativo ou fronteira de máquina.</span><span class="sxs-lookup"><span data-stu-id="fc077-119">Save the string representation of the <xref:System.DateTimeOffset> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>  
  
3.  <span data-ttu-id="fc077-120">Recuperar a cadeia de caracteres que representa o <xref:System.DateTimeOffset> valor.</span><span class="sxs-lookup"><span data-stu-id="fc077-120">Retrieve the string that represents the <xref:System.DateTimeOffset> value.</span></span>  
  
4.  <span data-ttu-id="fc077-121">Chamar o <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> método e passe <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> como o valor da `styles` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="fc077-121">Call the <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>  
  
 <span data-ttu-id="fc077-122">O exemplo a seguir ilustra como viagem um <xref:System.DateTimeOffset> valor.</span><span class="sxs-lookup"><span data-stu-id="fc077-122">The following example illustrates how to round-trip a <xref:System.DateTimeOffset> value.</span></span>  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
 [!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]  
  
 <span data-ttu-id="fc077-123">Essa técnica sempre identifica sem ambiguidade um <xref:System.DateTimeOffset> valor como um único ponto no tempo.</span><span class="sxs-lookup"><span data-stu-id="fc077-123">This technique always unambiguously identifies a <xref:System.DateTimeOffset> value as a single point in time.</span></span> <span data-ttu-id="fc077-124">O valor pode, em seguida, ser convertido para o tempo Universal Coordenado (UTC) chamando o <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> método, ou ele pode ser convertido para o tempo em um determinado fuso horário chamando o <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> ou <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="fc077-124">The value can then be converted to Coordinated Universal Time (UTC) by calling the <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> method, or it can be converted to the time in a particular time zone by calling the <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> or <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="fc077-125">A principal limitação dessa técnica é a data e hora aritmética, quando executada em um <xref:System.DateTimeOffset> valor que representa a hora em um determinado fuso horário, talvez não produza resultados precisos para esse fuso horário.</span><span class="sxs-lookup"><span data-stu-id="fc077-125">The major limitation of this technique is that date and time arithmetic, when performed on a <xref:System.DateTimeOffset> value that represents the time in a particular time zone, may not produce accurate results for that time zone.</span></span> <span data-ttu-id="fc077-126">Isso ocorre porque quando um <xref:System.DateTimeOffset> valor é instanciado, ele é dissociado do seu fuso horário.</span><span class="sxs-lookup"><span data-stu-id="fc077-126">This is because when a <xref:System.DateTimeOffset> value is instantiated, it is disassociated from its time zone.</span></span> <span data-ttu-id="fc077-127">Portanto, as regras de ajuste do fuso horário não podem mais ser aplicadas quando você executa cálculos de data e hora.</span><span class="sxs-lookup"><span data-stu-id="fc077-127">Therefore, that time zone's adjustment rules can no longer be applied when you perform date and time calculations.</span></span> <span data-ttu-id="fc077-128">É possível solucionar esse problema definindo um tipo personalizado que inclui um valor de data e hora e o respectivo fuso horário.</span><span class="sxs-lookup"><span data-stu-id="fc077-128">You can work around this problem by defining a custom type that includes both a date and time value and its accompanying time zone.</span></span>  
  
### <a name="to-round-trip-a-date-and-time-value-with-its-time-zone"></a><span data-ttu-id="fc077-129">A viagem um valor de data e hora com seu fuso horário</span><span class="sxs-lookup"><span data-stu-id="fc077-129">To round-trip a date and time value with its time zone</span></span>  
  
1.  <span data-ttu-id="fc077-130">Defina uma classe ou uma estrutura com dois campos.</span><span class="sxs-lookup"><span data-stu-id="fc077-130">Define a class or a structure with two fields.</span></span> <span data-ttu-id="fc077-131">O primeiro campo é um <xref:System.DateTime> ou um <xref:System.DateTimeOffset> objeto e o segundo é um <xref:System.TimeZoneInfo> objeto.</span><span class="sxs-lookup"><span data-stu-id="fc077-131">The first field is either a <xref:System.DateTime> or a <xref:System.DateTimeOffset> object, and the second is a <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="fc077-132">O exemplo a seguir é uma versão simple de tal tipo.</span><span class="sxs-lookup"><span data-stu-id="fc077-132">The following example is a simple version of such a type.</span></span>  
  
     [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
     [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]  
  
2.  <span data-ttu-id="fc077-133">Marcar a classe com o <xref:System.SerializableAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="fc077-133">Mark the class with the <xref:System.SerializableAttribute> attribute.</span></span>  
  
3.  <span data-ttu-id="fc077-134">Serialize o objeto usando o <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="fc077-134">Serialize the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> method.</span></span>  
  
4.  <span data-ttu-id="fc077-135">Restaure o objeto usando o <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> método.</span><span class="sxs-lookup"><span data-stu-id="fc077-135">Restore the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> method.</span></span>  
  
5.  <span data-ttu-id="fc077-136">Cast (em c#) ou converta (no Visual Basic) o objeto desserializado em um objeto do tipo apropriado.</span><span class="sxs-lookup"><span data-stu-id="fc077-136">Cast (in C#) or convert (in Visual Basic) the deserialized object to an object of the appropriate type.</span></span>  
  
 <span data-ttu-id="fc077-137">O exemplo a seguir ilustra como a viagem um objeto que armazena informações de data e hora e fuso horário.</span><span class="sxs-lookup"><span data-stu-id="fc077-137">The following example illustrates how to round-trip an object that stores both date and time and time zone information.</span></span>  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
 [!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]  
  
 <span data-ttu-id="fc077-138">Essa técnica deve refletir sempre inequivocamente o ponto correto de tempo tanto antes e depois de ser salvo e restaurado, fornecido a implementação do objeto combinado de data e hora e fuso horário não permite que o valor de data fiquem fora de sincronia com o valor de fuso horário.</span><span class="sxs-lookup"><span data-stu-id="fc077-138">This technique should always unambiguously reflect the correct point of time both before and after it is saved and restored, provided that the implementation of the combined date and time and time zone object does not allow the date value to become out of sync with the time zone value.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fc077-139">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="fc077-139">Compiling the Code</span></span>  
 <span data-ttu-id="fc077-140">Esses exemplos precisam de:</span><span class="sxs-lookup"><span data-stu-id="fc077-140">These examples require:</span></span>  
  
-   <span data-ttu-id="fc077-141">Se os seguintes namespaces importados com c# `using` instruções ou [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="fc077-141">That the following namespaces be imported with C# `using` statements or [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] `Imports` statements:</span></span>  
  
    -   <span data-ttu-id="fc077-142"><xref:System>(Apenas c#).</span><span class="sxs-lookup"><span data-stu-id="fc077-142"><xref:System> (C# only).</span></span>  
  
    -   <span data-ttu-id="fc077-143"><xref:System.Globalization?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fc077-143"><xref:System.Globalization?displayProperty=nameWithType>.</span></span>  
  
    -   <span data-ttu-id="fc077-144"><xref:System.IO?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fc077-144"><xref:System.IO?displayProperty=nameWithType>.</span></span>  
  
    -   <span data-ttu-id="fc077-145"><xref:System.Runtime.Serialization?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fc077-145"><xref:System.Runtime.Serialization?displayProperty=nameWithType>.</span></span>  
  
    -   <span data-ttu-id="fc077-146"><xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fc077-146"><xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="fc077-147">Uma referência a System.Core.dll.</span><span class="sxs-lookup"><span data-stu-id="fc077-147">A reference to System.Core.dll.</span></span>  
  
-   <span data-ttu-id="fc077-148">Cada exemplo de código, que o `DateInTimeZone` classe deve ser incluído em uma classe ou um módulo do Visual Basic, empacotado em métodos e chamado a partir de `Main` método.</span><span class="sxs-lookup"><span data-stu-id="fc077-148">Each code example, other than the `DateInTimeZone` class, should be included in a class or Visual Basic module, wrapped in methods, and called from the `Main` method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc077-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fc077-149">See Also</span></span>  
 [<span data-ttu-id="fc077-150">Executando operações de formatação</span><span class="sxs-lookup"><span data-stu-id="fc077-150">Performing Formatting Operations</span></span>](../../../docs/standard/base-types/performing-formatting-operations.md)  
 [<span data-ttu-id="fc077-151">Escolhendo entre DateTime, DateTimeOffset, TimeSpan e TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="fc077-151">Choosing Between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo</span></span>](../../../docs/standard/datetime/choosing-between-datetime.md)  
 [<span data-ttu-id="fc077-152">Cadeias de caracteres de formato de data e hora padrão</span><span class="sxs-lookup"><span data-stu-id="fc077-152">Standard Date and Time Format Strings</span></span>](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
