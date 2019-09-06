---
title: Suporte a DateTime e DateTimeOffset em System.Text.Json
description: Uma visão geral de como os tipos DateTime e DateTimeOffset têm suporte na biblioteca System. Text. JSON.
ms.technology: dotnet-standard
author: layomia
ms.author: laakinri
ms.date: 07/22/2019
helpviewer_keywords:
- JSON, Serializer, Utf8
- JSON DateTime, JSON DateTimeOffset
- DateTime, DateTimeOffset
- JsonSerializer, Utf8JsonReader, Utf8JsonWriter, JsonElement, JsonDocument
- JSON Serializer, JSON Reader, JSON Writer
- Converter, JSON Converter, DateTime Converter
- ISO, ISO 8601, ISO 8601-1:2019
ms.openlocfilehash: 5bff01b10b2bdea4fdcfee86e348c47f44d50103
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2019
ms.locfileid: "70374471"
---
# <a name="datetime-and-datetimeoffset-support-in-systemtextjson"></a><span data-ttu-id="451e7-103">Suporte a DateTime e DateTimeOffset em System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="451e7-103">DateTime and DateTimeOffset support in System.Text.Json</span></span>

<span data-ttu-id="451e7-104">A biblioteca System. Text. JSON analisa e grava <xref:System.DateTime> e <xref:System.DateTimeOffset> valores de acordo com o perfil estendido ISO 8601:-2019.</span><span class="sxs-lookup"><span data-stu-id="451e7-104">The System.Text.Json library parses and writes <xref:System.DateTime> and <xref:System.DateTimeOffset> values according to the ISO 8601:-2019 extended profile.</span></span>
<span data-ttu-id="451e7-105">Os [conversores](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0) fornecem suporte personalizado para serialização e desserialização <xref:System.Text.Json.JsonSerializer>com o.</span><span class="sxs-lookup"><span data-stu-id="451e7-105">[Converters](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0) provide custom support for serializing and deserializing with <xref:System.Text.Json.JsonSerializer>.</span></span>

## <a name="support-for-the-iso-8601-12019-format"></a><span data-ttu-id="451e7-106">Suporte para o formato ISO 8601-1:2019</span><span class="sxs-lookup"><span data-stu-id="451e7-106">Support for the ISO 8601-1:2019 format</span></span>

<span data-ttu-id="451e7-107">Os <xref:System.Text.Json.JsonSerializer> <xref:System.Text.Json.Utf8JsonReader> <xref:System.DateTime> <xref:System.DateTimeOffset> tipos, ,<xref:System.Text.Json.Utf8JsonWriter>e analisam e gravam e representam representações de texto de acordo com o perfil estendido do formato ISO 8601-1:2019; por exemplo, 2019-07-26T16 <xref:System.Text.Json.JsonElement> : 59:57-05:00.</span><span class="sxs-lookup"><span data-stu-id="451e7-107">The <xref:System.Text.Json.JsonSerializer>, <xref:System.Text.Json.Utf8JsonReader>, <xref:System.Text.Json.Utf8JsonWriter>, and <xref:System.Text.Json.JsonElement> types parse and write <xref:System.DateTime> and <xref:System.DateTimeOffset> text representations according to the extended profile of the ISO 8601-1:2019 format; for example, 2019-07-26T16:59:57-05:00.</span></span>

<span data-ttu-id="451e7-108"><xref:System.DateTime>e <xref:System.DateTimeOffset> os dados podem ser serializados com <xref:System.Text.Json.JsonSerializer>:</span><span class="sxs-lookup"><span data-stu-id="451e7-108"><xref:System.DateTime> and <xref:System.DateTimeOffset> data can be serialized with <xref:System.Text.Json.JsonSerializer>:</span></span>

[!code-csharp[example-serializing-with-jsonserializer](~/samples/snippets/standard/datetime/json/serializing-with-jsonserializer.cs)]

<span data-ttu-id="451e7-109">Eles também podem ser desserializados com <xref:System.Text.Json.JsonSerializer>:</span><span class="sxs-lookup"><span data-stu-id="451e7-109">They can also be deserialized with <xref:System.Text.Json.JsonSerializer>:</span></span>

[!code-csharp[example-deserializing-with-jsonserializer-valid](~/samples/snippets/standard/datetime/json/deserializing-with-jsonserializer-valid.cs)]

