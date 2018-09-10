---
title: Como aplicar uma viagem de ida e volta a valores de data e hora
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 55b16d135449cad8ed489a8a3e21db326be0fae0
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44193257"
---
# <a name="how-to-round-trip-date-and-time-values"></a><span data-ttu-id="8fc1a-102">Como aplicar uma viagem de ida e volta a valores de data e hora</span><span class="sxs-lookup"><span data-stu-id="8fc1a-102">How to: Round-trip Date and Time Values</span></span>
<span data-ttu-id="8fc1a-103">Em muitos aplicativos, um valor de data e hora destina-se a identificar sem ambiguidade um único ponto no tempo.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-103">In many applications, a date and time value is intended to unambiguously identify a single point in time.</span></span> <span data-ttu-id="8fc1a-104">Este tópico mostra como salvar e restaurar um valor <xref:System.DateTime> e um valor <xref:System.DateTimeOffset> para que o valor restaurado identifique o mesmo horário que o valor salvo.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-104">This topic shows how to save and restore a <xref:System.DateTime> value, a <xref:System.DateTimeOffset> value, and a date and time value with time zone information so that the restored value identifies the same time as the saved value.</span></span>  
  
### <a name="to-round-trip-a-datetime-value"></a><span data-ttu-id="8fc1a-105">Para fazer uma viagem de ida e volta de um valor DateTime</span><span class="sxs-lookup"><span data-stu-id="8fc1a-105">To round-trip a DateTime value</span></span>  
  
1.  <span data-ttu-id="8fc1a-106">Converta o valor <xref:System.DateTime> em sua representação de cadeia de caracteres chamando o método <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> com o especificador de formato "o".</span><span class="sxs-lookup"><span data-stu-id="8fc1a-106">Convert the <xref:System.DateTime> value to its string representation by calling the <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>  
  
2.  <span data-ttu-id="8fc1a-107">Salve a representação de cadeia de caracteres do valor <xref:System.DateTime> em um arquivo ou passe-a por um processo, domínio de aplicativo ou limite de computador.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-107">Save the string representation of the <xref:System.DateTime> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>  
  
3.  <span data-ttu-id="8fc1a-108">Recupere a cadeia de caracteres que representa o valor <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-108">Retrieve the string that represents the <xref:System.DateTime> value.</span></span>  
  
4.  <span data-ttu-id="8fc1a-109">Chame o método <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> e passe <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> como o valor do parâmetro `styles`.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-109">Call the <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>  
  
 <span data-ttu-id="8fc1a-110">O exemplo a seguir mostra como fazer a viagem de ida e volta de um valor <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-110">The following example illustrates how to round-trip a <xref:System.DateTime> value.</span></span>  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
 [!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]  
  
 <span data-ttu-id="8fc1a-111">Fazendo a viagem de ida e volta de um valor <xref:System.DateTime>, essa técnica consegue preservar o horário para todos os horários locais e universais.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-111">When round-tripping a <xref:System.DateTime> value, this technique successfully preserves the time for all local and universal times.</span></span> <span data-ttu-id="8fc1a-112">Por exemplo, se um valor <xref:System.DateTime> local for salvo em um sistema nos EUA, o fuso horário padrão do Pacífico será restaurado em um sistema no fuso horário padrão da região central dos EUA; a data e hora restauradas estarão duas horas à frente da hora original, o que reflete a diferença de hora entre os dois fusos horários.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-112">For example, if a local <xref:System.DateTime> value is saved on a system in the U.S. Pacific Standard Time zone and is restored on a system in the U.S. Central Standard Time zone, the restored date and time will be two hours later than the original time, which reflects the time difference between the two time zones.</span></span> <span data-ttu-id="8fc1a-113">No entanto, essa técnica não é necessariamente exata para horários não especificados.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-113">However, this technique is not necessarily accurate for unspecified times.</span></span> <span data-ttu-id="8fc1a-114">Todos os valores <xref:System.DateTime> cuja propriedade <xref:System.DateTime.Kind%2A> é <xref:System.DateTimeKind.Unspecified> são tratados como se fossem horários locais.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-114">All <xref:System.DateTime> values whose <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Unspecified> are treated as if they are local times.</span></span> <span data-ttu-id="8fc1a-115">Se não for o caso, <xref:System.DateTime> não conseguirá identificar o momento correto.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-115">If this is not the case, the <xref:System.DateTime> will not successfully identify the correct point in time.</span></span> <span data-ttu-id="8fc1a-116">A solução alternativa para essa limitação é acoplar rigorosamente um valor de data e hora com seu fuso horário para salvar e restaurar a operação.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-116">The workaround for this limitation is to tightly couple a date and time value with its time zone for the save and restore operation.</span></span>  
  
