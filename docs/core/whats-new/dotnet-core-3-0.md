---
title: Novidades do .NET Core 3.0
description: Conheça os novos recursos encontrados no .NET Core 3.0.
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 05/06/2019
ms.openlocfilehash: 8d6ff6bc55384281119600f2323212441c1815e9
ms.sourcegitcommit: 4c10802ad003374641a2c2373b8a92e3c88babc8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2019
ms.locfileid: "65452474"
---
# <a name="whats-new-in-net-core-30-preview-5"></a>Novidades do .NET Core 3.0 (Versão Prévia 5)

Este artigo descreve as novidades do .NET Core 3.0 (por meio da versão prévia 5). Um dos maiores avanços é o suporte para aplicativos Windows de área de trabalho (somente Windows). Usando a Área de Trabalho do Windows do componente de SDK do .NET Core 3.0, você pode portar seus aplicativos Windows Forms e WPF (Windows Presentation Foundation). Para deixar claro, o componente Windows Desktop só é compatível com o Windows e só é incluído nele. Para obter mais informações, consulte a seção [Área de Trabalho do Windows](#windows-desktop) mais adiante neste artigo.

O .NET Core 3.0 adiciona suporte para C# 8.0. É altamente recomendável que você use a versão mais recente do Visual Studio 2019 Atualização 1 Versão Prévia ou o VSCode com a extensão OmniSharp.

[Baixe e comece a trabalhar com o .NET Core 3.0 Versão Prévia 5](https://aka.ms/netcore3download) agora no Windows, Mac e Linux.

Para obter mais informações sobre cada versão prévia, veja os seguintes avisos:

- [Comunicado do .NET Core 3.0 Versão Prévia 5](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-5/)
- [Comunicado do .NET Core 3.0 Versão Prévia 4](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-4/)
- [Comunicado do .NET Core 3.0 Versão Prévia 3](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-3/)
- [Comunicado do .NET Core 3.0 Versão Prévia 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-2/)
- [Comunicado do .NET Core 3.0 Versão Prévia 1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/)

## <a name="net-core-sdk-windows-installer"></a>Windows Installer do SDK do .NET Core

O instalador MSI para Windows foi alterado do .NET Core 3.0 em diante. Os instaladores de SDK agora atualizarão versões de faixa de recurso do SDK no local. Faixas de recurso são definidas nos grupos de *centenas* na seção *patch* do número de versão. Por exemplo, **3.0.*101*** e **3.0.*201** são versões em duas faixas de recurso diferentes, enquanto **3.0.*101*** e **3.0.*199*** estão na mesma faixa de recurso. Além disso, quando o SDK do .NET Core **3.0.*101*** for instalado, o SDK do .NET Core **3.0.*100*** será removido do computador se ele existir. Quando o SDK do .NET Core **3.0.*200*** é instalado no mesmo computador, o SDK do .NET Core **3.0.*101*** não é removido.

Para obter mais informações sobre controle de versão, consulte [Visão geral de como é o controle de versão no .NET Core](../versions/index.md).

## <a name="c-80-preview"></a>C# 8.0 versão prévia

O .NET Core 3.0 dá suporte ao C# 8 versão prévia. Para obter mais informações sobre recursos do C# 8.0, consulte [Novidades do C# 8.0](../../csharp/whats-new/csharp-8.md).

## <a name="net-standard-21"></a>.NET Standard 2.1

Embora o .NET Core 3.0 dê suporte ao **.NET Standard 2.1**, o modelo `dotnet new classlib` padrão gera um projeto direcionado ao **.NET Standard 2.0**. Para direcionar ao **.NET Standard 2.1**, edite seu arquivo de projeto e altere a propriedade `TargetFramework` para `netstandard2.1`:

```xml
<Project Sdk="Microsoft.NET.Sdk">
 
  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>
 
</Project>
```

Se você estiver usando o Visual Studio, precisará do Visual Studio 2019, já que o Visual Studio 2017 não dá suporte ao **.NET Standard 2.1** nem ao **.NET Core 3.0**. É altamente recomendável que você use o [Visual Studio 2019 Atualização 1 Versão Prévia](https://visualstudio.microsoft.com/vs/preview/).

## <a name="improved-net-core-version-apis"></a>APIs de versão aprimoradas do .NET Core

Começando com o .NET Core 3.0, as APIs de versão fornecidas com o .NET Core agora retornam as informações que você espera. Por exemplo:

```csharp
System.Console.WriteLine($"Environment.Version: {System.Environment.Version}");

// Old result
//   Environment.Version: 4.0.30319.42000
//
// New result
//   Environment.Version: 3.0.0
```

```csharp
System.Console.WriteLine($"RuntimeInformation.FrameworkDescription: {System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription}");

// Old result
//   RuntimeInformation.FrameworkDescription: .NET Core 4.6.27415.71
//
// New result
//   RuntimeInformation.FrameworkDescription: .NET Core 3.0.0-preview4-27615-11
```

> [!WARNING]
> Alteração da falha. Isso é tecnicamente uma alteração da falha, porque o esquema de controle de versão foi alterado.

## <a name="net-platform-dependent-intrinsics"></a>Intrínsecos dependentes da plataforma .NET

Foram adicionadas APIs que permitem acesso a determinadas instruções da CPU orientadas a desempenho, como o **SIMD** ou conjuntos de **instruções de manipulação de bits**. Essas instruções podem ajudar a obter melhorias significativas de desempenho em determinados cenários, tais como processamento de dados eficiente em paralelo. 

Quando apropriado, as bibliotecas .NET começaram usando estas instruções para melhorar o desempenho.

Para obter mais informações, consulte [Intrínsecos dependentes da plataforma .NET](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).

## <a name="default-executables"></a>Executáveis por padrão

O .NET Core agora compila [executáveis dependentes de estrutura](../deploying/index.md#framework-dependent-executables-fde) por padrão. Esse comportamento é novo para aplicativos que usam uma versão do .NET Core instalada globalmente. Anteriormente, apenas [implantações autocontidas](../deploying/index.md#self-contained-deployments-scd) produziam um executável.

Durante `dotnet build` ou `dotnet publish`, é criado um executável que corresponde ao ambiente e à plataforma do SDK que você está usando. Você pode esperar desses executáveis o mesmo que de outros executáveis nativos, como:

* Você pode clicar duas vezes no arquivo executável.
* Você pode iniciar o aplicativo diretamente de um prompt de comando, como `myapp.exe` no Windows e `./myapp` no Linux e macOS.

## <a name="single-file-executables"></a>Executáveis de arquivo único

O comando `dotnet publish` dá suporte ao empacotamento de seu aplicativo em um executável de arquivo único específico da plataforma. O executável é autoextraível e contém todas as dependências (incluindo nativas) necessárias para a execução do aplicativo. Quando o aplicativo é executado pela primeira vez, o aplicativo é extraído para um diretório com base no nome do aplicativo e no identificador do build. A inicialização é mais rápida quando o aplicativo é executado novamente. O aplicativo não precisará autoextrair uma segunda vez, a menos que uma versão nova tenha sido usada.

Para publicar um único arquivo executável, defina o `PublishSingleFile` em seu projeto ou na linha de comando com o comando `dotnet publish`:

```console
dotnet publish -r win10-x64 /p:PublishSingleFile=true
```

Para obter mais informações sobre a publicação de arquivo único, consulte o [documento de design de empacotador de arquivo único](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).

## <a name="tiered-compilation"></a>Compilação em camadas

A TC ([compilação em camadas](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/)) está ativa por padrão com o .NET Core 3.0. Esse recurso permite que o tempo de execução use de modo mais adaptável o compilador JIT (just-in-time) para obter um melhor desempenho.

O principal benefício de TC é habilitar métodos de (re)jitting com um perfil para produzir o código, que pode ser de qualidade inferior mas mais rápido ou de qualidade superior mas mais lento. Isso ajuda a aumentar o desempenho de um aplicativo quando ele passa por vários estágios da execução, desde a inicialização até o estado estável. Isso contrasta com a abordagem de não TC, em que cada método é compilado de uma única maneira (o mesmo que a camada de alta qualidade) que é mais voltada para o estado estável em detrimento do desempenho de inicialização.

Para habilitar o JIT rápido (código com compilação JIT de camada 0), use esta configuração em seu arquivo de projeto:

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>true</TieredCompilationQuickJit>
</PropertyGroup>
```

Para desabilitar completamente a TC, use esta configuração em seu arquivo de projeto:

```xml
<TieredCompilation>false</TieredCompilation>
```

## <a name="build-copies-dependencies"></a>O build copia dependências

O comando `dotnet build` agora copia as dependências do NuGet para seu aplicativo do cache NuGet para a pasta de saída de build. Anteriormente, as dependências eram copiadas apenas como parte de `dotnet publish`.

Há algumas operações, como vinculação e publicação de página do razor, que ainda exigem publicação.

## <a name="local-tools"></a>Ferramentas locais

O .NET Core 3.0 apresenta ferramentas locais. Ferramentas locais são semelhantes às [ferramentas globais](../tools/global-tools.md), mas estão associadas a um local específico no disco. Ferramentas locais não estão disponíveis globalmente e são distribuídas como pacotes NuGet.

> [!WARNING]
> Se você tiver tentado ferramentas locais no .NET Core 3.0 Versão Prévia 1, tais como executar `dotnet tool restore` ou `dotnet tool install`, exclua a pasta de cache local de ferramentas. Caso contrário, as ferramentas locais não funcionarão em nenhuma versão mais recente. Essa pasta está localizada em:
>
> No macOS ou Linux: `rm -r $HOME/.dotnet/toolResolverCache`
>
> No Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`

As ferramentas locais dependem de um nome de arquivo de manifesto `dotnet-tools.json` no seu diretório atual. Esse arquivo de manifesto define as ferramentas que estarão disponíveis nessa pasta e abaixo. Você pode distribuir o arquivo de manifesto com o seu código para garantir que qualquer pessoa que trabalha com o seu código possa restaurar e usar as mesmas ferramentas.

Para ferramentas globais e locais, é necessária uma versão compatível do tempo de execução. Muitas ferramentas que estão atualmente em NuGet.org direcionam para o tempo de execução do .NET Core 2.1. Para instalar essas ferramentas, de forma global ou local, você ainda precisará instalar o [Tempo de execução do NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1).

## <a name="major-version-roll-forward"></a>Roll forward de versão principal

O .NET Core 3.0 introduz um recurso opcional que permite que seu aplicativo efetue roll forward para a versão principal mais recente do .NET Core. Adicionalmente, foi adicionada uma nova configuração para controlar como o roll forward é aplicado ao seu aplicativo. Isso pode ser configurado das seguintes maneiras:

- Propriedade do arquivo de projeto: `RollForward`
- Propriedade do arquivo de configuração de tempo de execução: `rollForward`
- Variável de ambiente: `DOTNET_ROLL_FORWARD`
- Argumento de linha de comando: `--roll-forward`

Um dos valores a seguir precisa ser especificado. Se a configuração for omitida, **Secundária** será o padrão.

- **LatestPatch**\
Efetuar roll forward para a versão de patch mais recente. Isso desabilita o roll forward da versão secundária.
- **Secundária**\
Se a versão secundária solicitada estiver ausente, efetue roll forward para a menor versão secundária mais alta. Se a versão secundária solicitada estiver presente, a política **LatestPatch** será usada.
- **Principal**\
Se a versão principal solicitada estiver ausente, efetuar roll forward para a versão principal mais alta e a versão secundária mais baixa. Se a versão principal solicitada está presente, a política **Secundária** é usada.
- **LatestMinor**\
Efetuar roll forward para a versão secundária mais recente, mesmo se a versão secundária solicitada estiver presente. Destinado a cenários de hospedagem de componente.
- **LatestMajor**\
Efetuar roll forward para a versão principal e a secundária mais altas, mesmo se a principal solicitada estiver presente. Destinado a cenários de hospedagem de componente.
- **Desabilitar**\
Não efetuar roll forward. Associar somente à versão especificada. Essa política não é recomendada para uso geral, pois ela desabilita a capacidade de efetuar roll forward para os patches mais recentes. Esse valor só é recomendado para teste.

Com a exceção da configuração **Desabilitar**, todas as configurações usarão a versão de patch mais recente disponível.

## <a name="windows-desktop"></a>Área de Trabalho do Windows

O .NET Core 3.0 dá suporte a aplicativos da Área de Trabalho do Windows usando o Windows Forms e o WPF (Windows Presentation Foundation). Essas estruturas também oferecem suporte ao uso de controles modernos e no estilo Fluent da biblioteca XAML da interface do usuário do Windows (WinUI) por meio de [Ilhas XAML](/windows/uwp/xaml-platform/xaml-host-controls).

O componente Windows Desktop faz parte do SDK do .NET Core 3.0 do Windows.

É possível criar um novo aplicativo de WPF ou Windows Forms com os seguintes comandos `dotnet`:

```console
dotnet new wpf
dotnet new winforms
```

O Visual Studio 2019 adiciona modelos de **Novo Projeto** ao Windows Forms e WPF no .NET Core 3.0.

Para obter mais informações sobre como portar um aplicativo existente do .NET Framework, consulte [Portar projetos do WPF](../porting/wpf.md) e [Portar projetos do Windows Forms](../porting/winforms.md).

## <a name="com-callable-components---windows-desktop"></a>Componentes que podem ser chamados por COM – Área de Trabalho do Windows

No Windows, agora você pode criar componentes gerenciados que podem ser chamados por COM. Essa funcionalidade é fundamental para usar o .NET Core com modelos de suplemento do COM e também para fornecer paridade com o .NET Framework.

Ao contrário do .NET Framework em que o *mscoree. dll* foi usado como o servidor COM, o .NET Core adicionará uma dll de inicializador nativa ao diretório *bin* quando você compilar o componente COM.

Para obter um exemplo de como criar um componente COM e consumi-lo, veja a [demonstração de COM](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).

## <a name="msix-deployment---windows-desktop"></a>Implantação de MSIX – Área de Trabalho do Windows

[MSIX](https://docs.microsoft.com/windows/msix/) é um novo formato de pacote de aplicativos do Windows. Ele pode ser usado para implantar aplicativos da área de trabalho do .NET Core 3.0 no Windows 10.

O [Projeto de Empacotamento de Aplicativos do Windows](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), disponível no Visual Studio 2019, permite criar pacotes MSIX com aplicativos .NET Core [autossuficientes](../deploying/index.md#self-contained-deployments-scd).

O arquivo de projeto do .NET Core precisa especificar os tempos de execução compatíveis na propriedade `<RuntimeIdentifiers>`:

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="winforms-highdpi"></a>WinForms HighDPI

Aplicativos do Windows Forms do .NET Core podem definir o modo de DPI Alto com <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>. O método `SetHighDpiMode` define o modo de DPI Alto correspondente, a menos que a configuração tenha sido definida por outros meios, tais como `App.Manifest` ou P/Invoke antes de `Application.Run`.

Os valores `highDpiMode` possíveis, conforme expressos pelo enum <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType>, são:

* `DpiUnaware`
* `SystemAware`
* `PerMonitor`
* `PerMonitorV2`
* `DpiUnawareGdiScaled`

Para obter mais informações sobre os modos de DPI Alto, consulte [Desenvolvimento de aplicativos de área de trabalho de DPI Alto no Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).

### <a name="ranges-and-indices"></a>Intervalos e índices

O novo tipo <xref:System.Index?displayProperty=nameWithType> pode ser usado para indexação. É possível criar um a partir de um `int` que conta desde o início, ou com um operador `^` de prefixo (C#) que conta do final:

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

Há também o tipo <xref:System.Range?displayProperty=nameWithType>, que consiste em dois valores `Index` (um para o início e outro para o final) e pode ser escrito com uma expressão de intervalo `x..y` (C#). Em seguida, você pode indexar com um `Range`, o que produz uma fatia:

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

Para obter mais informações, consulte o [tutorial de intervalos e índices](../../csharp/tutorials/ranges-indexes.md).

### <a name="async-streams"></a>Fluxos assíncronos

O tipo <xref:System.Collections.Generic.IAsyncEnumerable%601> é uma nova versão assíncrona de <xref:System.Collections.Generic.IEnumerable%601>. A linguagem permite o uso de `await foreach` em `IAsyncEnumerable<T>` para consumir seus elementos e o uso de `yield return` neles para produzir elementos.

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

Para obter mais informações, consulte o [tutorial de fluxos assíncronos](../../csharp/tutorials/generate-consume-asynchronous-stream.md).

## <a name="ieee-floating-point-improvements"></a>Melhorias de ponto flutuante IEEE

APIs de ponto flutuante estão sendo atualizadas para entrar em conformidade com a [revisão IEEE 754-2008](https://en.wikipedia.org/wiki/IEEE_754-2008_revision). A meta dessas alterações é expor todas as operações **necessárias** e verificar se elas estão comportamentalmente em conformidade com a especificação IEEE. Para obter mais informações sobre as melhorias de ponto flutuante, consulte a postagem no blog [Aprimoramentos de formatação e análise de ponto flutuante no .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/).

As correções de análise e formatação incluem:

* Analisar e arredondar corretamente entradas de qualquer tamanho.
* Analisar e formatar corretamente o zero negativo.
* Analisar corretamente `Infinity` e `NaN`, fazendo uma verificação sem diferenciação de maiúsculas e minúsculas e permitindo um `+` precedente opcional onde aplicável.

Novas APIs <xref:System.Math?displayProperty=nameWithType> incluem:

* <xref:System.Math.BitIncrement(System.Double)> e <xref:System.Math.BitDecrement(System.Double)>\
Correspondem às operações `nextUp` e `nextDown` do IEEE. Retornam o menor número de ponto flutuante que compara o valor maior ou menor que a entrada (respectivamente). Por exemplo, `Math.BitIncrement(0.0)` retorna `double.Epsilon`.

* <xref:System.Math.MaxMagnitude(System.Double,System.Double)> e <xref:System.Math.MinMagnitude(System.Double,System.Double)>\
Correspondem às operações `maxNumMag` e `minNumMag` do IEEE; retornam o valor maior ou menor em magnitude das duas entradas (respectivamente). Por exemplo, `Math.MaxMagnitude(2.0, -3.0)` retorna `-3.0`.

* <xref:System.Math.ILogB(System.Double)>\
Corresponde à operação `logB` IEEE que retorna um valor integral, ele retorna o log de base 2 integral do parâmetro de entrada. Esse método é praticamente o mesmo que `floor(log2(x))`, mas feito com o mínimo de erro de arredondamento.

* <xref:System.Math.ScaleB(System.Double,System.Int32)>\
Corresponde à operação IEEE `scaleB` que usa um valor integral, ele retorna efetivamente `x * pow(2, n)`, mas é feito com o mínimo de erro de arredondamento.

* <xref:System.Math.Log2(System.Double)>\
Corresponde à operação `log2` do IEEE; retorna o logaritmo de base 2. Minimiza o erro de arredondamento.

* <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
Corresponde à operação `fma` do IEEE; executa uma adição e multiplicação fundida. Em outras palavras, realiza `(x * y) + z` como uma única operação, minimizando o erro de arredondamento. Um exemplo é `FusedMultiplyAdd(1e308, 2.0, -1e308)`, que retorna `1e308`. O `(1e308 * 2.0) - 1e308` regular retorna `double.PositiveInfinity`.

* <xref:System.Math.CopySign(System.Double,System.Double)>\
Corresponde à operação `copySign` do IEEE; retorna o valor de `x`, mas com o sinal de `y`.

## <a name="fast-built-in-json-support"></a>Suporte interno rápido a JSON

Usuários do .NET têm dependido basicamente de [**Json.NET**](https://www.newtonsoft.com/json) e outras bibliotecas JSON populares, que continuam a ser boas opções. O **Json.NET** usa cadeias de caracteres do .NET como seu tipo de dados base, o qual subjacentemente é UTF-16.

O novo suporte interno ao JSON é de alto desempenho, baixa alocação e baseado em `Span<byte>`. Três novos tipos principais relacionados ao JSON tiveram o namespace <xref:System.Text.Json?displayProperty=nameWithType> adicionados ao .NET Core 3.0. Esses tipos *ainda* não dão suporte à serialização e desserialização de POCO (objeto CLR básico).

### <a name="utf8jsonreader"></a>Utf8JsonReader

<xref:System.Text.Json.Utf8JsonReader?displayProperty=nameWithType> é um leitor de alto desempenho, baixa alocação e somente para encaminhamento para texto JSON codificado em UTF-8, lido de um `ReadOnlySpan<byte>`. O `Utf8JsonReader` é um tipo fundamental, de baixo nível, que pode ser usado para criar analisadores e desserializadores personalizados. Ler por meio de uma payload JSON usando o novo `Utf8JsonReader` é duas vezes mais rápido do que usar o leitor do **Json.NET**. Ele não alocar até que você precise atualizar tokens JSON como cadeias de caracteres (UTF-16).

Aqui está um exemplo de leitura por meio do arquivo [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) criado pelo Visual Studio Code:

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJson)]

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJsonCall)]

### <a name="utf8jsonwriter"></a>Utf8JsonWriter

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> fornece um modo de alto desempenho, não armazenado em cache, somente avanço para escrita de texto JSON codificado em UTF-8 com base em tipos .NET comuns como `String`, `Int32` e `DateTime`. Assim como o leitor, o gravador é um tipo fundamental, de baixo nível, que pode ser usado para criar os serializadores personalizados. Gravar uma carga JSON usando o novo `Utf8JsonWriter` é de 30 a 80% mais rápido do que usando o gravador de **Json.NET** e não aloca.

### <a name="jsondocument"></a>JsonDocument

<xref:System.Text.Json.JsonDocument?displayProperty=nameWithType> é criado com base no `Utf8JsonReader`. O `JsonDocument` fornece a capacidade de analisar dados JSON e criar um DOM (Modelo de Objeto do Documento) somente leitura que pode ser consultado para dar suporte a enumeração e acesso aleatório. Os elementos JSON que compõem os dados podem ser acessados por meio do tipo <xref:System.Text.Json.JsonElement>, que é exposto pelo `JsonDocument` como uma propriedade chamada `RootElement`. O `JsonElement` contém os enumeradores de objeto e de matriz JSON junto com as APIs para converter o texto JSON em tipos .NET comuns. Analisar uma carga típica do JSON e acessar todos os seus membros usando o `JsonDocument` é 2 a 3 vezes mais rápido do que o **Json.NET** com poucas alocações para os dados que são dimensionados de forma razoável (ou seja, < 1 MB).

Este é um uso de exemplo de `JsonDocument` e `JsonElement` que pode ser usado como ponto de partida:

Aqui está um exemplo em C# 8.0 de leitura por meio do arquivo [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) criado pelo Visual Studio Code:

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJson)]

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJsonCall)]

### <a name="jsonserializer"></a>JsonSerializer

<xref:System.Text.Json.Serialization.JsonSerializer?displayProperty=nameWithType> baseia-se em <xref:System.Text.Json.Utf8JsonReader> e <xref:System.Text.Json.Utf8JsonWriter> para fornecer uma opção de serialização rápida e de pouca memória ao trabalhar com fragmentos e documentos JSON.

EXAMINE: https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/docs/SerializerProgrammingModel.md para obter um exemplo para portar para este artigo

Aqui está um exemplo de como serializar um objeto para JSON:

[!CODE-csharp[JsonSerializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonSerialize)]

Aqui está um exemplo de como desserializar uma cadeia de caracteres JSON para um objeto. Você pode usar a cadeia de caracteres JSON produzida pelo exemplo anterior:

[!CODE-csharp[JsonDeserializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonDeserialize)]

## <a name="interop-improvements"></a>Aprimoramentos de interoperabilidade

O .NET Core 3.0 melhora a interoperabilidade de API nativa.

### <a name="type-nativelibrary"></a>Tipo: NativeLibrary

<xref:System.Runtime.InteropServices.NativeLibrary?displayProperty=nameWithType> fornece um encapsulamento para carregar uma biblioteca nativa (usando a mesma lógica de carga que o .NET Core P/Invoke) e fornecer as funções auxiliares relevantes, tais como `getSymbol`. Para obter um exemplo de código, consulte a [demonstração de DLLMap](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).

### <a name="windows-native-interop"></a>Interoperabilidade nativa do Windows

O Windows oferece uma API nativa rica na forma de APIs C simples, COM e WinRT. Embora o .NET Core dê suporte a **P/Invoke**, o .NET Core 3.0 adiciona a capacidade de **criar conjuntamente APIs COM** e **ativar APIs WinRT**. Para obter um exemplo de código, consulte a [demonstração do Excel](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).

## <a name="http2-support"></a>Compatibilidade com HTTP/2

O tipo <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> dá suporte ao protocolo HTTP/2. O suporte está desabilitado no momento, mas pode ser ativado chamando `AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2Support", true);` antes de usar <xref:System.Net.Http.HttpClient>. Você também pode habilitar o suporte a HTTP/2, configurando a variável de ambiente `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` para `true` antes de executar o aplicativo.

Se o HTTP/2 estiver habilitado, a versão do protocolo HTTP será negociada via TLS/ALPN e HTTP/2 será usado apenas se o servidor selecionar o seu uso.

## <a name="tls-13--openssl-111-on-linux"></a>TLS 1.3 e OpenSSL 1.1.1 no Linux

O .NET Core agora faz proveito do [suporte a protocolo TLS 1.3 no OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/) quando esse protocolo está disponível em um determinado ambiente. Com o TLS 1.3:

* Tempos de conexão são aprimorados com um menor número de viagens de ida e volta necessárias entre o cliente e o servidor.
* Segurança aprimorada devido à remoção de vários algoritmos criptográficos obsoletos e não seguros.

Quando disponíveis, o .NET Core 3.0 usa **OpenSSL 1.1.1**, **1.1.0** ou **1.0.2** em um sistema Linux. Quando o **OpenSSL 1.1.1** está disponível, ambos os tipos <xref:System.Net.Security.SslStream?displayProperty=nameWithType> e <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> usarão o **protocolo TLS 1.3** (supondo que o cliente e o servidor deem suporte ao **protocolo TLS 1.3**).

>[!IMPORTANT]
>Windows e macOS ainda não oferecem suporte a **TLS 1.3**. O .NET Core 3.0 será compatível com **TLS 1.3** nesses sistemas operacionais quando o suporte for disponibilizado.

O exemplo de C# 8.0 a seguir demonstra o .NET Core 3.0 no Ubuntu 18.10 conectando-se a <https://www.cloudflare.com>:

[!CODE-csharp[TLSExample](~/samples/snippets/core/whats-new/whats-new-in-30/cs/TLS.cs#TLS)]

## <a name="cryptography-ciphers"></a>Cifras de criptografia

O .NET 3.0 adiciona o suporte para as criptografias **AES-GCM** e **AES-CCM**, implementadas com <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> e <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType>, respectivamente. Esses algoritmos são ambos do tipo [AEAD (criptografia autenticada com os dados de associação)](https://en.wikipedia.org/wiki/Authenticated_encryption).

O código a seguir demonstra como usar criptografia `AesGcm` para criptografar e descriptografar dados aleatórios.

[!CODE-csharp[AesGcm](~/samples/snippets/core/whats-new/whats-new-in-30/cs/Cipher.cs#AesGcm)]

## <a name="cryptographic-key-importexport"></a>Importar/exportar chave de criptografia

O .NET Core 3.0 dá suporte à importação e exportação de chaves públicas e privadas assimétricas de formatos padrão. Você não precisa usar um certificado X.509.

Todos os tipos principais, tais como *RSA*, *DSA*, *ECDsa* e *ECDiffieHellman*, dão suporte aos seguintes formatos:

* **Chave pública**
  * X.509 SubjectPublicKeyInfo

* **Chave privada**
  * PKCS nº 8 PrivateKeyInfo
  * PKCS nº 8 EncryptedPrivateKeyInfo

Chaves RSA também dão suporte a:

* **Chave pública**
  * PKCS nº 1 RSAPublicKey

* **Chave privada**
  * PKCS nº 1 RSAPrivateKey

Os métodos de exportação produzem dados binários codificados em DER e os métodos de importação esperam o mesmo. Se uma chave for armazenada no formato PEM compatível com texto, o chamador precisará decodificar o conteúdo em Base64 antes de chamar um método de importação.

[!CODE-csharp[RSA](~/samples/snippets/core/whats-new/whats-new-in-30/cs/RSA.cs#Rsa)]

Arquivos **PKCS nº 8** podem ser inspecionados com <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> e **arquivos PFX/PKCS nº 12** podem ser inspecionados com <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>. Arquivos **PFX/PKCS nº 12** podem ser manipulados com <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.

## <a name="serialport-for-linux"></a>SerialPort para Linux

O .NET Core 3.0 dá suporte a <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> no Linux.

Anteriormente, o .NET Core só dava suporte ao uso de `SerialPort` no Windows.

## <a name="docker-and-cgroup-memory-limits"></a>Limites de memória do Docker e cgroup

Da Versão Prévia 3 em diante, a execução do .NET Core 3.0 no Linux com o Docker funciona melhor com limites de memória cgroup. Executar um contêiner do Docker com limites de memória, tais como `docker run -m`, altera o comportamento do .NET Core.

* Tamanho de heap do GC (coletor de lixo) padrão: máximo de 20 MB ou 75% do limite de memória no contêiner.
* O tamanho explícito pode ser definido como um número absoluto ou um percentual do limite de cgroup.
* O tamanho mínimo do segmento reservado por heap de GC é de 16 MB. Esse tamanho reduz o número de heaps que são criados em computadores.

## <a name="smaller-garbage-collection-heap-sizes"></a>Tamanhos menores de heap de coleta de lixo

O tamanho do heap do coletor de lixo padrão foi reduzido, resultando em menor uso de memória pelo .NET Core. Essa alteração se alinha melhor com o orçamento de alocação de geração 0 com os tamanhos de cache de processadores modernos.

## <a name="garbage-collection-large-page-support"></a>Suporte de página grande de coleta de lixo

Páginas grandes (também conhecidas como páginas enormes no Linux) é um recurso em que o sistema operacional é capaz de estabelecer regiões de memória maiores do que o tamanho da página nativo (geralmente 4K) para melhorar o desempenho do aplicativo que está solicitando essas páginas grandes.

O coletor de lixo agora pode ser configurado com a configuração **GCLargePages** como um recurso opcional a ser escolhido para alocar páginas grandes no Windows.

## <a name="gpio-support-for-raspberry-pi"></a>Suporte de GPIO para o Raspberry Pi

Foram lançados dois pacotes para o NuGet que você pode usar para programação de GPIO:

* [System.Device.Gpio](https://www.nuget.org/packages/System.Device.Gpio)
* [Iot.Device.Bindings](https://www.nuget.org/packages/Iot.Device.Bindings)

Os pacotes GPIO incluem as APIs para dispositivos *GPIO*, *SPI*, *I2C* e *PWM*. O pacote de associações de IoT inclui associações de dispositivo. Para obter mais informações, veja o [repositório GitHub de dispositivos](https://github.com/dotnet/iot/blob/master/src/devices/).

## <a name="arm64-linux-support"></a>Suporte a ARM64 no Linux

O .NET Core 3.0 adiciona suporte para ARM64 para Linux. O principal caso de uso para ARM64 atualmente é em cenários de IoT. Para obter mais informações, consulte [Status do .NET Core ARM64](https://github.com/dotnet/announcements/issues/82).

[Imagens do Docker para o .NET Core ARM64](https://hub.docker.com/r/microsoft/dotnet/) estão disponíveis para Alpine, Debian e Ubuntu.

> [!NOTE]
> O suporte do Windows a **ARM64** ainda não está disponível.