<span data-ttu-id="451e7-110">Com opções padrão, as <xref:System.DateTime> representações de entrada e <xref:System.DateTimeOffset> de texto devem estar em conformidade com o perfil ISO 8601-1:2019 estendido.</span><span class="sxs-lookup"><span data-stu-id="451e7-110">With default options, input <xref:System.DateTime> and <xref:System.DateTimeOffset> text representations must conform to the extended ISO 8601-1:2019 profile.</span></span>
<span data-ttu-id="451e7-111">A tentativa de desserializar representações que não estão em conformidade com o perfil fará <xref:System.Text.Json.JsonSerializer> com que o <xref:System.Text.Json.JsonException>gere um:</span><span class="sxs-lookup"><span data-stu-id="451e7-111">Attempting to deserialize representations that don't conform to the profile will cause <xref:System.Text.Json.JsonSerializer> to throw a <xref:System.Text.Json.JsonException>:</span></span>

[!code-csharp[example-deserializing-with-jsonserializer-error](~/samples/snippets/standard/datetime/json/deserializing-with-jsonserializer-error.cs)]

<span data-ttu-id="451e7-112">O <xref:System.Text.Json.JsonDocument> fornece acesso estruturado ao conteúdo de uma carga JSON, incluindo <xref:System.DateTime> e <xref:System.DateTimeOffset> representações.</span><span class="sxs-lookup"><span data-stu-id="451e7-112">The <xref:System.Text.Json.JsonDocument> provides structured access to the contents of a JSON payload, including <xref:System.DateTime> and <xref:System.DateTimeOffset> representations.</span></span> <span data-ttu-id="451e7-113">O exemplo a seguir mostra como, quando é dada uma coleção de temperaturas, a temperatura média nas segundas-feiras pode ser calculada:</span><span class="sxs-lookup"><span data-stu-id="451e7-113">The example below shows how, when given a collection of temperatures, the average temperature on Mondays can be calculated:</span></span>

[!code-csharp[example-computing-with-jsondocument-valid](~/samples/snippets/standard/datetime/json/computing-with-jsondocument-valid.cs)]

<span data-ttu-id="451e7-114">A tentativa de calcular a temperatura média devido a uma carga com representações <xref:System.DateTime> sem conformidade causará <xref:System.Text.Json.JsonDocument> a geração de <xref:System.FormatException>:</span><span class="sxs-lookup"><span data-stu-id="451e7-114">Attempting to compute the average temperature given a payload with non-compliant <xref:System.DateTime> representations will cause <xref:System.Text.Json.JsonDocument> to throw a <xref:System.FormatException>:</span></span>

[!code-csharp[example-computing-with-jsondocument-error](~/samples/snippets/standard/datetime/json/computing-with-jsondocument-error.cs)]

<span data-ttu-id="451e7-115">As gravações <xref:System.Text.Json.Utf8JsonWriter> <xref:System.DateTime> e osdadosdenívelinferior:<xref:System.DateTimeOffset></span><span class="sxs-lookup"><span data-stu-id="451e7-115">The lower level <xref:System.Text.Json.Utf8JsonWriter> writes <xref:System.DateTime> and <xref:System.DateTimeOffset> data:</span></span>

[!code-csharp[example-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/writing-with-utf8jsonwriter.cs)]

<span data-ttu-id="451e7-116"><xref:System.Text.Json.Utf8JsonReader><xref:System.DateTime> análises e<xref:System.DateTimeOffset> dados:</span><span class="sxs-lookup"><span data-stu-id="451e7-116"><xref:System.Text.Json.Utf8JsonReader> parses <xref:System.DateTime> and <xref:System.DateTimeOffset> data:</span></span>

[!code-csharp[example-reading-with-utf8jsonreader-valid](~/samples/snippets/standard/datetime/json/reading-with-utf8jsonreader-valid.cs)]

<span data-ttu-id="451e7-117">A tentativa de ler formatos sem conformidade com <xref:System.Text.Json.Utf8JsonReader> o fará com que ele gere um: <xref:System.FormatException></span><span class="sxs-lookup"><span data-stu-id="451e7-117">Attempting to read non-compliant formats with <xref:System.Text.Json.Utf8JsonReader> will cause it to throw a <xref:System.FormatException>:</span></span>

[!code-csharp[example-reading-with-utf8jsonreader-error](~/samples/snippets/standard/datetime/json/reading-with-utf8jsonreader-error.cs)]

## <a name="custom-support-for-xrefsystemdatetime-and-xrefsystemdatetimeoffset-in-xrefsystemtextjsonjsonserializer"></a><span data-ttu-id="451e7-118">Suporte personalizado para <xref:System.DateTime> e <xref:System.DateTimeOffset> em<xref:System.Text.Json.JsonSerializer></span><span class="sxs-lookup"><span data-stu-id="451e7-118">Custom support for <xref:System.DateTime> and <xref:System.DateTimeOffset> in <xref:System.Text.Json.JsonSerializer></span></span>

