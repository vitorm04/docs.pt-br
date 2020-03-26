---
title: Migrar Newtonsoft.Json de System.Text.Json - .NET
author: tdykstra
ms.author: tdykstra
no-loc:
- System.Text.Json
- Newtonsoft.Json
ms.date: 01/10/2020
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 957bafcdf69d5792702962db6598458a0c8ec974
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291571"
---
# <a name="how-to-migrate-from-newtonsoftjson-to-systemtextjson"></a>Como migrar de Newtonsoft.Json para System.Text.Json

Este artigo mostra como migrar de [Newtonsoft.Json](https://www.newtonsoft.com/json) para <xref:System.Text.Json>.

O `System.Text.Json` namespace fornece funcionalidade para serializar e desserializar a partir de JavaScript Object Notation (JSON). A `System.Text.Json` biblioteca está incluída no quadro compartilhado [.NET Core 3.0.](https://aka.ms/netcore3download) Para outras frameworks de destino, instale o pacote [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet. O pacote suporta:

* .NET Standard 2.0 e versões posteriores
* .NET Framework 4.7.2 e versões posteriores
* .NET Core 2.0, 2.1 e 2.2

`System.Text.Json`foca principalmente no desempenho, segurança e conformidade com os padrões. Ele tem algumas diferenças importantes no comportamento padrão e não `Newtonsoft.Json`visa ter paridade de recursos com . Para alguns `System.Text.Json` cenários, não tem funcionalidade incorporada, mas existem soluçãorecomendada. Para outros cenários, as soluções são impraticáveis. Se sua aplicação depender de um recurso ausente, considere [arquivar um problema](https://github.com/dotnet/runtime/issues/new) para descobrir se o suporte ao seu cenário pode ser adicionado.

<!-- For information about which features might be added in future releases, see the [Roadmap](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md). [Restore this when the roadmap is updated.]-->

A maior parte deste artigo <xref:System.Text.Json.JsonSerializer> é sobre como usar a API, <xref:System.Text.Json.JsonDocument> mas também inclui orientações sobre como <xref:System.Text.Json.Utf8JsonReader>usar <xref:System.Text.Json.Utf8JsonWriter> o (que representa o Modelo de Objeto de Documento ou DOM), e tipos.

## <a name="table-of-differences-between-newtonsoftjson-and-systemtextjson"></a>Tabela de diferenças entre Newtonsoft.Json e System.Text.Json

A tabela `Newtonsoft.Json` a `System.Text.Json` seguir lista características e equivalentes. Os equivalentes se enquadram nas seguintes categorias:

* Suportado pela funcionalidade incorporada. Obter comportamento `System.Text.Json` semelhante pode exigir o uso de um atributo ou opção global.
* Não suportado, a solução é possível. As soluçãos são [conversores personalizados,](system-text-json-converters-how-to.md)que `Newtonsoft.Json` podem não fornecer paridade completa com funcionalidade. Para alguns destes, o código de amostra é fornecido como exemplos. Se você confiar `Newtonsoft.Json` nesses recursos, a migração exigirá modificações em seus modelos de objeto .NET ou outras alterações de código.
* Não suportado, a solução não é prática ou possível. Se você confiar `Newtonsoft.Json` nesses recursos, a migração não será possível sem mudanças significativas.

| Newtonsoft.Json                               | System.Text.Json equivalente |
|-------------------------------------------------------|-----------------------------|
| Desserialização insensível a casos por padrão           | ✔️ [configuração global PropertyNameInsensitive](#case-insensitive-deserialization) |
| Nomes de propriedade de camelos                             | ✔️ [configuração global PropertyNamingPolicy](system-text-json-how-to.md#use-camel-case-for-all-json-property-names) |
| Personagem mínimo escapando                            | ✔️ [caráter rigoroso escapando, configurável](#minimal-character-escaping) |
| `NullValueHandling.Ignore`configuração global             | ✔️ [ignorarnullValues opção global](system-text-json-how-to.md#exclude-all-null-value-properties) |
| Permitir comentários                                        | ✔️ [configuração global ReadCommentHandling](#comments) |
| Permitir commas de arrasto                                 | ✔️ [allowTrailingCommas configuração global](#trailing-commas) |
| Registro de conversor personalizado                         | ✔️ [Ordem de precedência difere](#converter-registration-precedence) |
| Sem profundidade máxima por padrão                           | ✔️ [profundidade máxima padrão 64, configurável](#maximum-depth) |
| Suporte para uma ampla gama de tipos                    | ⚠️[Alguns tipos exigem conversores personalizados](#types-without-built-in-support) |
| Desserializar strings como números                        | ⚠️[Não suportado, solução, amostra](#quoted-numbers) |
| Desserializar `Dictionary` com tecla não-string          | ⚠️[Não suportado, solução, amostra](#dictionary-with-non-string-key) |
| Serialização polimórfica                             | ⚠️[Não suportado, solução, amostra](#polymorphic-serialization) |
| Desserialização polimórfica                           | ⚠️[Não suportado, solução, amostra](#polymorphic-deserialization) |
| Desserializar o `object` tipo inferido para propriedades      | ⚠️[Não suportado, solução, amostra](#deserialization-of-object-properties) |
| Desserializar JSON `null` literal para tipos de valor não anulados | ⚠️[Não suportado, solução, amostra](#deserialize-null-to-non-nullable-type) |
| Desserializar para classes imutáveis e estruturas          | ⚠️[Não suportado, solução, amostra](#deserialize-to-immutable-classes-and-structs) |
| Atributo `[JsonConstructor]`                         | ⚠️[Não suportado, solução, amostra](#specify-constructor-to-use) |
| `Required`configuração `[JsonProperty]` no atributo        | ⚠️[Não suportado, solução, amostra](#required-properties) |
| `NullValueHandling`configuração `[JsonProperty]` no atributo | ⚠️[Não suportado, solução, amostra](#conditionally-ignore-a-property)  |
| `DefaultValueHandling`configuração `[JsonProperty]` no atributo | ⚠️[Não suportado, solução, amostra](#conditionally-ignore-a-property)  |
| `DefaultValueHandling`configuração global                 | ⚠️[Não suportado, solução, amostra](#conditionally-ignore-a-property) |
| `DefaultContractResolver`para excluir propriedades       | ⚠️[Não suportado, solução, amostra](#conditionally-ignore-a-property) |
| `DateTimeZoneHandling`, `DateFormatString` configurações   | ⚠️[Não suportado, solução, amostra](#specify-date-format) |
| Retornos de chamada                                             | ⚠️[Não suportado, solução, amostra](#callbacks) |
| Apoio a áreas públicas e não públicas              | ⚠️[Não suportado, solução](#public-and-non-public-fields) |
| Suporte para setters e getters de propriedades internas e privadas | ⚠️[Não suportado, solução](#internal-and-private-property-setters-and-getters) |
| Método `JsonConvert.PopulateObject`                   | ⚠️[Não suportado, solução](#populate-existing-objects) |
| `ObjectCreationHandling`configuração global               | ⚠️[Não suportado, solução](#reuse-rather-than-replace-properties) |
| Adicionar às coleções sem setters                    | ⚠️[Não suportado, solução](#add-to-collections-without-setters) |
| `PreserveReferencesHandling`configuração global           | ❌[Não suportado](#preserve-object-references-and-handle-loops) |
| `ReferenceLoopHandling`configuração global                | ❌[Não suportado](#preserve-object-references-and-handle-loops) |
| Suporte `System.Runtime.Serialization` para atributos | ❌[Não suportado](#systemruntimeserialization-attributes) |
| `MissingMemberHandling`configuração global                | ❌[Não suportado](#missingmemberhandling) |
| Permitir nomes de propriedades sem aspas                   | ❌[Não suportado](#json-strings-property-names-and-string-values) |
| Permitir aspas únicas em torno de valores de seqüência              | ❌[Não suportado](#json-strings-property-names-and-string-values) |
| Permitir valores JSON não-string para propriedades de string    | ❌[Não suportado](#non-string-values-for-string-properties) |

Esta não é uma lista `Newtonsoft.Json` exaustiva de recursos. A lista inclui muitos dos cenários que foram solicitados em problemas do [GitHub](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) ou postagens [stackoverflow.](https://stackoverflow.com/questions/tagged/system.text.json) Se você implementar uma solução para um dos cenários listados aqui que não possui código de amostra no momento e, se quiser compartilhar sua solução, selecione **Esta página** na [seção Feedback](/dotnet/standard/serialization/system-text-json-migrate-from-newtonsoft-how-to#feedback) desta página. Isso cria um problema do GitHub e lista-o na parte inferior desta página.

## <a name="differences-in-default-jsonserializer-behavior-compared-to-newtonsoftjson"></a>Diferenças no comportamento padrão do JsonSerializer em comparação com Newtonsoft.Json

<xref:System.Text.Json>é rigoroso por padrão e evita qualquer suposição ou interpretação em nome do chamador, enfatizando o comportamento determinístico. A biblioteca é intencionalmente projetada desta forma para desempenho e segurança. `Newtonsoft.Json`é flexível por padrão. Essa diferença fundamental no design está por trás de muitas das seguintes diferenças específicas no comportamento padrão.

### <a name="case-insensitive-deserialization"></a>Desserialização insensível a casos

Durante a desserialização, `Newtonsoft.Json` o nome da propriedade insensível ao caso é correspondente por padrão. O <xref:System.Text.Json> padrão é sensível a maiúsculas e minúsculas, o que dá melhor desempenho, já que está fazendo uma correspondência exata. Para obter informações sobre como fazer a correspondência insensível a casos, consulte [a correspondência de propriedade insensível a casos](system-text-json-how-to.md#case-insensitive-property-matching).

Se você está `System.Text.Json` usando indiretamente usando ASP.NET Core, você não precisa `Newtonsoft.Json`fazer nada para obter comportamentos como . ASP.NET Core especifica as configurações para [nomes de propriedade de invólucro de camelo](system-text-json-how-to.md#use-camel-case-for-all-json-property-names) e correspondência insensível a casos quando ele usa `System.Text.Json`.

### <a name="minimal-character-escaping"></a>Personagem mínimo escapando

Durante a `Newtonsoft.Json` serialização, é relativamente permissivo deixar os personagens passarem sem escapar deles. Ou seja, não os substitui `\uxxxx` `xxxx` por onde está o ponto de código do personagem. Onde ele escapa deles, ele faz isso `\` emitindo um antes `"` `\"`que o personagem (por exemplo, se torne ). <xref:System.Text.Json>escapa de mais caracteres por padrão para fornecer proteções de defesa em profundidade contra scripts entre sites (XSS) ou ataques de divulgação de informações e faz isso usando a seqüência de seis caracteres. `System.Text.Json`escapa de todos os caracteres não-ASCII por padrão, então você não `StringEscapeHandling.EscapeNonAscii` `Newtonsoft.Json`precisa fazer nada se estiver usando em . `System.Text.Json`também escapa de caracteres sensíveis a HTML, por padrão. Para obter informações sobre como `System.Text.Json` substituir o comportamento padrão, consulte [Personalizar a codificação de caracteres](system-text-json-how-to.md#customize-character-encoding).

### <a name="comments"></a>Comentários

Durante a desserialização, `Newtonsoft.Json` ignora os comentários no JSON por padrão. O <xref:System.Text.Json> padrão é lançar exceções para comentários porque a especificação [RFC 8259](https://tools.ietf.org/html/rfc8259) não as inclui. Para obter informações sobre como permitir comentários, consulte [Permitir comentários e commas de trilha](system-text-json-how-to.md#allow-comments-and-trailing-commas).

### <a name="trailing-commas"></a>Commas de arrasto

Durante a desserialização, `Newtonsoft.Json` ignora as commas de arrasto por padrão. Ele também ignora várias commas `[{"Color":"Red"},{"Color":"Green"},,]`de trilha (por exemplo, ). O <xref:System.Text.Json> padrão é lançar exceções para as commas de arrasto porque a especificação [RFC 8259](https://tools.ietf.org/html/rfc8259) não permite. Para obter informações `System.Text.Json` sobre como aceitá-los, consulte [Permitir comentários e commas de trilha](system-text-json-how-to.md#allow-comments-and-trailing-commas). Não há como permitir várias commas.

### <a name="converter-registration-precedence"></a>Precedência do registro de conversor

A `Newtonsoft.Json` precedência de registro para conversores personalizados é a seguinte:

* Atributo na propriedade
* Atributo no tipo
* [Coleção de conversores](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonSerializerSettings_Converters.htm)

Esta ordem significa que um `Converters` conversor personalizado na coleção é substituído por um conversor que é registrado aplicando um atributo no nível do tipo. Ambos os registros são substituídos por um atributo no nível da propriedade.

A <xref:System.Text.Json> precedência de registro para conversores personalizados é diferente:

* Atributo na propriedade
* <xref:System.Text.Json.JsonSerializerOptions.Converters>Coleção
* Atributo no tipo

A diferença aqui é que `Converters` um conversor personalizado na coleção substitui um atributo no nível do tipo. A intenção por trás dessa ordem de precedência é fazer alterações no tempo de execução sobrepor as escolhas de tempo de design. Não há como mudar a precedência.

Para obter mais informações sobre o registro do conversor personalizado, consulte [Registrar um conversor personalizado](system-text-json-converters-how-to.md#register-a-custom-converter).

### <a name="maximum-depth"></a>Profundidade máxima

`Newtonsoft.Json`não tem um limite máximo de profundidade por padrão. Pois <xref:System.Text.Json> há um limite padrão de 64, e é <xref:System.Text.Json.JsonSerializerOptions.MaxDepth?displayProperty=nameWithType>configurável por configuração .

### <a name="json-strings-property-names-and-string-values"></a>Strings JSON (nomes de propriedades e valores de string)

Durante a desserialização, `Newtonsoft.Json` aceita nomes de propriedades cercados por aspas duplas, aspas individuais ou sem aspas. Ele aceita valores de seqüência cercados por aspas duplas ou aspas simples. Por exemplo, `Newtonsoft.Json` aceita o seguinte JSON:

```json
{
  "name1": "value",
  'name2': "value",
  name3: 'value'
}
```

`System.Text.Json`só aceita nomes de propriedade e valores de seqüência em cotações duplas porque esse formato é exigido pela especificação [RFC 8259](https://tools.ietf.org/html/rfc8259) e é o único formato considerado JSON válido.

Um valor incluído em cotações únicas resulta em uma [JsonException](xref:System.Text.Json.JsonException) com a seguinte mensagem:

```
''' is an invalid start of a value.
```

### <a name="non-string-values-for-string-properties"></a>Valores não-string para propriedades de string

`Newtonsoft.Json`aceita valores não-string, como um número `true` `false`ou os literais e, para desserialização para propriedades de string tipo. Aqui está um exemplo de `Newtonsoft.Json` JSON que desserializa com sucesso para a seguinte classe:

```json
{
  "String1": 1,
  "String2": true,
  "String3": false
}
```

```csharp
public class ExampleClass
{
    public string String1 { get; set; }
    public string String2 { get; set; }
    public string String3 { get; set; }
}
```

`System.Text.Json`não desserializar valores não-string em propriedades de seqüência. Um valor não-string recebido para um campo de string resulta em uma [JsonException](xref:System.Text.Json.JsonException) com a seguinte mensagem:

```
The JSON value could not be converted to System.String.
```

## <a name="scenarios-using-jsonserializer-that-require-workarounds"></a>Cenários usando JsonSerializer que requerem soluçãos

Os seguintes cenários não são suportados pela funcionalidade incorporada, mas as soluções são possíveis. As soluçãos são [conversores personalizados,](system-text-json-converters-how-to.md)que `Newtonsoft.Json` podem não fornecer paridade completa com funcionalidade. Para alguns destes, o código de amostra é fornecido como exemplos. Se você confiar `Newtonsoft.Json` nesses recursos, a migração exigirá modificações em seus modelos de objeto .NET ou outras alterações de código.

### <a name="types-without-built-in-support"></a>Tipos sem suporte embutido

<xref:System.Text.Json>não fornece suporte integrado para os seguintes tipos:

* <xref:System.Data.DataTable>e tipos relacionados
* Tipos f#, como [sindicatos discriminados,](../../fsharp/language-reference/discriminated-unions.md) [tipos de registros](../../fsharp/language-reference/records.md)e tipos de registros [anônimos.](../../fsharp/language-reference/anonymous-records.md)
* <xref:System.Dynamic.ExpandoObject>
* <xref:System.TimeZoneInfo>
* <xref:System.Numerics.BigInteger>
* <xref:System.TimeSpan>
* <xref:System.DBNull>
* <xref:System.Type>
* <xref:System.ValueTuple>e seus tipos genéricos associados

Conversores personalizados podem ser implementados para tipos que não têm suporte integrado.

### <a name="quoted-numbers"></a>Números citados

`Newtonsoft.Json`pode serializar ou desserializar números representados por strings JSON (cercados por citações). Por exemplo, ele `{"DegreesCelsius":"23"}` pode `{"DegreesCelsius":23}`aceitar: em vez de . Para habilitar <xref:System.Text.Json>esse comportamento em , implemente um conversor personalizado como o exemplo a seguir. O conversor lida `long`com propriedades definidas como:

* Ele serializa-os como strings JSON.
* Ele aceita números e números JSON dentro das cotações enquanto desserializa.

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/LongToStringConverter.cs)]

Registre este conversor personalizado [usando um atributo](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property) em <xref:System.Text.Json.JsonSerializerOptions.Converters> propriedades individuais `long` ou [adicionando o conversor](system-text-json-converters-how-to.md#registration-sample---converters-collection) à coleção.

### <a name="dictionary-with-non-string-key"></a>Dicionário com tecla não-string

`Newtonsoft.Json`suporta coleções de `Dictionary<TKey, TValue>`tipo . O suporte incorporado para coleções <xref:System.Text.Json> de dicionários é limitado a `Dictionary<string, TValue>`. Ou seja, a chave deve ser uma corda.

Para suportar um dicionário com um inteiro ou algum outro tipo como chave, crie um conversor como o exemplo em [Como escrever conversores personalizados](system-text-json-converters-how-to.md#support-dictionary-with-non-string-key).

### <a name="polymorphic-serialization"></a>Serialização polimórfica

`Newtonsoft.Json`automaticamente faz serialização polimórfica. Para obter informações sobre as capacidades limitadas de serialização polimórfica de <xref:System.Text.Json>, consulte [Serialize propriedades de classes derivadas](system-text-json-how-to.md#serialize-properties-of-derived-classes).

A solução de solução descrita lá é para definir `object`propriedades que podem conter classes derivadas como tipo . Se isso não for possível, outra opção é `Write` criar um conversor com um método para toda a hierarquia do tipo de herança, como o exemplo em [Como escrever conversores personalizados](system-text-json-converters-how-to.md#support-polymorphic-deserialization).

### <a name="polymorphic-deserialization"></a>Desserialização polimórfica

`Newtonsoft.Json`tem `TypeNameHandling` uma configuração que adiciona metadados de nome de tipo ao JSON durante a serialização. Ele usa os metadados enquanto desserializa para fazer desserialização polimórfica. <xref:System.Text.Json>pode fazer uma gama limitada de [serialização polimórfica,](system-text-json-how-to.md#serialize-properties-of-derived-classes) mas não desserialização polimórfica.

Para suportar a desserialização polimórfica, crie um conversor como o exemplo em [Como escrever conversores personalizados](system-text-json-converters-how-to.md#support-polymorphic-deserialization).

### <a name="deserialization-of-object-properties"></a>Desserialização de propriedades de objetos

Quando `Newtonsoft.Json` desserializa <xref:System.Object>para, é:

* Infere o tipo de valores primitivos na `null`carga útil JSON (diferente `DateTime` de ) e retorna o armazenado, `string` `long` `double`ou `boolean`como um objeto em caixa. *Valores primitivos* são valores únicos de JSON, `false`como `null`um número JSON, string, `true`, ou .
* Retorna `JObject` a `JArray` ou para valores complexos na carga útil JSON. *Valores complexos* são coleções de pares de valores-chave JSON dentro de chaves ()`{}`ou listas de valores dentro de parênteses ().`[]` As propriedades e valores dentro dos suportes ou suportes podem ter propriedades ou valores adicionais.
* Retorna uma referência nula quando `null` a carga tem o json literal.

<xref:System.Text.Json>armazena uma `JsonElement` caixa para valores primitivos e <xref:System.Object>complexos sempre que desserializar para, por exemplo:

* Uma `object` propriedade.
* Um `object` valor de dicionário.
* Um `object` valor de matriz.
* Uma `object`raiz.

No `System.Text.Json` entanto, trata `null` o mesmo `Newtonsoft.Json` que e retorna `null` uma referência nula quando a carga tem o JSON literal nele.

Para implementar inferência `object` de tipo para propriedades, crie um conversor como o exemplo em [Como escrever conversores personalizados](system-text-json-converters-how-to.md#deserialize-inferred-types-to-object-properties).

### <a name="deserialize-null-to-non-nullable-type"></a>Desserializar nulo para tipo não anulado

`Newtonsoft.Json`não lança uma exceção no seguinte cenário:

* `NullValueHandling`está definido `Ignore`para , e
* Durante a desserialização, o JSON contém um valor nulo para um tipo de valor não anulado.

No mesmo cenário, <xref:System.Text.Json> é uma exceção. (A configuração de <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType>manuseio nulo correspondente é .)

Se você possui o tipo de destino, a melhor solução é tornar `int` a `int?`propriedade em questão anulada (por exemplo, mudar para ).

Outra solução é fazer um conversor para o tipo, como o `DateTimeOffset` seguinte exemplo que lida com valores nulos para tipos:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DateTimeOffsetNullHandlingConverter.cs)]

Registre este conversor personalizado [usando um atributo na propriedade](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property) ou [adicionando o conversor](system-text-json-converters-how-to.md#registration-sample---converters-collection) à <xref:System.Text.Json.JsonSerializerOptions.Converters> coleção.

**Nota:** O conversor anterior **lida com valores nulos de forma diferente** do `Newtonsoft.Json` que para POCOs que especificam valores padrão. Por exemplo, suponha que o seguinte código represente seu objeto de destino:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

E suponha que o Seguinte JSON seja desserializado usando o conversor anterior:

```json
{
  "Date": null,
  "TemperatureCelsius": 25,
  "Summary": null
}
```

Após a desserialização, o `Date` imóvel possui 1/1/0001 (`default(DateTimeOffset)`), ou seja, o valor definido na construtora é substituído. Dado o mesmo POCO `Newtonsoft.Json` e JSON, a desserialização deixaria `Date` 1/1/2001 na propriedade.

### <a name="deserialize-to-immutable-classes-and-structs"></a>Desserializar para classes imutáveis e estruturas

`Newtonsoft.Json`pode desserializar para classes imutáveis e estruturas porque pode usar construtores que têm parâmetros. <xref:System.Text.Json>suporta apenas construtores públicos sem parâmetros. Como solução de solução, você pode chamar um construtor com parâmetros em um conversor personalizado.

Aqui está uma estrutura imutável com múltiplos parâmetros de construção:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ImmutablePoint.cs#ImmutablePoint)]

E aqui está um conversor que serializa e desserializa esta estrutura:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ImmutablePointConverter.cs)]

Registre este conversor personalizado [adicionando o conversor](system-text-json-converters-how-to.md#registration-sample---converters-collection) à <xref:System.Text.Json.JsonSerializerOptions.Converters> coleção.

Para um exemplo de conversor semelhante que lida com propriedades genéricas abertas, consulte o [conversor incorporado para pares de valor-chave](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/JsonValueConverterKeyValuePair.cs).

### <a name="specify-constructor-to-use"></a>Especificar construtor para usar

O `Newtonsoft.Json` `[JsonConstructor]` atributo permite especificar qual construtor chamar ao desserializar para um POCO. <xref:System.Text.Json>suporta apenas construtores sem parâmetros. Como solução, você pode chamar qualquer construtor que você precisar em um conversor personalizado. Veja o exemplo [de Deserialize para classes e estruturas imutáveis](#deserialize-to-immutable-classes-and-structs).

### <a name="required-properties"></a>Propriedades obrigatórias

Em `Newtonsoft.Json`, você especifica que uma `Required` propriedade `[JsonProperty]` é necessária definindo no atributo. `Newtonsoft.Json`lança uma exceção se nenhum valor for recebido no JSON para uma propriedade marcada conforme necessário.

<xref:System.Text.Json>não lança uma exceção se nenhum valor for recebido para uma das propriedades do tipo de destino. Por exemplo, se `WeatherForecast` você tem uma classe:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

O JSON a seguir é desserializado sem erro:

```json
{
    "TemperatureCelsius": 25,
    "Summary": "Hot"
}
```

Para que a desserialização falhe se nenhuma `Date` propriedade estiver no JSON, implemente um conversor personalizado. O código do conversor de `Date` amostra a seguir abre uma exceção se a propriedade não for definida após a desserialização estar concluída:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastRequiredPropertyConverter.cs)]

Registre este conversor personalizado [usando um atributo na classe POCO](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) ou [adicionando o conversor](system-text-json-converters-how-to.md#registration-sample---converters-collection) à <xref:System.Text.Json.JsonSerializerOptions.Converters> coleção.

Se você seguir esse padrão, não passe no objeto opções <xref:System.Text.Json.JsonSerializer.Serialize%2A> ao <xref:System.Text.Json.JsonSerializer.Deserialize%2A>ligar recursivamente ou . O objeto opções contém a <xref:System.Text.Json.JsonSerializerOptions.Converters%2A> coleção. Se você passá-lo para `Serialize` ou `Deserialize`, o conversor personalizado chama para si mesmo, fazendo um loop infinito que resulta em uma exceção de estouro de pilha. Se as opções padrão não forem viáveis, crie uma nova instância das opções com as configurações necessárias. Essa abordagem será lenta, uma vez que cada nova instância armazena caches independentemente.

O código de conversor anterior é um exemplo simplificado. Uma lógica adicional seria necessária se você precisasse lidar com atributos (como [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) ou diferentes opções (como codificadores personalizados). Além disso, o código de exemplo não lida com propriedades para as quais um valor padrão é definido no construtor. E essa abordagem não diferencia entre os seguintes cenários:

* Uma propriedade está faltando no JSON.
* Uma propriedade para um tipo não anulado está presente no JSON, mas o valor é `int`o padrão para o tipo, como zero para um .
* Uma propriedade para um tipo de valor anulado está presente no JSON, mas o valor é nulo.

### <a name="conditionally-ignore-a-property"></a>Ignorar condicionalmente uma propriedade

`Newtonsoft.Json`tem várias maneiras de ignorar condicionalmente uma propriedade sobre serialização ou desserialização:

* `DefaultContractResolver`permite selecionar propriedades para incluir ou excluir, com base em critérios arbitrários.
* As `NullValueHandling` `DefaultValueHandling` configurações `JsonSerializerSettings` em que você especificar que todas as propriedades de valor nulo ou de valor padrão devem ser ignoradas.
* As `NullValueHandling` `DefaultValueHandling` configurações do `[JsonProperty]` atributo permitem especificar propriedades individuais que devem ser ignoradas quando definidas como nulas ou o valor padrão.

<xref:System.Text.Json>fornece as seguintes maneiras de omitir propriedades durante a serialização:

* O atributo [[JsonIgnore]](system-text-json-how-to.md#exclude-individual-properties) em uma propriedade faz com que a propriedade seja omitida do JSON durante a serialização.
* A opção global [IgnoreNullValues](system-text-json-how-to.md#exclude-all-null-value-properties) permite que você exclua todas as propriedades de valor nulo.
* A opção global [IgnoreReadOnlyProperties](system-text-json-how-to.md#exclude-all-read-only-properties) permite excluir todas as propriedades somente leitura.

Essas opções **não** permitem:

* Ignore todas as propriedades que possuem o valor padrão para o tipo.
* Ignore as propriedades selecionadas que têm o valor padrão para o tipo.
* Ignore as propriedades selecionadas se seu valor for nulo.
* Ignore as propriedades selecionadas com base em critérios arbitrários avaliados no tempo de execução.

Para essa funcionalidade, você pode escrever um conversor personalizado. Aqui está uma amostra POCO e um conversor personalizado para ele que ilustra esta abordagem:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastRuntimeIgnoreConverter.cs)]

O conversor `Summary` faz com que a propriedade seja omitida da serialização se seu valor for nulo, uma string vazia ou "N/A".

Registre este conversor personalizado [usando um atributo na classe](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) ou [adicionando o conversor](system-text-json-converters-how-to.md#registration-sample---converters-collection) à <xref:System.Text.Json.JsonSerializerOptions.Converters> coleção.

Esta abordagem requer uma lógica adicional se:

* O POCO inclui propriedades complexas.
* Você precisa lidar com `[JsonIgnore]` atributos como ou opções como codificadores personalizados.

### <a name="specify-date-format"></a>Especificar o formato da data

`Newtonsoft.Json`fornece várias maneiras `DateTime` de `DateTimeOffset` controlar como propriedades e tipos são serializados e desserializados:

* A `DateTimeZoneHandling` configuração pode ser `DateTime` usada para serializar todos os valores como datas UTC.
* A `DateFormatString` configuração e `DateTime` os conversores podem ser usados para personalizar o formato das strings de data.

Em <xref:System.Text.Json>, o único formato que tem suporte embutido é iso 8601-1:2019 desde que é amplamente adotado, inequívoco, e faz viagens de ida e volta precisamente. Para usar qualquer outro formato, crie um conversor personalizado. Para obter mais informações, consulte [o suporte datetime e datetimeOffset no System.Text.Json](../datetime/system-text-json-support.md).

### <a name="callbacks"></a>Retornos de chamada

`Newtonsoft.Json`permite executar código personalizado em vários pontos do processo de serialização ou desserialização:

* OnDesserialização (quando começa a desserializar um objeto)
* OnDeserializado (quando terminado desserializando um objeto)
* OnSerializing (ao começar a serializar um objeto)
* OnSerialized (quando concluído serializando um objeto)

Em <xref:System.Text.Json>, você pode simular retornos de chamadas escrevendo um conversor personalizado. O exemplo a seguir mostra um conversor personalizado para um POCO. O conversor inclui código que exibe uma mensagem `Newtonsoft.Json` em cada ponto que corresponde a um retorno de chamada.

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastCallbacksConverter.cs)]

Registre este conversor personalizado [usando um atributo na classe](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) ou [adicionando o conversor](system-text-json-converters-how-to.md#registration-sample---converters-collection) à <xref:System.Text.Json.JsonSerializerOptions.Converters> coleção.

Se você usar um conversor personalizado que segue a amostra anterior:

* O `OnDeserializing` código não tem acesso à nova instância POCO. Para manipular a nova instância POCO no início da desserialização, coloque esse código no construtor POCO.
* Não passe no objeto opções quando ligar `Serialize` recursivamente ou `Deserialize`. O objeto opções contém a `Converters` coleção. Se você passar `Serialize` para `Deserialize`ou , o conversor será usado, fazendo um loop infinito que resulta em uma exceção de estouro de pilha.

### <a name="public-and-non-public-fields"></a>Campos públicos e não públicos

`Newtonsoft.Json`pode serializar e desserializar campos, bem como propriedades. <xref:System.Text.Json>só funciona com propriedades públicas. Conversores personalizados podem fornecer essa funcionalidade.

### <a name="internal-and-private-property-setters-and-getters"></a>Setters e getters de propriedades internas e privadas

`Newtonsoft.Json`pode usar setters de propriedade privadas `JsonProperty` e internas e getters através do atributo. <xref:System.Text.Json>suporta apenas setters públicos. Conversores personalizados podem fornecer essa funcionalidade.

### <a name="populate-existing-objects"></a>Preencher objetos existentes

O `JsonConvert.PopulateObject` método `Newtonsoft.Json` em desserializa um documento JSON para uma instância existente de uma classe, em vez de criar uma nova instância. <xref:System.Text.Json>sempre cria uma nova instância do tipo de destino usando o construtor sem parâmetros públicos padrão. Conversores personalizados podem desserializar para uma instância existente.

### <a name="reuse-rather-than-replace-properties"></a>Reutilizar em vez de substituir propriedades

A `Newtonsoft.Json` `ObjectCreationHandling` configuração permite especificar que os objetos nas propriedades devem ser reutilizados em vez de substituídos durante a desserialização. <xref:System.Text.Json>sempre substitui objetos em propriedades.  Conversores personalizados podem fornecer essa funcionalidade.

### <a name="add-to-collections-without-setters"></a>Adicionar às coleções sem setters

Durante a desserialização, `Newtonsoft.Json` adiciona objetos a uma coleção mesmo que a propriedade não tenha setter. <xref:System.Text.Json>ignora propriedades que não têm setters. Conversores personalizados podem fornecer essa funcionalidade.

## <a name="scenarios-that-jsonserializer-currently-doesnt-support"></a>Cenários que jsonSerializer atualmente não suporta

Para os seguintes cenários, as soluções não são práticas ou possíveis. Se você confiar `Newtonsoft.Json` nesses recursos, a migração não será possível sem mudanças significativas.

### <a name="preserve-object-references-and-handle-loops"></a>Preservar referências de objeto e alças de punho

Por padrão, `Newtonsoft.Json` serializa por valor. Por exemplo, se um objeto contém duas propriedades `Person` que contêm `Person` uma referência ao mesmo objeto, os valores das propriedades desse objeto são duplicados no JSON.

`Newtonsoft.Json`tem `PreserveReferencesHandling` uma `JsonSerializerSettings` configuração que permite serializar por referência:

* Um metadados identificador é adicionado ao JSON `Person` criado para o primeiro objeto.
* O JSON criado para o `Person` segundo objeto contém uma referência a esse identificador em vez de valores de propriedade.

`Newtonsoft.Json`também tem `ReferenceLoopHandling` uma configuração que permite ignorar referências circulares em vez de lançar uma exceção.

<xref:System.Text.Json>só suporta serialização por valor e lança uma exceção para referências circulares.

### <a name="systemruntimeserialization-attributes"></a>Atribuições do System.Runtime.Serialization

<xref:System.Text.Json>não suporta atributos `System.Runtime.Serialization` do namespace, `DataMemberAttribute` `IgnoreDataMemberAttribute`como e .

### <a name="octal-numbers"></a>Números octais

`Newtonsoft.Json`trata números com um zero líder como números octais. <xref:System.Text.Json>não permite zeros de liderança porque a especificação [RFC 8259](https://tools.ietf.org/html/rfc8259) não permite.

### <a name="missingmemberhandling"></a>Tratamento de membros ausentes

`Newtonsoft.Json`pode ser configurado para lançar exceções durante a desserialização se o JSON incluir propriedades que estão faltando no tipo de destino. <xref:System.Text.Json>ignora propriedades extras no JSON, exceto quando você usa o [atributo [JsonExtensionData].](system-text-json-how-to.md#handle-overflow-json) Não há solução para o recurso de membro desaparecido.

### <a name="tracewriter"></a>TraceWriter

`Newtonsoft.Json`permite depurar usando `TraceWriter` um registro para exibir que são gerados por serialização ou desserialização. <xref:System.Text.Json>não faz registro.

## <a name="jsondocument-and-jsonelement-compared-to-jtoken-like-jobject-jarray"></a>JsonDocument e JsonElement comparados ao JToken (como JObject, JArray)

<xref:System.Text.Json.JsonDocument?displayProperty=fullName>fornece a capacidade de analisar e construir um DOM (Document Object Model, modelo de objeto **de** documento) somente leitura a partir de cargas JSON existentes. O DOM fornece acesso aleatório aos dados em uma carga útil JSON. Os elementos JSON que compõem a <xref:System.Text.Json.JsonElement> carga útil podem ser acessados através do tipo. O `JsonElement` tipo fornece APIs para converter texto JSON para tipos comuns .NET. `JsonDocument`expõe uma <xref:System.Text.Json.JsonDocument.RootElement> propriedade.

### <a name="jsondocument-is-idisposable"></a>JsonDocument é iDescartável

`JsonDocument`constrói uma exibição na memória dos dados em um buffer agrupado. Portanto, ao `JObject` `JArray` contrário `Newtonsoft.Json`ou `JsonDocument` de `IDisposable` , o tipo implementa e precisa ser usado dentro de um bloco de uso.

Só devolva um `JsonDocument` de sua API se você quiser transferir a propriedade vitalícia e descartar a responsabilidade para o chamador. Na maioria dos cenários, isso não é necessário. Se o chamador precisar trabalhar com todo o <xref:System.Text.Json.JsonElement.Clone%2A> documento <xref:System.Text.Json.JsonDocument.RootElement%2A>JSON, devolva o do , que é um <xref:System.Text.Json.JsonElement>. Se o chamador precisar trabalhar com um elemento específico <xref:System.Text.Json.JsonElement.Clone%2A> dentro <xref:System.Text.Json.JsonElement>do documento JSON, retorne o que . Se você `RootElement` devolver o ou um subelemento diretamente sem fazer um `Clone`, `JsonElement` o `JsonDocument` chamador não poderá acessar o retornado após o que possui ser descartado.

Aqui está um exemplo que exige `Clone`que você faça um:

```csharp
public JsonElement LookAndLoad(JsonElement source)
{
    string json = File.ReadAllText(source.GetProperty("fileName").GetString());

    using (JsonDocument doc = JsonDocument.Parse(json))
    {
        return doc.RootElement.Clone();
    }
}
```

O código anterior `JsonElement` espera `fileName` um que contenha uma propriedade. Ele abre o arquivo JSON e cria um `JsonDocument`. O método pressupõe que o chamador quer trabalhar com `Clone` todo `RootElement`o documento, por isso retorna o do .

Se você `JsonElement` receber um e estiver retornando um subelemento, `Clone` não é necessário devolver um subelemento. O interlocutor é responsável `JsonDocument` por manter vivo `JsonElement` o que o falecido pertence. Por exemplo: 

```csharp
public JsonElement ReturnFileName(JsonElement source)
{
   return source.GetProperty("fileName");
}
```

### <a name="jsondocument-is-read-only"></a>JsonDocument é somente leitura

O <xref:System.Text.Json> DOM não pode adicionar, remover ou modificar elementos JSON. Ele foi projetado desta forma para o desempenho e para reduzir as alocações para analisar tamanhos comuns de carga JSON (ou seja, < 1 MB). Se o seu cenário atualmente usa um DOM modificável, uma das seguintes soluçãos pode ser viável:

* Para construir `JsonDocument` um a partir do zero (ou seja, sem `Parse` passar uma carga JSON `Utf8JsonWriter` existente para o método), escreva `JsonDocument`o texto JSON usando a saída e analise a saída a partir disso para fazer uma nova .
* Para modificar um `JsonDocument`existente, use-o para escrever texto JSON, fazendo alterações enquanto `JsonDocument`você escreve e analise a saída a partir disso para fazer um novo .
* Para mesclar documentos JSON existentes, `JContainer.Merge` equivalentes `Newtonsoft.Json`às `JObject.Merge` OU APIs de , consulte [este problema do GitHub](https://github.com/dotnet/corefx/issues/42466#issuecomment-570475853).

### <a name="jsonelement-is-a-union-struct"></a>JsonElement é uma estrutura sindical

`JsonDocument`expõe o `RootElement` como uma <xref:System.Text.Json.JsonElement>propriedade do tipo , que é um tipo de união, estrutura que abrange qualquer elemento JSON. `Newtonsoft.Json`usa tipos hierárquicos dedicados como `JObject`,`JArray`, `JToken`e assim por diante. `JsonElement`é o que você pode pesquisar e enumerar mais, e você pode usar `JsonElement` para materializar elementos JSON em tipos .NET.

### <a name="how-to-search-a-jsondocument-and-jsonelement-for-sub-elements"></a>Como pesquisar um JsonDocument e JsonElement para obter subelementos

Pesquisas de tokens JSON usando `JObject` ou `JArray` de `Newtonsoft.Json` acordo tendem a ser relativamente rápidas porque são pesquisas em algum dicionário. Em comparação, `JsonElement` as pesquisas em que requerem uma busca seqüencial das `TryGetProperty`propriedades e, portanto, são relativamente lentas (por exemplo, ao usar ). <xref:System.Text.Json>é projetado para minimizar o tempo inicial de análise em vez do tempo de análise. Portanto, use as seguintes abordagens para `JsonDocument` otimizar o desempenho ao pesquisar através de um objeto:

* Use os enumeradores embutidos<xref:System.Text.Json.JsonElement.EnumerateArray%2A> (e) <xref:System.Text.Json.JsonElement.EnumerateObject%2A>em vez de fazer sua própria indexação ou loops.
* Não faça uma busca sequencial em `JsonDocument` todo o todo `RootElement`através de cada propriedade usando . Em vez disso, pesquise em objetos JSON aninhados com base na estrutura conhecida dos dados JSON. Por exemplo, se você está `Grade` procurando `Student` uma propriedade `Student` em objetos, `Grade` faça loop através dos `JsonElement` objetos `Grade` e obtenha o valor de cada um, em vez de pesquisar todos os objetos que procuram por propriedades. Fazer este último resultará em repasses desnecessários sobre os mesmos dados.

Para um exemplo de código, consulte [Usar JsonDocument para acessar dados](system-text-json-how-to.md#use-jsondocument-for-access-to-data).

## <a name="utf8jsonreader-compared-to-jsontextreader"></a>Utf8JsonReader comparado com JsonTextReader

<xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName>é um leitor json codificado de alto desempenho e baixa alocação para texto JSON codificado utf-8, lido a partir de um [byte\<ReadOnlySpan>](xref:System.ReadOnlySpan%601) ou [\<ReadOnlySequence byte>](xref:System.Buffers.ReadOnlySequence%601). O `Utf8JsonReader` é um tipo de baixo nível que pode ser usado para construir analisadores personalizados e desumificadores.

As seções a seguir explicam `Utf8JsonReader`os padrões de programação recomendados para o uso .

### <a name="utf8jsonreader-is-a-ref-struct"></a>Utf8JsonReader é um ref struct

Como `Utf8JsonReader` o tipo é uma *estrutura de ref,* ele tem [certas limitações.](../../csharp/language-reference/keywords/ref.md#ref-struct-types) Por exemplo, ele não pode ser armazenado como um campo em uma classe ou estrutura além de uma estrutura de ref. Para obter alto desempenho, este `ref struct` tipo deve ser um, pois ele precisa fazer cache da entrada [ReadOnlySpan\<byte>](xref:System.ReadOnlySpan%601), que por si só é uma estrutura de ref. Além disso, este tipo é mutável, uma vez que mantém o estado. Portanto, **passá-lo por árbitro** e não por valor. Passá-lo por valor resultaria em uma cópia de estrutura e as alterações de estado não seriam visíveis para o chamador. Isso difere `Newtonsoft.Json` de `Newtonsoft.Json` `JsonTextReader` uma classe. Para obter mais informações sobre como usar os structs de ref, consulte [Escrever código C# seguro e eficiente](../../csharp/write-safe-efficient-code.md).

### <a name="read-utf-8-text"></a>Leia o texto utf-8

Para obter o melhor desempenho `Utf8JsonReader`possível ao usar as cargas JSON já codificadas como texto UTF-8 em vez de como strings UTF-16. Para um exemplo de código, consulte [Filtrar dados usando Utf8JsonReader](system-text-json-how-to.md#filter-data-using-utf8jsonreader).

### <a name="read-with-a-stream-or-pipereader"></a>Leia com um Stream ou PipeReader

O `Utf8JsonReader` suporte é a leitura de um utf-8 codificado [ReadOnlySpan\<byte>](xref:System.ReadOnlySpan%601) ou [\<ReadOnlySequence byte>](xref:System.Buffers.ReadOnlySequence%601) (que é o resultado da leitura de a <xref:System.IO.Pipelines.PipeReader>).

Para leitura síncrona, você pode ler a carga útil JSON até o final do fluxo em uma matriz de bytes e passá-la para o leitor. Para ler a partir de uma seqüência (que <xref:System.Text.Encoding.UTF8>está codificada como UTF-16), ligue .<xref:System.Text.Encoding.GetBytes%2A> para primeiro transcodificar a seqüência para uma matriz de byte codificada UTF-8. Então passe isso `Utf8JsonReader`para o.

Uma `Utf8JsonReader` vez que a entrada considera o texto JSON como texto JSON, uma marca de ordem de byte UTF-8 (BOM) é considerada JSON inválida. O interlocutor precisa filtrar isso antes de passar os dados para o leitor.

Para exemplos de código, consulte [Use Utf8JsonReader](system-text-json-how-to.md#use-utf8jsonreader).

### <a name="read-with-multi-segment-readonlysequence"></a>Leia com readonlysequence de vários segmentos

Se a sua entrada JSON for um [byte\<ReadOnlySpan>, ](xref:System.ReadOnlySpan%601) `ValueSpan` cada elemento JSON pode ser acessado a partir da propriedade no leitor à medida que você passar pelo loop de leitura. No entanto, se a sua entrada for um [byte\<ReadOnlySequence>](xref:System.Buffers.ReadOnlySequence%601) (que é o resultado da leitura de um), <xref:System.IO.Pipelines.PipeReader>alguns elementos JSON podem abranger vários segmentos do `ReadOnlySequence<byte>` objeto. Esses elementos não <xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A> seriam acessíveis a partir de um bloco de memória contíguo. Em vez disso, sempre `ReadOnlySequence<byte>` que você tiver <xref:System.Text.Json.Utf8JsonReader.HasValueSequence%2A> um multisegmento como entrada, pesquise a propriedade no leitor para descobrir como acessar o elemento JSON atual. Aqui está um padrão recomendado:

```csharp
while (reader.Read())
{
    switch (reader.TokenType)
    {
        // ...
        ReadOnlySpan<byte> jsonElement = reader.HasValueSequence ?
            reader.ValueSequence.ToArray() :
            reader.ValueSpan;
        // ...
    }
}
```

### <a name="use-valuetextequals-for-property-name-lookups"></a>Use ValueTextEquals para pesquisas de nomes de propriedades

Não use <xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A> para fazer comparações byte-by-byte, pedindo <xref:System.MemoryExtensions.SequenceEqual%2A> para pesquisas de nome de propriedade. Em <xref:System.Text.Json.Utf8JsonReader.ValueTextEquals%2A> vez disso, porque esse método escapa de todos os personagens que escapam no JSON. Aqui está um exemplo que mostra como procurar uma propriedade chamada "nome":

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ValueTextEqualsExample.cs?name=SnippetDefineUtf8Var)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ValueTextEqualsExample.cs?name=SnippetUseUtf8Var&highlight=11)]

### <a name="read-null-values-into-nullable-value-types"></a>Leia valores nulos em tipos de valores anulados

`Newtonsoft.Json`fornece APIs <xref:System.Nullable%601>que retornam, `ReadAsBoolean`como, `Null` `TokenType` que lida com `bool?`um para você retornando um . As APIs `System.Text.Json` incorporadas retornam apenas tipos de valor não anulados. Por exemplo, <xref:System.Text.Json.Utf8JsonReader.GetBoolean%2A?displayProperty=nameWithType> `bool`retorna um . Ele abre uma exceção se encontrar `Null` no JSON. Os exemplos a seguir mostram duas maneiras de lidar com nulos, uma devolvendo um tipo de valor anulado e outra devolvendo o valor padrão:

```csharp
public bool? ReadAsNullableBoolean()
{
    _reader.Read();
    if (_reader.TokenType == JsonTokenType.Null)
    {
        return null;
    }
    if (_reader.TokenType != JsonTokenType.True && _reader.TokenType != JsonTokenType.False)
    {
        throw new JsonException();
    }
    return _reader.GetBoolean();
}
```

```csharp
public bool ReadAsBoolean(bool defaultValue)
{
    _reader.Read();
    if (_reader.TokenType == JsonTokenType.Null)
    {
        return defaultValue;
    }
    if (_reader.TokenType != JsonTokenType.True && _reader.TokenType != JsonTokenType.False)
    {
        throw new JsonException();
    }
    return _reader.GetBoolean();
}
```

### <a name="multi-targeting"></a>Multiplataforma

Se você precisar continuar `Newtonsoft.Json` a usar para determinadas estruturas de destino, você pode fazer várias metas e ter duas implementações. No entanto, isso não `#ifdefs` é trivial e exigiria algumas e duplicação de origem. Uma maneira de compartilhar o máximo de `ref struct` código `Utf8JsonReader` possível `Newtonsoft.Json` `JsonTextReader`é criar um invólucro ao redor e . Este invólucro unificaria a área da superfície pública enquanto isolava as diferenças comportamentais. Isso permite isolar as alterações principalmente para a construção do tipo, juntamente com a passagem do novo tipo por referência. Este é o padrão que a biblioteca [Microsoft.Extensions.DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/) segue:

* [UnifiedJsonReader.JsonTextReader.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonReader.JsonTextReader.cs)
* [UnifiedJsonReader.Utf8JsonReader.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonReader.Utf8JsonReader.cs)

## <a name="utf8jsonwriter-compared-to-jsontextwriter"></a>Utf8JsonWriter comparado com JsonTextWriter

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName>é uma maneira de alto desempenho de escrever texto JSON codificado `String`UTF-8 de tipos comuns .NET como , `Int32`e `DateTime`. O escritor é um tipo de baixo nível que pode ser usado para construir serializadores personalizados.

As seções a seguir explicam `Utf8JsonWriter`os padrões de programação recomendados para o uso .

### <a name="write-with-utf-8-text"></a>Escreva com o texto UTF-8

Para obter o melhor desempenho `Utf8JsonWriter`possível ao usar as cargas JSON, escreva as cargas JSON já codificadas como texto UTF-8 em vez de como strings UTF-16. Use <xref:System.Text.Json.JsonEncodedText> para cache e pré-codificar nomes e valores conhecidos de propriedade de string sáis como estáticas, e passá-los para o escritor, em vez de usar literais de seqüência UTF-16. Isso é mais rápido do que cache e usando matrizes de bytes UTF-8.

Essa abordagem também funciona se você precisar fazer fugas personalizadas. `System.Text.Json`não permite que você desabilite a fuga enquanto escreve uma string. No entanto, você pode <xref:System.Text.Encodings.Web.JavaScriptEncoder> passar em seu próprio costume `JsonEncodedText` como uma `JavascriptEncoder` opção para o escritor, `JsonEncodedText` ou criar o seu próprio que usa o seu para fazer a fuga, e, em seguida, escrever o em vez da string. Para obter mais informações, consulte [Personalizar a codificação de caracteres](system-text-json-how-to.md#customize-character-encoding).

### <a name="write-raw-values"></a>Escreva valores brutos

O `Newtonsoft.Json` `WriteRawValue` método escreve JSON bruto onde um valor é esperado. <xref:System.Text.Json>não tem equivalente direto, mas aqui está uma solução alternativa que garante que apenas json válido seja escrito:

```csharp
using JsonDocument doc = JsonDocument.Parse(string);
doc.WriteTo(writer);
```

### <a name="customize-character-escaping"></a>Personalizar a fuga de caracteres

A [configuração StringEscapeHandling](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_StringEscapeHandling.htm) oferece opções para escapar de `JsonTextWriter` todos os caracteres **ou** caracteres HTML não-ASCII. Por padrão, `Utf8JsonWriter` escapa de todos os caracteres não-ASCII **e** HTML. Essa fuga é feita por razões de segurança aprofundadas. Para especificar uma política de <xref:System.Text.Encodings.Web.JavaScriptEncoder> fuga <xref:System.Text.Json.JsonWriterOptions.Encoder?displayProperty=nameWithType>diferente, crie um e um conjunto . Para obter mais informações, consulte [Personalizar a codificação de caracteres](system-text-json-how-to.md#customize-character-encoding).

### <a name="customize-json-format"></a>Personalizar o formato JSON

`JsonTextWriter`inclui as seguintes configurações, para as quais `Utf8JsonWriter` não tem equivalente:

* [Recuo](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_Indentation.htm) - Especifica quantos caracteres fazer. `Utf8JsonWriter`sempre faz recuo de 2 caracteres.
* [Recuo](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_IndentChar.htm) - Especifica o caractere a ser usado para recuo.  `Utf8JsonWriter`sempre usa espaço em branco.
* [QuoteChar](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteChar.htm) - Especifica o caractere a ser usado para cercar valores de seqüência de caracteres.  `Utf8JsonWriter`sempre usa aspas duplas.
* [QuoteName](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteName.htm) - Especifica se deve ou não cercar nomes de propriedades com aspas.  `Utf8JsonWriter`sempre os cerca com citações.

Não há solução que lhe faça personalizar o JSON produzido por `Utf8JsonWriter` esses caminhos.

### <a name="write-null-values"></a>Escreva valores nulos

Para escrever valores `Utf8JsonWriter`nulos usando , chamada:

* <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A>para escrever um par de valor-chave com nulo como o valor.
* <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue%2A>para escrever nulo como um elemento de uma matriz JSON.

Para uma propriedade de string, <xref:System.Text.Json.Utf8JsonWriter.WriteString%2A> se <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A> a `WriteNull` seqüência é nula, e são equivalentes a e `WriteNullValue`.

### <a name="write-timespan-uri-or-char-values"></a>Escreva valores de Timespan, Uri ou char

`JsonTextWriter`fornece `WriteValue` métodos para valores [timespan,](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_18.htm) [uri](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_22.htm)e [char.](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_3.htm) `Utf8JsonWriter`não tem métodos equivalentes. Em vez disso, formatar esses `ToString()`valores como <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A>strings (chamando, por exemplo) e chamar .

### <a name="multi-targeting"></a>Multiplataforma

Se você precisar continuar `Newtonsoft.Json` a usar para determinadas estruturas de destino, você pode fazer várias metas e ter duas implementações. No entanto, isso não `#ifdefs` é trivial e exigiria algumas e duplicação de origem. Uma maneira de compartilhar o máximo de código `Utf8JsonWriter` possível `Newtonsoft` `JsonTextWriter`é criar um invólucro ao redor e . Este invólucro unificaria a área da superfície pública enquanto isolava as diferenças comportamentais. Isso permite isolar as alterações principalmente para a construção do tipo. [Microsoft.Extensions.DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/) biblioteca segue:

* [UnifiedJsonWriter.JsonTextWriter.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonWriter.JsonTextWriter.cs)
* [UnifiedJsonWriter.Utf8JsonWriter.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonWriter.Utf8JsonWriter.cs)

## <a name="additional-resources"></a>Recursos adicionais

<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)[Restore this when the roadmap is updated.]-->
* [System.Text.JsonVisão geral](system-text-json-overview.md)
* [Como usarSystem.Text.Json](system-text-json-how-to.md)
* [Como gravar conversores personalizados](system-text-json-converters-how-to.md)
* [Datahora e dateTimeOffset suporte emSystem.Text.Json](../datetime/system-text-json-support.md)
* [System.Text.JsonReferência de API](xref:System.Text.Json)
* [System.Text.Json. Referência de API de serialização](xref:System.Text.Json.Serialization)