### <a name="to-round-trip-a-datetimeoffset-value"></a><span data-ttu-id="8fc1a-117">Para fazer uma viagem de ida e volta de um valor DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="8fc1a-117">To round-trip a DateTimeOffset value</span></span>  
  
1.  <span data-ttu-id="8fc1a-118">Converta o valor <xref:System.DateTimeOffset> em sua representação de cadeia de caracteres chamando o método <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> com o especificador de formato "o".</span><span class="sxs-lookup"><span data-stu-id="8fc1a-118">Convert the <xref:System.DateTimeOffset> value to its string representation by calling the <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>  
  
2.  <span data-ttu-id="8fc1a-119">Salve a representação de cadeia de caracteres do valor <xref:System.DateTimeOffset> em um arquivo ou passe-a por um processo, domínio de aplicativo ou limite de computador.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-119">Save the string representation of the <xref:System.DateTimeOffset> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>  
  
3.  <span data-ttu-id="8fc1a-120">Recupere a cadeia de caracteres que representa o valor <xref:System.DateTimeOffset>.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-120">Retrieve the string that represents the <xref:System.DateTimeOffset> value.</span></span>  
  
4.  <span data-ttu-id="8fc1a-121">Chame o método <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> e passe <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> como o valor do parâmetro `styles`.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-121">Call the <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>  
  
 <span data-ttu-id="8fc1a-122">O exemplo a seguir mostra como fazer a viagem de ida e volta de um valor <xref:System.DateTimeOffset>.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-122">The following example illustrates how to round-trip a <xref:System.DateTimeOffset> value.</span></span>  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
 [!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]  
  
 <span data-ttu-id="8fc1a-123">Essa técnica sempre identifica sem ambiguidade um valor <xref:System.DateTimeOffset> como um único momento.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-123">This technique always unambiguously identifies a <xref:System.DateTimeOffset> value as a single point in time.</span></span> <span data-ttu-id="8fc1a-124">O valor pode ser convertido em UTC (Tempo Universal Coordenado) chamando o método <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> ou pode ser convertido em determinado fuso horário chamando o método <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> ou <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-124">The value can then be converted to Coordinated Universal Time (UTC) by calling the <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> method, or it can be converted to the time in a particular time zone by calling the <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> or <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="8fc1a-125">A principal limitação dessa técnica é que a aritmética de data e hora, quando executada em um valor <xref:System.DateTimeOffset> que representa o horário em determinado fuso horário, talvez não produza resultados precisos para esse fuso horário.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-125">The major limitation of this technique is that date and time arithmetic, when performed on a <xref:System.DateTimeOffset> value that represents the time in a particular time zone, may not produce accurate results for that time zone.</span></span> <span data-ttu-id="8fc1a-126">Isso ocorre porque, quando um valor <xref:System.DateTimeOffset> é instanciado, é dissociado do fuso horário.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-126">This is because when a <xref:System.DateTimeOffset> value is instantiated, it is disassociated from its time zone.</span></span> <span data-ttu-id="8fc1a-127">Portanto, as regras de ajuste do fuso horário não podem mais ser aplicadas quando você executa cálculos de data e hora.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-127">Therefore, that time zone's adjustment rules can no longer be applied when you perform date and time calculations.</span></span> <span data-ttu-id="8fc1a-128">É possível solucionar esse problema definindo um tipo personalizado que inclui um valor de data e hora e o respectivo fuso horário.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-128">You can work around this problem by defining a custom type that includes both a date and time value and its accompanying time zone.</span></span>  
  
### <a name="to-round-trip-a-date-and-time-value-with-its-time-zone"></a><span data-ttu-id="8fc1a-129">Para fazer a viagem de ida e volta de um valor de data e hora com seu fuso horário</span><span class="sxs-lookup"><span data-stu-id="8fc1a-129">To round-trip a date and time value with its time zone</span></span>  
  