<span data-ttu-id="451e7-119">Se você quiser que o serializador execute a análise ou a formatação personalizada, poderá implementar [conversores personalizados](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0).</span><span class="sxs-lookup"><span data-stu-id="451e7-119">If you want the serializer to perform custom parsing or formatting, you can implement [custom converters](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0).</span></span>
<span data-ttu-id="451e7-120">Veja aqui alguns exemplos:</span><span class="sxs-lookup"><span data-stu-id="451e7-120">Here are a few examples:</span></span>

### <a name="using-datetimeoffsetparse-and-datetimeoffsettostring"></a><span data-ttu-id="451e7-121">Usando `DateTime(Offset).Parse` o e o`DateTime(Offset).ToString`</span><span class="sxs-lookup"><span data-stu-id="451e7-121">Using `DateTime(Offset).Parse` and `DateTime(Offset).ToString`</span></span>

<span data-ttu-id="451e7-122">Se você não puder determinar os formatos de suas <xref:System.DateTime> representações de entrada ou <xref:System.DateTimeOffset> de texto, poderá usar `DateTime(Offset).Parse` o método em sua lógica de leitura do conversor.</span><span class="sxs-lookup"><span data-stu-id="451e7-122">If you can't determine the formats of your input <xref:System.DateTime> or <xref:System.DateTimeOffset> text representations, you can use the `DateTime(Offset).Parse` method in your converter read logic.</span></span> <span data-ttu-id="451e7-123">Isso permite que você use o. O amplo suporte da net para análise de <xref:System.DateTime> vários <xref:System.DateTimeOffset> formatos de texto e, incluindo cadeias de caracteres não ISO 8601 e formatos ISO 8601 que não estão em conformidade com o perfil ISO 8601-1:2019 estendido.</span><span class="sxs-lookup"><span data-stu-id="451e7-123">This allows you to use .NET's extensive support for parsing various <xref:System.DateTime> and <xref:System.DateTimeOffset> text formats, including non-ISO 8601 strings and ISO 8601 formats that don't conform to the extended ISO 8601-1:2019 profile.</span></span> <span data-ttu-id="451e7-124">Essa abordagem é significativamente menos eficaz do que usar a implementação nativa do serializador.</span><span class="sxs-lookup"><span data-stu-id="451e7-124">This approach is significantly less performant than using the serializer's native implementation.</span></span>

<span data-ttu-id="451e7-125">Para serialização, você pode usar o `DateTime(Offset).ToString` método em sua lógica de gravação do conversor.</span><span class="sxs-lookup"><span data-stu-id="451e7-125">For serializing, you can use the `DateTime(Offset).ToString` method in your converter write logic.</span></span> <span data-ttu-id="451e7-126">Isso permite que você escreva <xref:System.DateTime> e <xref:System.DateTimeOffset> valores usando qualquer um dos [formatos de data e hora padrão](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings)e os [formatos de data e hora personalizados](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings).</span><span class="sxs-lookup"><span data-stu-id="451e7-126">This allows you to write <xref:System.DateTime> and <xref:System.DateTimeOffset> values using any of the [standard date and time formats](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings), and the [custom date and time formats](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings).</span></span>
<span data-ttu-id="451e7-127">Isso também é significativamente menos eficaz do que usar a implementação nativa do serializador.</span><span class="sxs-lookup"><span data-stu-id="451e7-127">This is also significantly less performant than using the serializer's native implementation.</span></span>

[!code-csharp[example-showing-datetime-parse](~/samples/snippets/standard/datetime/json/datetime-converter-examples/example1/Program.cs)]

> [!NOTE]
> <span data-ttu-id="451e7-128">Ao implementar <xref:System.Text.Json.Serialization.JsonConverter%601>, e `T` é <xref:System.DateTime>, o `typeToConvert` parâmetro sempre `typeof(DateTime)`será.</span><span class="sxs-lookup"><span data-stu-id="451e7-128">When implementing <xref:System.Text.Json.Serialization.JsonConverter%601>, and `T` is <xref:System.DateTime>, the `typeToConvert` parameter will always be `typeof(DateTime)`.</span></span>
<span data-ttu-id="451e7-129">O parâmetro é útil para lidar com casos polimórficos e ao usar genéricos para obter `typeof(T)` uma maneira de desempenho.</span><span class="sxs-lookup"><span data-stu-id="451e7-129">The parameter is useful for handling polymorphic cases and when using generics to get `typeof(T)` in a performant way.</span></span>

