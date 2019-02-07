---
title: Novidades do .NET Core 3.0
description: Conheça os novos recursos encontrados no .NET Core 3.0.
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 12/31/2018
ms.openlocfilehash: baaa2676865c475e331ec889e7b10ae326b552fa
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675082"
---
# <a name="whats-new-in-net-core-30-preview-2"></a>Novidades do .NET Core 3.0 (Versão Prévia 2)

Este artigo descreve as novidades do .NET Core 3.0 (Versão Prévia 2). Um dos maiores avanços é o suporte para aplicativos Windows de área de trabalho (somente Windows). Utilizando um componente do SDK do .NET Core 3.0 chamado Windows Desktop, você pode portar seus aplicativos do Windows Forms e WPF (Windows Presentation Foundation). Para deixar claro, o componente Windows Desktop só é compatível com o Windows e só é incluído nele. Para saber mais, confira a seção [Desktop Windows](#windows-desktop) abaixo.

O .NET Core 3.0 adiciona suporte para C# 8.0.

[Baixe e comece a usar agora mesmo o .NET Core 3 Versão Prévia 2](https://aka.ms/netcore3download) no Windows, no Mac e no Linux. Veja todos os detalhes da versão nas [Notas sobre a versão do .NET Core 3 Versão Prévia 2](https://aka.ms/netcore3releasenotes).

Para obter mais informações sobre o que foi lançado com a Versão Prévia 1, confira o [comunicado sobre o .NET Core 3.0 Versão Prévia 1](https://blogs.msdn.microsoft.com/dotnet/2018/12/04/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/).

Para obter mais informações sobre o que foi lançado com a Versão Prévia 2, confira o [comunicado sobre o .NET Core 3.0 Versão Prévia 1]().

## <a name="c-8"></a>C# 8

O .NET Core 3.0 dá suporte ao C# 8 e, no .NET Core 3.0 Versão Prévia 2 em diante, ele dá suporte a essas novas funcionalidades. Para obter mais informações sobre as funcionalidades do C# 8.0, confira as seguintes postagens no blog:

- [Do more with patterns in C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2019/01/24/do-more-with-patterns-in-c-8-0/) (Faça mais com padrões no C# 8.0)
- [Take C# 8.0 for a spin](https://blogs.msdn.microsoft.com/dotnet/2018/12/05/take-c-8-0-for-a-spin/) (Leve o C# 8.0 para dar uma volta)
- [Building C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2018/11/12/building-c-8-0/) (Compilando o C# 8.0)


### <a name="ranges-and-indices"></a>Intervalos e índices

O novo tipo `Index` pode ser usado para indexação. É possível criar um a partir de um `int` que conta desde o início, ou com um operador `^` de prefixo (C#) que conta do final:

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

Há também um tipo `Range`, que consiste em dois valores `Index`, um para o início e outro para o final, e pode ser escrito com uma expressão de intervalo `x..y` (C#). Você pode indexar com `Range` para produzir uma fatia:

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

### <a name="async-streams"></a>Fluxos assíncronos

O tipo `IAsyncEnumerable<T>` é uma nova versão assíncrona de `IEnumerable<T>`. A linguagem permite o uso de `await foreach` em `IAsyncEnumerable<T>` para consumir seus elementos e o uso de `yield return` neles para produzir elementos.

O exemplo a seguir demonstra a produção e o consumo de fluxos assíncronos. A instrução `foreach` é assíncrona e usa `yield return` para produzir um fluxo assíncrono para chamadores. Esse padrão (usar `yield return`) é o modelo recomendado para a produção de fluxos assíncronos.

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result; 
    }
}
```

Além de poder `await foreach`, você também pode criar iteradores assíncronos, por exemplo, um iterador que retorne um `IAsyncEnumerable/IAsyncEnumerator` em que é possível aplicar `await` e `yield`. Para objetos que precisam ser descartados, você pode usar `IAsyncDisposable`, que vários tipos BCL implementam, como `Stream` e `Timer`.

>[!NOTE]
>Você precisará que o .NET Core 3.0 Versão Prévia 2 use fluxos assíncronos caso deseje fazer o desenvolvimento com o Visual Studio 2019 Preview 2 ou a última versão prévia da [extensão do C# para Visual Studio Code](https://github.com/OmniSharp/omnisharp-vscode/releases/tag/v1.18.0-beta5). Se você estiver usando o .NET Core 3.0 Versão Prévia 2 na linha de comando, tudo funcionará conforme esperado.

### <a name="using-declarations"></a>Declarações using

As *declarações using* são uma nova maneira de garantir que o objeto seja descartado corretamente. Uma *declaração using* mantém o objeto ativo enquanto ele ainda está no escopo. Depois que o objeto fica fora do escopo, ele é automaticamente descartado. Isso reduzirá as *instruções using* aninhadas e tornará o código mais limpo.

```csharp
static void Main(string[] args)
{
    using var options = Parse(args);
    if (options["verbose"]) { WriteLine("Logging..."); }

} // options disposed here
```

### <a name="switch-expressions"></a>Expressões switch

As *expressões switch* são uma forma mais limpa de criar uma *instrução switch* mas, como são uma expressão, elas retornam um valor. As *expressões switch* também são totalmente integradas à correspondência de padrões e usam o padrão de descarte, `_`, para representar o valor `default`.

Veja a sintaxe para as *expressões switch* no seguinte exemplo:

```csharp
static string Display(object o) => o switch
{
    Point { X: 0, Y: 0 }         => "origin",
    Point { X: var x, Y: var y } => $"({x}, {y})",
    _                            => "unknown"
};
```

Há dois padrões envolvidos nesse exemplo. `o` corresponde primeiro ao *padrão de tipo* `Point` e, em seguida, ao *padrão de propriedade* dentro das *{chaves}*. O `_` descreve o `discard pattern`, que é igual a `default` em *instruções switch*.

Os padrões permitem que você escreva um código declarativo que captura sua intenção, em vez de um código de procedimento que implementa testes para ela. O compilador fica responsável por implementar esse código de procedimento entediante e oferece a garantia de sempre fazer isso corretamente.

Ainda haverá casos em que as *instruções switch* serão uma escolha melhor que as *expressões switch* e os padrões poderão ser usados com ambos os estilos de sintaxe.

Para obter mais informações, confira [Do more with patterns in C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2019/01/24/do-more-with-patterns-in-c-8-0/) (Faça mais com padrões no C# 8.0).

## <a name="ieee-floating-point-improvements"></a>Melhorias de ponto flutuante IEEE

As APIs de ponto flutuante estão no processo de serem atualizadas para conformidade com a [revisão do IEEE 754-2008](https://en.wikipedia.org/wiki/IEEE_754-2008_revision). O objetivo dessas alterações é expor todas as operações "obrigatórias" e garantir que seu comportamento esteja em conformidade com a especificação IEEE.

Correções de análise e formatação:

* Analisar e arredondar corretamente entradas de qualquer tamanho.
* Analisar e formatar corretamente o zero negativo.
* Analisar corretamente o Infinito e o NaN executando uma verificação que não diferencia maiúsculas de minúsculas e permitindo um `+` anterior opcional quando aplicável.

As novas APIs de Matemática têm:

* `BitIncrement/BitDecrement`\
Correspondem às operações `nextUp` e `nextDown` do IEEE. Retornam o menor número de ponto flutuante que compara o valor maior ou menor que a entrada (respectivamente). Por exemplo, `Math.BitIncrement(0.0)` retorna `double.Epsilon`.

* `MaxMagnitude/MinMagnitude`\
Correspondem às operações `maxNumMag` e `minNumMag` do IEEE; retornam o valor maior ou menor em magnitude das duas entradas (respectivamente). Por exemplo, `Math.MaxMagnitude(2.0, -3.0)` retorna `-3.0`.

* `ILogB`\
Corresponde à operação `logB` do IEEE que retorna um valor integral; retorna o log de base 2 integral do parâmetro de entrada. Isso é praticamente o mesmo que `floor(log2(x))`, mas feito com erro de arredondamento mínimo.

* `ScaleB`\
Corresponde à operação `scaleB` do IEEE que usa um valor integral; retorna efetivamente `x * pow(2, n)`, mas é feito com erro de arredondamento mínimo.

* `Log2`\
Corresponde à operação `log2` do IEEE; retorna o logaritmo de base 2. Minimiza o erro de arredondamento.

* `FusedMultiplyAdd`\
Corresponde à operação `fma` do IEEE; executa uma adição e multiplicação fundida. Em outras palavras, realiza `(x * y) + z` como uma única operação, minimizando o erro de arredondamento. Um exemplo é `FusedMultiplyAdd(1e308, 2.0, -1e308)`, que retorna `1e308`. O `(1e308 * 2.0) - 1e308` regular retorna `double.PositiveInfinity`.

* `CopySign`\
Corresponde à operação `copySign` do IEEE; retorna o valor de `x`, mas com o sinal de `y`.

## <a name="net-platform-dependent-intrinsics"></a>Intrínsecos dependentes da plataforma .NET

Foram adicionadas APIs que permitem acesso a determinadas instruções da CPU orientadas a desempenho, como o **SIMD** ou conjuntos de **instruções de manipulação de bits**. Essas instruções podem ajudar a obter melhorias significativas de desempenho em determinados cenários, como processamento de dados com eficiência em paralelo. Além de expor as APIs para uso dos programas, as bibliotecas .NET começaram a usar essas instruções para melhorar o desempenho.

Os seguintes PRs do CoreCLR demonstram alguns intrínsecos, por meio de implementação ou uso:

* [Implementar intrínsecos de hardware SSE2 simples](https://github.com/dotnet/coreclr/pull/15585)
* [Implementar intrínsecos de hardware SSE](https://github.com/dotnet/coreclr/pull/15538)
* [Intrínsecos de HW base Arm64](https://github.com/dotnet/coreclr/pull/16822)
* [Usar TZCNT e LZCNT para Locate{First|Last}Found{Byte|Char}](https://github.com/dotnet/coreclr/pull/21073)

Para obter mais informações, confira [Intrínsecos dependentes da plataforma .NET](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md), que define uma abordagem para definição dessa infraestrutura de hardware, permitindo que a Microsoft, fornecedores de chips ou qualquer outra empresa ou indivíduo defina APIs de chip/hardware que devem ser expostas ao código .NET.

## <a name="default-executables"></a>Executáveis por padrão

Agora, o .NET Core criará [executáveis dependentes da estrutura](../deploying/index.md#framework-dependent-executables-fde), por padrão. Isso é novidade para aplicativos que usam uma versão do .NET Core instalada globalmente. Até agora, apenas [implantações autossuficientes](../deploying/index.md#self-contained-deployments-scd) produziam um executável.

Durante `dotnet build` ou `dotnet publish`, um arquivo executável é criado, desde que corresponda ao ambiente e à plataforma do SDK que você está usando. Você pode esperar desses executáveis o mesmo que de outros executáveis nativos, como:

* Você pode clicar duas vezes no arquivo executável.
* Você pode iniciar o aplicativo diretamente de um prompt de comando, como `myapp.exe` no Windows e `./myapp` no Linux e macOS.

## <a name="build-copies-dependencies"></a>O build copia dependências

`dotnet build` agora copia as dependências do NuGet para seu aplicativo do cache do NuGet para a pasta de saída do build. Anteriormente, as dependências eram copiadas apenas como parte de `dotnet publish`. 

Há algumas operações, como vinculação e publicação de página do razor, que ainda exigem publicação.


## <a name="local-dotnet-tools"></a>Ferramentas dotnet locais

>[!WARNING]
>Houve uma alteração nas Ferramentas Locais do .NET Core entre o .NET Core 3.0 Versão Prévia 1 e o .NET Core 3.0 Versão Prévia 2.  Se você tentou usar as ferramentas locais na Versão Prévia 1 executando um comando semelhante a `dotnet tool restore` ou `dotnet tool install`, você precisa excluir a pasta de cache das ferramentas locais antes que as ferramentas locais funcionem corretamente na Versão Prévia 2. Essa pasta está localizada em:
>
>No Mac/Linux: `rm -r $HOME/.dotnet/toolResolverCache`
>
>No Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`
>
>Se você não excluir essa pasta, receberá um erro.

Enquanto o .NET Core 2.1 oferecia suporte para ferramentas globais, o .NET Core 3.0 agora tem ferramentas locais. As ferramentas locais são semelhantes às ferramentas globais, mas estão associadas a um local específico no disco. Isso permite ferramentas por projeto e por repositório. Qualquer ferramenta instalada localmente não está disponível globalmente. As ferramentas são distribuídas como pacotes NuGet.

As ferramentas locais dependem de um nome de arquivo de manifesto `dotnet-tools.json` no seu diretório atual. Esse arquivo de manifesto define as ferramentas que estarão disponíveis nessa pasta e abaixo. Ao criar esse arquivo de manifesto na raiz do seu repositório, garanta que qualquer pessoa que clone seu código possa restaurar e usar as ferramentas necessárias para trabalhar com êxito com seu código.

Para criar um arquivo de manifesto `dotnet-tools.json`, use:

```console
dotnet new tool-manifest
```

Adicione uma nova ferramenta ao manifesto local com:

```console
dotnet tool install <packageId>
```

Liste também as ferramentas no manifesto local com:

```console
dotnet tool list
```

Para ver quais ferramentas são instaladas globalmente, use:

```console
dotnet tool list -g
```

Quando o arquivo de manifesto das ferramentas locais estiver disponível, mas as ferramentas definidas no manifesto não tiverem sido instaladas, use o seguinte comando para baixar e instalar essas ferramentas automaticamente:

```console
dotnet tool restore
```

Execute uma ferramenta local com o seguinte comando:

```console
dotnet tool run <tool-command-name>
```

Quando uma ferramenta local é executada, o dotnet pesquisa um manifesto na estrutura do diretório atual. Ao encontrar um arquivo de manifesto de ferramenta, ele é pesquisado para a ferramenta solicitada. Se a ferramenta for encontrada no manifesto, mas não no cache, o usuário receberá um erro e precisará executar `dotnet tool restore`.

Para remover uma ferramenta do arquivo de manifesto da ferramenta local, execute o seguinte comando:

```console
dotnet tool uninstall <packageId>
```

O arquivo de manifesto da ferramenta é projetado para permitir a edição manual, o que você pode fazer para atualizar a versão necessária ao trabalhar com o repositório. Veja aqui um exemplo de arquivo `dotnet-tools.json`:

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "dotnetsay": {
      "version": "2.1.4",
      "commands": [
        "dotnetsay"
      ]
    },
    "t-rex": {
      "version": "1.0.103",
      "commands": [
        "t-rex"
      ]
    }
  }
}
```

Para ferramentas globais e locais, é necessária uma versão compatível do tempo de execução. Muitas ferramentas que estão atualmente em NuGet.org direcionam para o tempo de execução do .NET Core 2.1. Para instalá-las global ou localmente, você ainda precisará instalar o [tempo de execução do NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1).

## <a name="windows-desktop"></a>Área de Trabalho do Windows

A partir do .NET Core 3.0 Versão prévia 1, é possível criar aplicativos de área de trabalho do Windows usando WPF e Windows Forms. Essas estruturas também oferecem suporte ao uso de controles modernos e no estilo Fluent da biblioteca XAML da interface do usuário do Windows (WinUI) por meio de [Ilhas XAML](/windows/uwp/xaml-platform/xaml-host-controls).

O componente Windows Desktop faz parte do SDK do .NET Core 3.0 do Windows.

É possível criar um novo aplicativo de WPF ou Windows Forms com os seguintes comandos `dotnet`:

```console
dotnet new wpf
dotnet new winforms
```

O Visual Studio 2019 Preview 2 adiciona modelos de **Novo Projeto** ao Windows Forms e WPF no .NET Core 3.0. Ainda não há suporte para designers. Além disso, é possível abrir, iniciar e depurar esses projetos no Visual Studio 2019.

O Visual Studio 2017 15.9 adiciona a capacidade de [habilitar versões prévias do .NET Core](https://blogs.msdn.microsoft.com/dotnet/2018/11/13/net-core-tooling-update-for-visual-studio-2017-version-15-9/), mas você precisa ativar essa funcionalidade e esse não é um cenário compatível.

Os novos projetos são os mesmos que os projetos existentes do .NET Core, com algumas adições. Veja aqui a comparação entre o projeto básico de console do .NET Core e um projeto básico do Windows Forms e WPF.

Em um projeto de console do .NET Core, o projeto usa o SDK `Microsoft.NET.Sdk` e declara uma dependência no .NET Core 3.0 por meio da estrutura de destino `netcoreapp3.0`. Para criar um aplicativo de área de trabalho do Windows, use o SDK `Microsoft.NET.Sdk.WindowsDesktop` e escolha qual estrutura de interface do usuário usar:

```diff
-<Project Sdk="Microsoft.NET.Sdk">
+<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
+   <UseWPF>true</UseWPF>
  </PropertyGroup>
</Project>
```

Para escolher o Windows Forms ao invés da WPF, defina `UseWindowsForms` em vez de `UseWPF`:

```diff
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
-   <UseWPF>true</UseWPF>
+   <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>
</Project>
```

`UseWPF` e `UseWindowsForms` podem ser definidos como `true` se o aplicativo usar ambas as estruturas; por exemplo, quando uma caixa de diálogo do Windows Forms hospeda um controle da WPF.

Compartilhe seus comentários nos repositórios [dotnet/winforms](https://github.com/dotnet/winforms/issues), [dotnet/wpf](https://github.com/dotnet/wpf/issues) e [dotnet/core](https://github.com/dotnet/core/issues).

## <a name="msix-deployment-for-windows-desktop"></a>Implantação do MSIX para Windows Desktop

O [MSIX](https://docs.microsoft.com/windows/msix/) é um novo formato de pacote do aplicativo do Windows. Ele pode ser usado para implantar aplicativos da área de trabalho do .NET Core 3.0 no Windows 10.

O [Projeto de Empacotamento de Aplicativos do Windows](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), disponível no Visual Studio 2019 Preview 2, permite criar pacotes MSIX com aplicativos .NET Core [autossuficientes](../deploying/#self-contained-deployments-scd).

>Observação: O arquivo de projeto do .NET Core precisa especificar os tempos de execução compatíveis na propriedade `<RuntimeIdentifiers>`:
```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="fast-built-in-json-support"></a>Suporte interno rápido a JSON

O ecossistema do .NET dependia do [**Json.NET**](https://www.newtonsoft.com/json) e de outras bibliotecas JSON populares, que continuam sendo boas opções. O **Json.NET** usa cadeias de caracteres do .NET como seu tipo de dados base, que, na verdade, são UTF-16.

O novo suporte interno ao JSON é de alto desempenho, baixa alocação e baseado em `Span<byte>`. Três novos tipos principais relacionados ao JSON tiveram o namespace `System.Text.Json` adicionados ao .NET Core 3.0.

### <a name="utf8jsonreader"></a>Utf8JsonReader

`System.Text.Json.Utf8JsonReader` é um leitor de alto desempenho, baixa alocação e somente para encaminhamento para texto JSON codificado em UTF-8, lido de um `ReadOnlySpan<byte>`. O `Utf8JsonReader` é um tipo fundamental de baixo nível, que pode ser usado para criar analisadores e desserializadores personalizados. Ler por meio de uma payload JSON usando o novo `Utf8JsonReader` é duas vezes mais rápido do que usar o leitor do **Json.NET**. Ele não faz alocação até que você precise atualizar tokens JSON como cadeias de caracteres (UTF-16).

Essa nova API incluirá os seguintes componentes:

* Na versão prévia 1: Leitor de JSON (acesso sequencial)
* Em breve: Gravação de JSON, DOM (acesso aleatório), serializador POCO, desserializador POCO

Veja aqui o loop de leitor básico para o `Utf8JsonReader` que pode ser usado como ponto de partida:

```csharp
using System.Text.Json;

public static void Utf8JsonReaderLoop(ReadOnlySpan<byte> dataUtf8)
{
    var json = new Utf8JsonReader(dataUtf8, isFinalBlock: true, state: default);

    while (json.Read())
    {
        JsonTokenType tokenType = json.TokenType;
        ReadOnlySpan<byte> valueSpan = json.ValueSpan;
        switch (tokenType)
        {
            case JsonTokenType.StartObject:
            case JsonTokenType.EndObject:
                break;
            case JsonTokenType.StartArray:
            case JsonTokenType.EndArray:
                break;
            case JsonTokenType.PropertyName:
                break;
            case JsonTokenType.String:
                string valueString = json.GetStringValue();
                break;
            case JsonTokenType.Number:
                if (!json.TryGetInt32Value(out int valueInteger))
                {
                    throw new FormatException();
                }
                break;
            case JsonTokenType.True:
            case JsonTokenType.False:
                bool valueBool = json.GetBooleanValue();
                break;
            case JsonTokenType.Null:
                break;
            default:
                throw new ArgumentException();
        }
    }

    dataUtf8 = dataUtf8.Slice((int)json.BytesConsumed);
    JsonReaderState state = json.CurrentState;
}
```

### <a name="utf8jsonwriter"></a>Utf8JsonWriter

`System.Text.Json.Utf8JsonWriter` fornece um modo de alto desempenho, não armazenado em cache, somente avanço para escrita de texto JSON codificado em UTF-8 com base em tipos .NET comuns como `String`, `Int32` e `DateTime`. Assim como o leitor, o gravador é um tipo fundamental de baixo nível que pode ser utilizado para criar serializadores personalizados. A escrita de um conteúdo em JSON usando o novo `Utf8JsonWriter` é 30-80% mais rápido do que o uso do gravador no **Json.NET** e não faz alocações.

Este é um uso de exemplo do `Utf8JsonWriter` que pode ser usado como ponto de partida:

```csharp
static int WriteJson(IBufferWriter<byte> output, long[] extraData)
{
    var json = new Utf8JsonWriter(output, state: default);

    json.WriteStartObject();

    json.WriteNumber("age", 15, escape: false);
    json.WriteString("date", DateTime.Now);
    json.WriteString("first", "John");
    json.WriteString("last", "Smith");

    json.WriteStartArray("phoneNumbers", escape: false);
    json.WriteStringValue("425-000-1212", escape: false);
    json.WriteStringValue("425-000-1213");
    json.WriteEndArray();

    json.WriteStartObject("address");
    json.WriteString("street", "1 Microsoft Way");
    json.WriteString("city", "Redmond");
    json.WriteNumber("zip", 98052);
    json.WriteEndObject();

    json.WriteStartArray("ExtraArray");
    for (var i = 0; i < extraData.Length; i++)
    {
        json.WriteNumberValue(extraData[i]);
    }
    json.WriteEndArray();

    json.WriteEndObject();

    json.Flush(isFinalBlock: true);

    return (int)json.BytesWritten;
}
```

O `Utf8JsonWriter` aceita `IBufferWriter<byte>` como a localização de saída na qual gravar os dados JSON de forma síncrona e você, como o chamador, precisa fornecer uma implementação concreta. Atualmente, a plataforma não inclui uma implementação dessa interface. Para obter um exemplo de `IBufferWriter<byte>`, confira [https://gist.github.com/ahsonkhan/c76a1cc4dc7107537c3fdc0079a68b35](https://gist.github.com/ahsonkhan/c76a1cc4dc7107537c3fdc0079a68b35)

### <a name="jsondocument"></a>JsonDocument

`System.Text.Json.JsonDocument` é criado com base no `Utf8JsonReader`. O `JsonDocument` fornece a capacidade de analisar dados JSON e criar um DOM (Modelo de Objeto do Documento) somente leitura que pode ser consultado para dar suporte a enumeração e acesso aleatório. Os elementos JSON que compõem os dados podem ser acessados por meio do tipo `JsonElement` que é exposto pelo `JsonDocument` como uma propriedade chamada `RootElement`. O `JsonElement` contém os enumeradores de objeto e de matriz JSON junto com as APIs para converter o texto JSON em tipos .NET comuns. A análise de um conteúdo JSON típico e o acesso a todos os seus membros usando o `JsonDocument` é de 2 a 3 vezes mais rápido do que o **Json.NET**, com muito poucas alocações para dados que são razoavelmente dimensionados (ou seja, < 1 MB).

Este é um uso de exemplo de `JsonDocument` e `JsonElement` que pode ser usado como ponto de partida:

```csharp
static double ParseJson()
{
    const string json = " [ { \"name\": \"John\" }, [ \"425-000-1212\", 15 ], { \"grades\": [ 90, 80, 100, 75 ] } ]";

    double average = -1;

    using (JsonDocument doc = JsonDocument.Parse(json))
    {
        JsonElement root = doc.RootElement;
        JsonElement info = root[1];

        string phoneNumber = info[0].GetString();
        int age = info[1].GetInt32();

        JsonElement grades = root[2].GetProperty("grades");

        double sum = 0;
        foreach (JsonElement grade in grades.EnumerateArray())
        {
            sum += grade.GetInt32();
        }

        int numberOfCourses = grades.GetArrayLength();
        average = sum / numberOfCourses;
    }

    return average;
}
```

## <a name="assembly-unloadability"></a>Capacidade de descarregamento de assembly

A capacidade de descarregamento de assembly é uma nova funcionalidade do `AssemblyLoadContext`. Essa nova funcionalidade é amplamente transparente de uma perspectiva da API, exposta com apenas algumas novas APIs. Ela permite que um contexto do carregador seja descarregado, liberando toda a memória para tipos instanciados, campos estáticos e para o próprio assembly. Um aplicativo deve conseguir carregar e descarregar assemblies por meio desse mecanismo para sempre, sem experimentar perda de memória.

Essa nova funcionalidade pode ser usada para cenários semelhantes a:

* Cenários de plug-in em que o carregamento e o descarregamento dinâmicos de plug-in são necessários. 
* Compilação, execução e, em seguida, liberação dinâmicas do código. Útil para sites, mecanismos de script etc.
* Carregamento de assemblies para introspecção (como ReflectionOnlyLoad), embora [MetadataLoadContext](#type-metadataloadcontext) (lançado na Versão Prévia 1) seja uma opção melhor em muitos casos.

Para obter mais informações, confira o documento [Usando a capacidade de descarregamento](https://github.com/dotnet/coreclr/pull/22221).

O descarregamento de assembly exige cuidado significativo para garantir que todas as referências a objetos gerenciados externas a um contexto do carregador sejam compreendidas e gerenciadas. Quando o contexto do carregador é solicitado a ser descarregado, as referências externas precisam ter sido removidas, de modo que o contexto do carregador seja autoconsistente somente consigo mesmo.

A capacidade de descarregamento de assembly era fornecida no .NET Framework por Domínios do Aplicativo (AppDomains), que não são compatíveis com o .NET Core. Os AppDomains apresentavam benefícios e limitações em comparação com esse novo modelo. Considere que esse novo modelo de carregador seja mais flexível e tenha um desempenho mais alto quando comparado aos AppDomains.

## <a name="windows-native-interop"></a>Interoperabilidade nativa do Windows

O Windows oferece uma API nativa sofisticada, na forma de APIs C simples, COM e WinRT. No .NET Core 1.0 em diante, há suporte para **PInvoke**. Agora com o .NET Core 3.0, foi adicionado o suporte para a capacidade de **Cocriar APIs COM** e **Ativar APIs WinRT**.

Veja um exemplo de como usar o COM com o [código-fonte de Demonstração do Excel](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).


## <a name="type-sequencereader"></a>Tipo: SequenceReader

`System.Buffers.SequenceReader` foi adicionado ao .NET Core 3.0, podendo ser usado como um leitor para `ReadOnlySequence<T>`. Isso permite uma análise fácil, de baixa alocação e de alto desempenho dos dados `System.IO.Pipelines`, que pode cruzar vários buffers de backup. 

O exemplo a seguir quebra uma `Sequence` de entrada em linhas delimitadas `CR/LF` válidas:

```csharp
private static ReadOnlySpan<byte> CRLF => new byte[] { (byte)'\r', (byte)'\n' };

public static void ReadLines(ReadOnlySequence<byte> sequence)
{
    SequenceReader<byte> reader = new SequenceReader<byte>(sequence);

    while (!reader.End)
    {
        if (!reader.TryReadToAny(out ReadOnlySpan<byte> line, CRLF, advancePastDelimiter:false))
        {
            // Couldn't find another delimiter
            // ...
        }

        if (!reader.IsNext(CRLF, advancePast: true))
        {
            // Not a good CR/LF pair
            // ...
        }

        // line is valid, process
        ProcessLine(line);
    }
}
```

## <a name="type-metadataloadcontext"></a>Tipo: MetadataLoadContext

Adicionamos o tipo `MetadataLoadContext`, permitindo a leitura de metadados de assembly sem afetar o domínio do aplicativo do chamador. Assemblies são lidos como dados, incluindo assemblies compilados para arquiteturas e plataformas diferentes do ambiente de tempo de execução atual. `MetadataLoadContext` se sobrepõe a <xref:System.Reflection.Assembly.ReflectionOnlyLoad*>, que só está disponível no .NET Framework.

`MetdataLoadContext` está disponível no [pacote System.Reflection.MetadataLoadContext](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext). Este é um pacote do .NET Standard 2.0.

O `MetadataLoadContext` expõe APIs semelhantes ao tipo <xref:System.Runtime.Loader.AssemblyLoadContext>, mas não é baseado nesse tipo. Assim como <xref:System.Runtime.Loader.AssemblyLoadContext>, o `MetadataLoadContext` permite o carregamento de assemblies dentro de um universo de carregamento de assemblies isolado. APIs `MetdataLoadContext` retornam objetos <xref:System.Reflection.Assembly>, permitindo o uso de APIs de reflexão familiares. APIs orientadas a execução, como [MethodBase.Invoke](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/src/System/Reflection/TypeLoading/Methods/RoMethod.cs#L127), não são permitidas e emitirão InvalidOperationException.

O exemplo a seguir demonstra como localizar tipos concretos em um assembly que implementa determinada interface:

```csharp
var paths = new string[] {@"C:\myapp\mscorlib.dll", @"C:\myapp\myapp.dll"};
var resolver = new PathAssemblyResolver(paths);
using (var lc = new MetadataLoadContext(resolver))
{
    Assembly a = lc.LoadFromAssemblyName("myapp");
    Type myInterface = a.GetType("MyApp.IPluginInterface");
    foreach (Type t in a.GetTypes())
    {
        if (t.IsClass && myInterface.IsAssignableFrom(t))
            Console.WriteLine($"Class {t.FullName} implements IPluginInterface");
    }
}
```

Cenários para `MetadataLoadContext` incluem recursos de tempo de design, ferramentas de tempo de build e recursos de destaque de tempo de execução, que precisam inspecionar um conjunto de assemblies como dados e ter todos os bloqueios de arquivo e memória liberados após a execução da inspeção.

Em `MetadataLoadContext`, uma classe de resolvedor é transmitida para seu construtor. O trabalho do resolvedor é carregar um `Assembly` considerando seu `AssemblyName`. A classe de resolvedor deriva da classe abstrata `MetadataAssemblyResolver`. Uma implementação do resolvedor para cenários com base em caminho é fornecida com `PathAssemblyResolver`.

Os [testes de MetadataLoadContext](https://github.com/dotnet/corefx/tree/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests) demonstram vários casos de uso. Os [testes de assembly](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests/Assembly/AssemblyTests.cs) são uma boa forma de começar.

## <a name="tls-13--openssl-111-on-linux"></a>TLS 1.3 e OpenSSL 1.1.1 no Linux

O .NET Core agora aproveitará o [suporte do TLS 1.3 no OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), quando estiver disponível em determinado ambiente. O TLS 1.3 tem vários benefícios, de acordo com a [equipe do OpenSSL](https://www.openssl.org/blog/blog/2018/09/11/release111/):

* Tempos de conexão aprimorados, devido a uma redução no número de viagens de ida e volta necessário entre o cliente e servidor.

* Segurança aprimorada devido à remoção de vários algoritmos criptográficos obsoletos e não seguros e à criptografia de maior quantidade do handshake de conexão.

O .NET Core 3.0 Versão prévia 1 é capaz de utilizar **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, ou **OpenSSL 1.0.2** (seja qual for a melhor versão encontrada, em um sistema Linux).  Quando o **OpenSSL 1.1.1**  estiver disponível, os tipos SslStream e HttpClient usarão **TLS 1.3** ao usar `SslProtocols.None` (protocolos padrão do sistema), considerando que o cliente e o servidor ofereçam suporte a **TLS 1.3**.

O exemplo a seguir demonstra o .NET Core 3.0 Versão prévia 1 em Ubuntu 18.10 conectando-se a <https://www.cloudflare.com>:

```csharp
using System;
using System.Net.Security;
using System.Net.Sockets;
using System.Threading.Tasks;

namespace tlstest
{
    class Program
    {
        static async Task Main()
        {
            using (TcpClient tcpClient = new TcpClient())
            {
                string targetHost = "www.cloudflare.com";

                await tcpClient.ConnectAsync(targetHost, 443);

                using (SslStream sslStream = new SslStream(tcpClient.GetStream()))
                {
                    await sslStream.AuthenticateAsClientAsync(targetHost);
                    await Console.Out.WriteLineAsync($"Connected to {targetHost} with {sslStream.SslProtocol}");
                }
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/tlstest$ dotnet run
Connected to www.cloudflare.com with Tls13
user@comp-ubuntu1810:~/tlstest$ openssl version
OpenSSL 1.1.1  11 Sep 2018
```

>[!IMPORTANT]
>Windows e macOS ainda não oferecem suporte a **TLS 1.3**. O .NET Core 3.0 será compatível com **TLS 1.3** nesses sistemas operacionais quando o suporte for disponibilizado.

## <a name="cryptography"></a>Criptografia

Foi adicionado suporte para criptografias **AES-GCM** e **AES-CCM**, implementadas via `System.Security.Cryptography.AesGcm` e `System.Security.Cryptography.AesCcm`. Esses algoritmos são os [algoritmos de Criptografia Autenticada com Dados de Associação (AEAD) ](https://en.wikipedia.org/wiki/Authenticated_encryption) e os primeiros algoritmos de Criptografia Autenticada (AE) adicionados ao .NET Core.

O código a seguir demonstra como usar criptografia **AesGcm** para criptografar e descriptografar dados aleatórios.

O código para **AesCcm** seria quase idêntico (somente os nomes de variáveis de classe seriam diferentes).

```csharp
// key should be: pre-known, derived, or transported via another channel, such as RSA encryption
byte[] key = new byte[16];
RandomNumberGenerator.Fill(key);

byte[] nonce = new byte[12];
RandomNumberGenerator.Fill(nonce);

// normally this would be your data
byte[] dataToEncrypt = new byte[1234];
byte[] associatedData = new byte[333];
RandomNumberGenerator.Fill(dataToEncrypt);
RandomNumberGenerator.Fill(associatedData);

// these will be filled during the encryption
byte[] tag = new byte[16];
byte[] ciphertext = new byte[dataToEncrypt.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Encrypt(nonce, dataToEncrypt, ciphertext, tag, associatedData);
}

// tag, nonce, ciphertext, associatedData should be sent to the other part

byte[] decryptedData = new byte[ciphertext.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Decrypt(nonce, ciphertext, tag, decryptedData, associatedData);
}

// do something with the data
// this should always print that data is the same
Console.WriteLine($"AES-GCM: Decrypted data is{(dataToEncrypt.SequenceEqual(decryptedData) ? "the same as" : "different than")} original data.");
```

## <a name="cryptographic-key-importexport"></a>Importar/exportar chave de criptografia

O .NET Core 3.0 Versão prévia 1 oferece suporte à importação e exportação de chaves públicas e privadas assimétricas nos formatos padrão, sem a necessidade de usar um certificado X.509.

Todos os tipos de chave (RSA, DSA, ECDsa, ECDiffieHellman) são compatíveis com o formato **X.509 SubjectPublicKeyInfo** para chaves públicas e com os formatos **PKCS#8 PrivateKeyInfo** e **PKCS#8 EncryptedPrivateKeyInfo** para chaves privadas. RSA também é compatível com **PKCS#1 RSAPublicKey** e **PKCS#1 RSAPrivateKey**. Todos os métodos de exportação produzem dados binários codificados por DER, e os métodos de importação esperam o mesmo. Se uma chave for armazenada no formato PEM compatível com texto, o chamador precisará decodificar o conteúdo em Base64 antes de chamar um método de importação.

```csharp
using System;
using System.IO;
using System.Security.Cryptography;

namespace rsakeyprint
{
    class Program
    {
        static void Main(string[] args)
        {
            using (RSA rsa = RSA.Create())
            {
                byte[] keyBytes = File.ReadAllBytes(args[0]);
                rsa.ImportRSAPrivateKey(keyBytes, out int bytesRead);
 
                Console.WriteLine($"Read {bytesRead} bytes, {keyBytes.Length-bytesRead} extra byte(s) in file.");
                RSAParameters rsaParameters = rsa.ExportParameters(true);
                Console.WriteLine(BitConverter.ToString(rsaParameters.D));
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/rsakeyprint$ echo Making a small key to save on screen space.
Making a small key to save on screen space.
user@comp-ubuntu1810:~/rsakeyprint$ openssl genrsa 768 | openssl rsa -outform der -out rsa.key
Generating RSA private key, 768 bit long modulus (2 primes)
..+++++++
........+++++++
e is 65537 (0x010001)
writing RSA key
user@comp-ubuntu1810:~/rsakeyprint$ dotnet run rsa.key
Read 461 bytes, 0 extra byte(s) in file.
0F-D0-82-34-F8-13-38-4A-7F-C7-52-4A-F6-93-F8-FB-6D-98-7A-6A-04-3B-BC-35-8C-7D-AC-A5-A3-6E-AD-C1-66-30-81-2C-2A-DE-DA-60-03-6A-2C-D9-76-15-7F-61-97-57-
79-E1-6E-45-62-C3-83-04-97-CB-32-EF-C5-17-5F-99-60-92-AE-B6-34-6F-30-06-03-AC-BF-15-24-43-84-EB-83-60-EF-4D-3B-BD-D9-5D-56-26-F0-51-CE-F1
user@comp-ubuntu1810:~/rsakeyprint$ openssl rsa -in rsa.key -inform der -text -noout | grep -A7 private
privateExponent:
    0f:d0:82:34:f8:13:38:4a:7f:c7:52:4a:f6:93:f8:
    fb:6d:98:7a:6a:04:3b:bc:35:8c:7d:ac:a5:a3:6e:
    ad:c1:66:30:81:2c:2a:de:da:60:03:6a:2c:d9:76:
    15:7f:61:97:57:79:e1:6e:45:62:c3:83:04:97:cb:
    32:ef:c5:17:5f:99:60:92:ae:b6:34:6f:30:06:03:
    ac:bf:15:24:43:84:eb:83:60:ef:4d:3b:bd:d9:5d:
    56:26:f0:51:ce:f1
```

Arquivos PKCS#8 podem ser inspecionados com a classe `System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo`.

Arquivos PFX/PKCS#12 podem ser inspecionados e manipulados com `System.Security.Cryptography.Pkcs.Pkcs12Info` e `System.Security.Cryptography.Pkcs.Pkcs12Builder`, respectivamente.

## <a name="serialport-for-linux"></a>SerialPort para Linux

O .NET Core 3.0 agora oferece suporte a <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> no Linux.

Anteriormente, o .NET Core só era compatível com o uso do tipo `SerialPort` no Windows.

## <a name="more-bcl-improvements"></a>Mais melhorias do BCL

O `Span<T>`, `Memory<T>` e tipos relacionados, que foram introduzidos no .NET Core 2.1, foram otimizados no .NET Core 3.0. Operações comuns, como construção de intervalo, divisão, análise e formatação agora funcionam melhor. 

Além disso, tipos como `String` tiveram melhorias discretas para torná-los mais eficientes quando usados como chaves com `Dictionary<TKey, TValue>` e outras coleções. Nenhuma alteração de código é necessária para se beneficiar dessas melhorias.

As melhorias a seguir também são novas no .NET Core 3 Versão prévia 1:

* Suporte a Brotli integrado a HttpClient
* ThreadPool.UnsafeQueueWorkItem(IThreadPoolWorkItem)
* Unsafe.Unbox
* CancellationToken.Unregister
* Operadores aritméticos complexos
* APIs de soquete para TCP em atividade
* StringBuilder.GetChunks
* Análise de IPEndPoint
* RandomNumberGenerator.GetInt32

## <a name="tiered-compilation"></a>Compilação em camadas

A [compilação em camadas](https://blogs.msdn.microsoft.com/dotnet/2018/08/02/tiered-compilation-preview-in-net-core-2-1/) é ativada por padrão com o .NET Core 3.0. É um recurso que permite que o tempo de execução use de forma mais adaptável o compilador Just-In-Time (JIT) para obter um melhor desempenho, tanto na inicialização quanto para maximizar a taxa de transferência.

Esse recurso foi adicionado como um recurso opcional no [.NET Core 2.1](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/) e, em seguida, foi habilitado por padrão no [.NET Core 2.2 Versão prévia 2](https://blogs.msdn.microsoft.com/dotnet/2018/09/12/announcing-net-core-2-2-preview-2/). Subsequentemente, foi revertido novamente para opcional na versão .NET Core 2.2.

## <a name="arm64-linux-support"></a>Suporte a ARM64 no Linux

Foi adicionado suporte para o ARM64 no Linux. O principal caso de uso para ARM64 atualmente é em cenários de IoT.

As imagens de [Docker Alpine, Debian e Ubuntu estão disponíveis para o .NET Core para ARM64](https://hub.docker.com/r/microsoft/dotnet/).

Consulte [Status do ARM64 do .NET Core](https://github.com/dotnet/announcements/issues/82) para saber mais.

>[!NOTE]
> O suporte do Windows a **ARM64** ainda não está disponível.

## <a name="install-net-core-30-previews-on-linux-with-snap"></a>Instalar as Versões Prévias do .NET Core 3.0 no Linux com o Snap

O Snap é a maneira preferencial para instalar e testar versões prévias do .NET Core em [distribuições Linux que dão suporte ao Snap](https://docs.snapcraft.io/installing-snapd/6735).

Depois de configurar o Snap no sistema, execute o comando a seguir para instalar o [SDK da Versão Prévia do SDK do .NET Core 3.0](https://snapcraft.io/dotnet-sdk).

```console
sudo snap install dotnet-sdk --beta --classic
```
 
Quando o .NET Core é instalado usando o pacote do Snap, o comando padrão do .NET Core é `dotnet-sdk.dotnet`, em vez de apenas `dotnet`. O benefício do comando com namespace é que ele não entrará em conflito com uma possível versão do .NET Core instalada globalmente existente. Esse comando pode ter um alias com o `dotnet` com:

```console
sudo snap alias dotnet-sdk.dotnet dotnet
```

Algumas distribuições exigem uma etapa adicional para habilitar o acesso ao certificado SSL. Confira nossa [Configuração do Linux](https://github.com/dotnet/core/blob/master/Documentation/linux-setup.md) para obter detalhes.

## <a name="gpio-support-for-raspberry-pi"></a>Suporte de GPIO para o Raspberry Pi

Dois novos pacotes foram lançados para o NuGet, que podem ser usados para a programação de GPIO.

* [System.Device.Gpio](https://www.nuget.org/packages/System.Device.Gpio/0.1.0-prerelease.19078.2)
* [Iot.Device.Bindings](https://www.nuget.org/packages/Iot.Device.Bindings/0.1.0-prerelease.19078.2)

Os Pacotes de GPIO incluem APIs para dispositivos GPIO, SPI, I2C e PWM. O pacote de associações de IoT inclui [associações de dispositivo](https://github.com/dotnet/iot/blob/master/src/devices/README.md) para vários chips e sensores, as mesmas disponíveis em [dotnet/iot – src/devices](https://github.com/dotnet/iot/tree/master/src/devices).

As APIs de porta serial atualizadas que foram anunciadas como parte do .NET Core 3.0 Versão Prévia 1 não fazem parte desses pacotes, mas estão disponíveis como parte da plataforma .NET Core.


## <a name="platform-support"></a>Suporte de plataforma

O .NET Core 3 terá suporte nos seguintes sistemas operacionais:

* Cliente Windows: 7, 8.1, 10 (1607 e posterior)
* Windows Server: 2012 R2 SP1 e posterior
* macOS: 10.12 e posterior
* RHEL: 6 e posterior
* Fedora: 26 e posterior
* Ubuntu: 16.04 e posterior
* Debian: 9 e posterior
* SLES: 12 e posterior
* openSUSE: 42.3+
* Alpine: 3.8+

O suporte de chip é descrito a seguir:

* x64 no Windows, no macOS e no Linux
* x86 no Windows
* ARM32 no Windows e no Linux
* ARM64 no Linux

Para o Linux, há suporte para o ARM32 no Debian 9 ou posterior e no Ubuntu 16.04 ou posterior. Para o ARM64, isso é o mesmo que o ARM32 com a adição do Alpine 3.8. Essas são as mesmas versões dessas distribuições que têm suporte para o X64.

As imagens do Docker para o .NET Core 3.0 estão disponíveis em [microsoft/dotnet no Hub do Docker](https://hub.docker.com/r/microsoft/dotnet/). Atualmente, a Microsoft está no processo de adoção do [MCR (Registro de Contêiner da Microsoft)](https://cloudblogs.microsoft.com/opensource/2019/01/17/improved-discovery-experience-microsoft-containers-docker-hub/) e é esperado que as imagens finais do .NET Core 3.0 sejam publicadas somente no MCR.