1.  <span data-ttu-id="8fc1a-130">Defina uma classe ou uma estrutura com dois campos.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-130">Define a class or a structure with two fields.</span></span> <span data-ttu-id="8fc1a-131">O primeiro campo é um objeto <xref:System.DateTime> ou <xref:System.DateTimeOffset>, e o segundo é um objeto <xref:System.TimeZoneInfo>.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-131">The first field is either a <xref:System.DateTime> or a <xref:System.DateTimeOffset> object, and the second is a <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="8fc1a-132">O exemplo a seguir é uma versão simples desse tipo.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-132">The following example is a simple version of such a type.</span></span>  
  
     [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
     [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]  
  
2.  <span data-ttu-id="8fc1a-133">Marcar a classe com o atributo <xref:System.SerializableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-133">Mark the class with the <xref:System.SerializableAttribute> attribute.</span></span>  
  
3.  <span data-ttu-id="8fc1a-134">Serialize o objeto usando o método <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-134">Serialize the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> method.</span></span>  
  
4.  <span data-ttu-id="8fc1a-135">Restaure o objeto usando o método <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A>.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-135">Restore the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> method.</span></span>  
  
5.  <span data-ttu-id="8fc1a-136">Transmita (em C#) ou converta (em Visual Basic) o objeto desserializado em um objeto do tipo apropriado.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-136">Cast (in C#) or convert (in Visual Basic) the deserialized object to an object of the appropriate type.</span></span>  
  
 <span data-ttu-id="8fc1a-137">O exemplo a seguir ilustra como fazer a viagem de ida e volta de um objeto que armazena informações de data e hora e fuso horário.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-137">The following example illustrates how to round-trip an object that stores both date and time and time zone information.</span></span>  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
 [!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]  
  
 <span data-ttu-id="8fc1a-138">Essa técnica deve refletir sempre inequivocamente o ponto no tempo correto, antes e depois de ser salvo e restaurado, desde que a implementação do objeto combinado de data e hora e fuso horário não permita que o valor de data fique fora de sincronia com o valor de fuso horário.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-138">This technique should always unambiguously reflect the correct point of time both before and after it is saved and restored, provided that the implementation of the combined date and time and time zone object does not allow the date value to become out of sync with the time zone value.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8fc1a-139">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="8fc1a-139">Compiling the Code</span></span>  
 <span data-ttu-id="8fc1a-140">Esses exemplos precisam de:</span><span class="sxs-lookup"><span data-stu-id="8fc1a-140">These examples require:</span></span>  
  
-   <span data-ttu-id="8fc1a-141">Os seguintes namespaces sejam importados com instruções `using` em C# ou instruções `Imports` em Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="8fc1a-141">That the following namespaces be imported with C# `using` statements or Visual Basic `Imports` statements:</span></span>  
  
    -   <span data-ttu-id="8fc1a-142"><xref:System> (apenas para C#).</span><span class="sxs-lookup"><span data-stu-id="8fc1a-142"><xref:System> (C# only).</span></span>  
  
    -   <span data-ttu-id="8fc1a-143"><xref:System.Globalization?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-143"><xref:System.Globalization?displayProperty=nameWithType>.</span></span>  
  
    -   <span data-ttu-id="8fc1a-144"><xref:System.IO?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-144"><xref:System.IO?displayProperty=nameWithType>.</span></span>  
  
    -   <span data-ttu-id="8fc1a-145"><xref:System.Runtime.Serialization?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-145"><xref:System.Runtime.Serialization?displayProperty=nameWithType>.</span></span>  
  
    -   <span data-ttu-id="8fc1a-146"><xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-146"><xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="8fc1a-147">Uma referência a System.Core.dll.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-147">A reference to System.Core.dll.</span></span>  
  
-   <span data-ttu-id="8fc1a-148">Cada exemplo de código, exceto a classe `DateInTimeZone`, deve ser incluído em uma classe ou um módulo do Visual Basic, empacotado em métodos e chamado do método `Main`.</span><span class="sxs-lookup"><span data-stu-id="8fc1a-148">Each code example, other than the `DateInTimeZone` class, should be included in a class or Visual Basic module, wrapped in methods, and called from the `Main` method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fc1a-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8fc1a-149">See also</span></span>

- [<span data-ttu-id="8fc1a-150">Executando operações de formatação</span><span class="sxs-lookup"><span data-stu-id="8fc1a-150">Performing Formatting Operations</span></span>](../../../docs/standard/base-types/performing-formatting-operations.md)  
- [<span data-ttu-id="8fc1a-151">Escolhendo entre DateTime, DateTimeOffset, TimeSpan e TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="8fc1a-151">Choosing Between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo</span></span>](../../../docs/standard/datetime/choosing-between-datetime.md)  
- [<span data-ttu-id="8fc1a-152">Cadeias de caracteres de formato de data e hora padrão</span><span class="sxs-lookup"><span data-stu-id="8fc1a-152">Standard Date and Time Format Strings</span></span>](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