### <a name="using-xrefsystembufferstextutf8parser-and-xrefsystembufferstextutf8formatter"></a><span data-ttu-id="451e7-130">Usando <xref:System.Buffers.Text.Utf8Parser> o e o<xref:System.Buffers.Text.Utf8Formatter></span><span class="sxs-lookup"><span data-stu-id="451e7-130">Using <xref:System.Buffers.Text.Utf8Parser> and <xref:System.Buffers.Text.Utf8Formatter></span></span>

<span data-ttu-id="451e7-131">Você pode usar os métodos de análise e formatação baseados em UTF-8 rápidos na lógica do conversor se suas <xref:System.DateTime> representações de entrada ou <xref:System.DateTimeOffset> de texto estiverem em conformidade com uma das [cadeias de caracteres de formato de data e hora padrão](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings)"R", "l", "O" ou "G", ou se você quiser Escreva de acordo com um desses formatos.</span><span class="sxs-lookup"><span data-stu-id="451e7-131">You can use fast UTF-8-based parsing and formatting methods in your converter logic if your input <xref:System.DateTime> or <xref:System.DateTimeOffset> text representations are compliant with one of the "R", "l", "O", or "G" [standard date and time format Strings](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings), or you want to write according to one of these formats.</span></span> <span data-ttu-id="451e7-132">Isso é muito mais rápido do `DateTime(Offset).Parse` que `DateTime(Offset).ToString`usar o e o.</span><span class="sxs-lookup"><span data-stu-id="451e7-132">This is much faster than using `DateTime(Offset).Parse` and `DateTime(Offset).ToString`.</span></span>

<span data-ttu-id="451e7-133">Este exemplo mostra um conversor personalizado que serializa e <xref:System.DateTime> desserializa valores de acordo com [o formato padrão "R"](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-rfc1123-r-r-format-specifier):</span><span class="sxs-lookup"><span data-stu-id="451e7-133">This example shows a custom converter that serializes and deserializes <xref:System.DateTime> values according to [the "R" standard format](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-rfc1123-r-r-format-specifier):</span></span>

[!code-csharp[example-showing-utf8-parser-and-formatter](~/samples/snippets/standard/datetime/json/datetime-converter-examples/example2/Program.cs)]

> [!NOTE]
> <span data-ttu-id="451e7-134">O formato padrão "R" terá sempre 29 caracteres.</span><span class="sxs-lookup"><span data-stu-id="451e7-134">The "R" standard format will always be 29 characters long.</span></span>

### <a name="using-datetimeoffsetparse-as-a-fallback-to-the-serializers-native-parsing"></a><span data-ttu-id="451e7-135">Usando `DateTime(Offset).Parse` como um fallback para a análise nativa do serializador</span><span class="sxs-lookup"><span data-stu-id="451e7-135">Using `DateTime(Offset).Parse` as a fallback to the serializer's native parsing</span></span>

<span data-ttu-id="451e7-136">Se, em geral, você <xref:System.DateTime> esperar <xref:System.DateTimeOffset> que sua entrada ou seus dados estejam de acordo com o perfil ISO 8601-1:2019 estendido, poderá usar a lógica de análise nativa do serializador.</span><span class="sxs-lookup"><span data-stu-id="451e7-136">If you generally expect your input <xref:System.DateTime> or <xref:System.DateTimeOffset> data to conform to the extended ISO 8601-1:2019 profile, you can use the serializer's native parsing logic.</span></span> <span data-ttu-id="451e7-137">Você também pode implementar um mecanismo de fallback apenas no caso.</span><span class="sxs-lookup"><span data-stu-id="451e7-137">You can also implement a fallback mechanism just in case.</span></span>
<span data-ttu-id="451e7-138">Este exemplo mostra que, após a falha de análise <xref:System.DateTime> de uma representação <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)>de texto usando, o conversor analisa os dados com <xref:System.DateTime.Parse(System.String)>êxito usando.</span><span class="sxs-lookup"><span data-stu-id="451e7-138">This example shows that, after failing to parse a <xref:System.DateTime> text representation using <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)>, the converter successfully parses the data using <xref:System.DateTime.Parse(System.String)>.</span></span>

[!code-csharp[example-showing-datetime-parse-as-fallback](~/samples/snippets/standard/datetime/json/datetime-converter-examples/example3/Program.cs)]

## <a name="the-extended-iso-8601-12019-profile-in-systemtextjson"></a><span data-ttu-id="451e7-139">O perfil ISO 8601-1:2019 estendido em System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="451e7-139">The extended ISO 8601-1:2019 profile in System.Text.Json</span></span>

### <a name="date-and-time-components"></a><span data-ttu-id="451e7-140">Componentes de data e hora</span><span class="sxs-lookup"><span data-stu-id="451e7-140">Date and time components</span></span>

<span data-ttu-id="451e7-141">O perfil ISO 8601-1:2019 estendido implementado <xref:System.Text.Json> em define os seguintes componentes para representações de data e hora.</span><span class="sxs-lookup"><span data-stu-id="451e7-141">The extended ISO 8601-1:2019 profile implemented in <xref:System.Text.Json> defines the following components for date and time representations.</span></span> <span data-ttu-id="451e7-142">Esses componentes são usados para definir vários níveis de granularidade com suporte durante a análise e a <xref:System.DateTime> formatação <xref:System.DateTimeOffset> e as representações.</span><span class="sxs-lookup"><span data-stu-id="451e7-142">These components are used to define various levels of granularity supported when parsing and formatting <xref:System.DateTime> and <xref:System.DateTimeOffset> representations.</span></span>

| <span data-ttu-id="451e7-143">Componente</span><span class="sxs-lookup"><span data-stu-id="451e7-143">Component</span></span>       | <span data-ttu-id="451e7-144">Formatar</span><span class="sxs-lookup"><span data-stu-id="451e7-144">Format</span></span>                      | <span data-ttu-id="451e7-145">Descrição</span><span class="sxs-lookup"><span data-stu-id="451e7-145">Description</span></span>                                                                     |
|-----------------|-----------------------------|---------------------------------------------------------------------------------|
| <span data-ttu-id="451e7-146">Year</span><span class="sxs-lookup"><span data-stu-id="451e7-146">Year</span></span>            | <span data-ttu-id="451e7-147">"yyyy"</span><span class="sxs-lookup"><span data-stu-id="451e7-147">"yyyy"</span></span>                      | <span data-ttu-id="451e7-148">0001-9999</span><span class="sxs-lookup"><span data-stu-id="451e7-148">0001-9999</span></span>                                                                       |
| <span data-ttu-id="451e7-149">Month</span><span class="sxs-lookup"><span data-stu-id="451e7-149">Month</span></span>           | <span data-ttu-id="451e7-150">"MM"</span><span class="sxs-lookup"><span data-stu-id="451e7-150">"MM"</span></span>                        | <span data-ttu-id="451e7-151">01-12</span><span class="sxs-lookup"><span data-stu-id="451e7-151">01-12</span></span>                                                                           |
| <span data-ttu-id="451e7-152">Day</span><span class="sxs-lookup"><span data-stu-id="451e7-152">Day</span></span>             | <span data-ttu-id="451e7-153">"dd"</span><span class="sxs-lookup"><span data-stu-id="451e7-153">"dd"</span></span>                        | <span data-ttu-id="451e7-154">01-28, 01-29, 01-30, 01-31 com base no mês/ano</span><span class="sxs-lookup"><span data-stu-id="451e7-154">01-28, 01-29, 01-30, 01-31 based on month/year</span></span>                                  |
| <span data-ttu-id="451e7-155">Hora</span><span class="sxs-lookup"><span data-stu-id="451e7-155">Hour</span></span>            | <span data-ttu-id="451e7-156">"HH"</span><span class="sxs-lookup"><span data-stu-id="451e7-156">"HH"</span></span>                        | <span data-ttu-id="451e7-157">00-23</span><span class="sxs-lookup"><span data-stu-id="451e7-157">00-23</span></span>                                                                           |
| <span data-ttu-id="451e7-158">Minuto</span><span class="sxs-lookup"><span data-stu-id="451e7-158">Minute</span></span>          | <span data-ttu-id="451e7-159">"mm"</span><span class="sxs-lookup"><span data-stu-id="451e7-159">"mm"</span></span>                        | <span data-ttu-id="451e7-160">00-59</span><span class="sxs-lookup"><span data-stu-id="451e7-160">00-59</span></span>                                                                           |
| <span data-ttu-id="451e7-161">Segundo</span><span class="sxs-lookup"><span data-stu-id="451e7-161">Second</span></span>          | <span data-ttu-id="451e7-162">"ss"</span><span class="sxs-lookup"><span data-stu-id="451e7-162">"ss"</span></span>                        | <span data-ttu-id="451e7-163">00-59</span><span class="sxs-lookup"><span data-stu-id="451e7-163">00-59</span></span>                                                                           |
| <span data-ttu-id="451e7-164">Segunda fração</span><span class="sxs-lookup"><span data-stu-id="451e7-164">Second fraction</span></span> | <span data-ttu-id="451e7-165">"FFFFFFF"</span><span class="sxs-lookup"><span data-stu-id="451e7-165">"FFFFFFF"</span></span>                   | <span data-ttu-id="451e7-166">Mínimo de um dígito, no máximo 16 dígitos</span><span class="sxs-lookup"><span data-stu-id="451e7-166">Minimum of one digit, maximum of 16 digits</span></span>                                      |
| <span data-ttu-id="451e7-167">Diferença de tempo</span><span class="sxs-lookup"><span data-stu-id="451e7-167">Time offset</span></span>     | <span data-ttu-id="451e7-168">"K"</span><span class="sxs-lookup"><span data-stu-id="451e7-168">"K"</span></span>                         | <span data-ttu-id="451e7-169">"Z" ou "(' + '/'-') HH ': ' mm '</span><span class="sxs-lookup"><span data-stu-id="451e7-169">Either "Z" or "('+'/'-')HH':'mm"</span></span>                                                |
| <span data-ttu-id="451e7-170">Hora parcial</span><span class="sxs-lookup"><span data-stu-id="451e7-170">Partial time</span></span>    | <span data-ttu-id="451e7-171">"HH": "mm": "SS [FFFFFFF]"</span><span class="sxs-lookup"><span data-stu-id="451e7-171">"HH':'mm':'ss[FFFFFFF]"</span></span>     | <span data-ttu-id="451e7-172">Tempo sem informações de deslocamento UTC</span><span class="sxs-lookup"><span data-stu-id="451e7-172">Time without UTC offset information</span></span>                                             |
| <span data-ttu-id="451e7-173">Data completa</span><span class="sxs-lookup"><span data-stu-id="451e7-173">Full date</span></span>       | <span data-ttu-id="451e7-174">"yyyy'-'MM'-'dd"</span><span class="sxs-lookup"><span data-stu-id="451e7-174">"yyyy'-'MM'-'dd"</span></span>            | <span data-ttu-id="451e7-175">Data do calendário</span><span class="sxs-lookup"><span data-stu-id="451e7-175">Calendar date</span></span>                                                                   |
| <span data-ttu-id="451e7-176">Tempo total</span><span class="sxs-lookup"><span data-stu-id="451e7-176">Full time</span></span>       | <span data-ttu-id="451e7-177">"Time'K parcial"</span><span class="sxs-lookup"><span data-stu-id="451e7-177">"'Partial time'K"</span></span>           | <span data-ttu-id="451e7-178">UTC do dia ou hora local do dia com o deslocamento de tempo entre a hora local e o UTC</span><span class="sxs-lookup"><span data-stu-id="451e7-178">UTC of day or Local time of day with the time offset between local time and UTC</span></span> |
| <span data-ttu-id="451e7-179">Data e hora</span><span class="sxs-lookup"><span data-stu-id="451e7-179">Date time</span></span>       | <span data-ttu-id="451e7-180">"Hora completa ' ' T' ' '</span><span class="sxs-lookup"><span data-stu-id="451e7-180">"'Full date''T''Full time'"</span></span> | <span data-ttu-id="451e7-181">Data do calendário e hora do dia, por exemplo, 2019-07-26T16:59:57-05:00</span><span class="sxs-lookup"><span data-stu-id="451e7-181">Calendar date and time of day, e.g. 2019-07-26T16:59:57-05:00</span></span>                   |

### <a name="support-for-parsing"></a><span data-ttu-id="451e7-182">Suporte para análise</span><span class="sxs-lookup"><span data-stu-id="451e7-182">Support for parsing</span></span>

<span data-ttu-id="451e7-183">Os seguintes níveis de granularidade são definidos para análise:</span><span class="sxs-lookup"><span data-stu-id="451e7-183">The following levels of granularity are defined for parsing:</span></span>

1. <span data-ttu-id="451e7-184">' Data completa '</span><span class="sxs-lookup"><span data-stu-id="451e7-184">'Full date'</span></span>
    1. <span data-ttu-id="451e7-185">"yyyy'-'MM'-'dd"</span><span class="sxs-lookup"><span data-stu-id="451e7-185">"yyyy'-'MM'-'dd"</span></span>

2. <span data-ttu-id="451e7-186">"Data completa ' T' ' ' hora ' ': ' ' minuto '"</span><span class="sxs-lookup"><span data-stu-id="451e7-186">"'Full date''T''Hour'':''Minute'"</span></span>
    1. <span data-ttu-id="451e7-187">"yyyy'-'MM'-'dd'T'HH ': ' mm"</span><span class="sxs-lookup"><span data-stu-id="451e7-187">"yyyy'-'MM'-'dd'T'HH':'mm"</span></span>

3. <span data-ttu-id="451e7-188">"A data completa ' T' ' ' t ' ' hora parcial '"</span><span class="sxs-lookup"><span data-stu-id="451e7-188">"'Full date''T''Partial time'"</span></span>
    1. <span data-ttu-id="451e7-189">"yyyy'-'MM'-'dd'T'HH": "mm": "SS" ([o especificador de formato classificável ("s")](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))</span><span class="sxs-lookup"><span data-stu-id="451e7-189">"yyyy'-'MM'-'dd'T'HH':'mm':'ss" ([The Sortable ("s") Format Specifier](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))</span></span>
    2. <span data-ttu-id="451e7-190">"yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' FFFFFFF</span><span class="sxs-lookup"><span data-stu-id="451e7-190">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF"</span></span>

4. <span data-ttu-id="451e7-191">"" Data completa "' T' ' hora ' ': ' ' minuto ' ' deslocamento de tempo '"</span><span class="sxs-lookup"><span data-stu-id="451e7-191">"'Full date''T''Time hour'':''Minute''Time offset'"</span></span>
    1. <span data-ttu-id="451e7-192">"yyyy'-'MM'-'dd'T'HH':'mmZ"</span><span class="sxs-lookup"><span data-stu-id="451e7-192">"yyyy'-'MM'-'dd'T'HH':'mmZ"</span></span>
    2. <span data-ttu-id="451e7-193">"yyyy'-'MM'-'dd'T'HH ': ' mm (' + '/'-') HH ': ' mm '</span><span class="sxs-lookup"><span data-stu-id="451e7-193">"yyyy'-'MM'-'dd'T'HH':'mm('+'/'-')HH':'mm"</span></span>

5. <span data-ttu-id="451e7-194">' Data e hora '</span><span class="sxs-lookup"><span data-stu-id="451e7-194">'Date time'</span></span>
    1. <span data-ttu-id="451e7-195">"yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ssZ '</span><span class="sxs-lookup"><span data-stu-id="451e7-195">"yyyy'-'MM'-'dd'T'HH':'mm':'ssZ"</span></span>
    2. <span data-ttu-id="451e7-196">"yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' FFFFFFFZ"</span><span class="sxs-lookup"><span data-stu-id="451e7-196">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFFZ"</span></span>
    3. <span data-ttu-id="451e7-197">"yyyy'-'MM'-'dd'T'HH ': ' mm ': ' SS (' + '/'-') HH ': ' mm '</span><span class="sxs-lookup"><span data-stu-id="451e7-197">"yyyy'-'MM'-'dd'T'HH':'mm':'ss('+'/'-')HH':'mm"</span></span>
    4. <span data-ttu-id="451e7-198">"yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' FFFFFFF (' + '/'-') HH ': ' mm '</span><span class="sxs-lookup"><span data-stu-id="451e7-198">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF('+'/'-')HH':'mm"</span></span>

<span data-ttu-id="451e7-199">Se houver frações decimais para segundos, deve haver pelo menos um dígito; `2019-07-26T00:00:00.` não é permitido.</span><span class="sxs-lookup"><span data-stu-id="451e7-199">If there are decimal fractions for seconds, there must be at least one digit; `2019-07-26T00:00:00.` is not allowed.</span></span>
<span data-ttu-id="451e7-200">Embora sejam permitidos até 16 dígitos fracionários, somente os primeiros sete são analisados.</span><span class="sxs-lookup"><span data-stu-id="451e7-200">While up to 16 fractional digits are allowed, only the first seven are parsed.</span></span> <span data-ttu-id="451e7-201">Qualquer coisa além disso é considerada um zero.</span><span class="sxs-lookup"><span data-stu-id="451e7-201">Anything beyond that is considered a zero.</span></span>
<span data-ttu-id="451e7-202">Por exemplo, `2019-07-26T00:00:00.1234567890` será analisado como se `2019-07-26T00:00:00.1234567`fosse.</span><span class="sxs-lookup"><span data-stu-id="451e7-202">For example, `2019-07-26T00:00:00.1234567890` will be parsed as if it is `2019-07-26T00:00:00.1234567`.</span></span>
<span data-ttu-id="451e7-203">Isso é para se manter compatível com <xref:System.DateTime> a implementação, que está limitada a essa resolução.</span><span class="sxs-lookup"><span data-stu-id="451e7-203">This is to stay compatible with the <xref:System.DateTime> implementation, which is limited to this resolution.</span></span>

<span data-ttu-id="451e7-204">Não há suporte para segundos bissextos.</span><span class="sxs-lookup"><span data-stu-id="451e7-204">Leap seconds are not supported.</span></span>

### <a name="support-for-formatting"></a><span data-ttu-id="451e7-205">Suporte para formatação</span><span class="sxs-lookup"><span data-stu-id="451e7-205">Support for formatting</span></span>

<span data-ttu-id="451e7-206">Os seguintes níveis de granularidade são definidos para formatação:</span><span class="sxs-lookup"><span data-stu-id="451e7-206">The following levels of granularity are defined for formatting:</span></span>

1. <span data-ttu-id="451e7-207">"A data completa ' T' ' ' t ' ' hora parcial '"</span><span class="sxs-lookup"><span data-stu-id="451e7-207">"'Full date''T''Partial time'"</span></span>
    1. <span data-ttu-id="451e7-208">"yyyy'-'MM'-'dd'T'HH": "mm": "SS" ([o especificador de formato classificável ("s")](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))</span><span class="sxs-lookup"><span data-stu-id="451e7-208">"yyyy'-'MM'-'dd'T'HH':'mm':'ss"  ([The Sortable ("s") Format Specifier](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))</span></span>

        <span data-ttu-id="451e7-209">Usado para formatar um <xref:System.DateTime> sem segundos fracionários e sem informações de deslocamento.</span><span class="sxs-lookup"><span data-stu-id="451e7-209">Used to format a <xref:System.DateTime> without fractional seconds and without offset information.</span></span>

    2. <span data-ttu-id="451e7-210">"yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' FFFFFFF</span><span class="sxs-lookup"><span data-stu-id="451e7-210">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF"</span></span>

        <span data-ttu-id="451e7-211">Usado para formatar um <xref:System.DateTime> com segundos fracionários, mas sem informações de deslocamento.</span><span class="sxs-lookup"><span data-stu-id="451e7-211">Used to format a <xref:System.DateTime> with fractional seconds but without offset information.</span></span>

2. <span data-ttu-id="451e7-212">' Data e hora '</span><span class="sxs-lookup"><span data-stu-id="451e7-212">'Date time'</span></span>
    1. <span data-ttu-id="451e7-213">"yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ssZ '</span><span class="sxs-lookup"><span data-stu-id="451e7-213">"yyyy'-'MM'-'dd'T'HH':'mm':'ssZ"</span></span>

        <span data-ttu-id="451e7-214">Usado para formatar um <xref:System.DateTime> ou <xref:System.DateTimeOffset> sem segundos fracionários, mas com um deslocamento UTC.</span><span class="sxs-lookup"><span data-stu-id="451e7-214">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> without fractional seconds but with a UTC offset.</span></span>

    2. <span data-ttu-id="451e7-215">"yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' FFFFFFFZ"</span><span class="sxs-lookup"><span data-stu-id="451e7-215">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFFZ"</span></span>

        <span data-ttu-id="451e7-216">Usado para formatar um <xref:System.DateTime> ou <xref:System.DateTimeOffset> com segundos fracionários e com um deslocamento UTC.</span><span class="sxs-lookup"><span data-stu-id="451e7-216">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> with fractional seconds and with a UTC offset.</span></span>

    3. <span data-ttu-id="451e7-217">"yyyy'-'MM'-'dd'T'HH ': ' mm ': ' SS (' + '/'-') HH ': ' mm '</span><span class="sxs-lookup"><span data-stu-id="451e7-217">"yyyy'-'MM'-'dd'T'HH':'mm':'ss('+'/'-')HH':'mm"</span></span>

        <span data-ttu-id="451e7-218">Usado para formatar um <xref:System.DateTime> ou <xref:System.DateTimeOffset> sem segundos fracionários, mas com um deslocamento local.</span><span class="sxs-lookup"><span data-stu-id="451e7-218">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> without fractional seconds but with a local offset.</span></span>

    4. <span data-ttu-id="451e7-219">"yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' FFFFFFF (' + '/'-') HH ': ' mm '</span><span class="sxs-lookup"><span data-stu-id="451e7-219">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF('+'/'-')HH':'mm"</span></span>

        <span data-ttu-id="451e7-220">Usado para formatar um <xref:System.DateTime> ou <xref:System.DateTimeOffset> com segundos fracionários e com um deslocamento local.</span><span class="sxs-lookup"><span data-stu-id="451e7-220">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> with fractional seconds and with a local offset.</span></span>
