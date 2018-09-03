---
title: Desenvolvendo bibliotecas com as Ferramentas de Plataforma Cruzada
description: Saiba como criar bibliotecas para .NET usando ferramentas da CLI do .NET Core.
author: cartermp
ms.author: mairaw
ms.date: 05/01/2017
ms.openlocfilehash: a6db7a15c484122600afd54814d19ea11bd1abc1
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43256190"
---
# <a name="developing-libraries-with-cross-platform-tools"></a>Desenvolvendo bibliotecas com as Ferramentas de Plataforma Cruzada

Esse artigo aborda como escrever bibliotecas para .NET usando as ferramentas de plataforma cruzada da CLI. A CLI fornece uma experiência eficiente e de baixo nível que funciona em qualquer sistema operacional com suporte. Você ainda pode criar bibliotecas com o Visual Studio e, se essa for sua experiência preferida, [consultar o guia do Visual Studio](libraries-with-vs.md).

## <a name="prerequisites"></a>Pré-requisitos

Você precisa da [CLI e do SDK do .NET Core](https://www.microsoft.com/net/core) instalados no seu computador.

Para as seções deste documento que tratam de versões do .NET Framework, é necessário ter o [.NET Framework](http://getdotnet.azurewebsites.net/) instalado em um computador Windows.

Além disso, se você quiser dar suporte a destinos do .NET Framework mais antigos, você precisará instalar pacotes de direcionamento/desenvolvedor para versões mais antigas de estrutura na [página de plataformas de destino do .NET](http://getdotnet.azurewebsites.net/target-dotnet-platforms.html). Consulte esta tabela:

| Versão do .NET Framework | O que baixar                                       |
| ---------------------- | ------------------------------------------------------ |
| 4.6.1                  | Pacote de Direcionamento do .NET Framework 4.6.1                    |
| 4.6                    | Pacote de Direcionamento do .NET Framework 4.6                      |
| 4.5.2                  | Pacote de Desenvolvedor do .NET Framework 4.5.2                    |
| 4.5.1                  | Pacote de Desenvolvedor do .NET Framework 4.5.1                    |
| 4.5                    | Software Development Kit do Windows (SDK do Windows) para Windows 8         |
| 4.0                    | SDK do Windows para Windows 7 e .NET Framework 4         |
| 2.0, 3.0 e 3.5      | Tempo de Execução do .NET Framework 3.5 SP1 (ou versão do Windows 8 ou superior) |

## <a name="how-to-target-the-net-standard"></a>Como direcionar para o .NET Standard

Se você ainda não conhece o .NET Standard, veja [.NET Standard](../../standard/net-standard.md) para saber mais.

Nesse artigo, há uma tabela que mapeia as versões do .NET Standard para várias implementações:

[!INCLUDE [net-standard-table](~/includes/net-standard-table.md)]

Veja aqui o que essa tabela significa para fins de criação de uma biblioteca:

A versão do .NET Standard que você escolher será uma escolha entre acessar as APIs mais recentes e a capacidade de direcionar para mais implementações do .NET e versões do .NET Standard. Você controla o intervalo das plataformas que podem ser destinos e as versões escolhendo uma versão de `netstandardX.X` (em que `X.X` é um número de versão) e a adicionando ao seu arquivo de projeto (`.csproj` ou `.fsproj`).

Você tem três opções principais ao direcionar para o .NET Standard, dependendo das suas necessidades.

1. Você pode usar a versão padrão do .NET Standard fornecido por modelos, `netstandard1.4`, que fornece acesso à maioria das APIs no .NET Standard ao mesmo tempo que mantém a compatibilidade com UWP, .NET Framework 4.6.1 e o próximo .NET Standard 2.0.

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>netstandard1.4</TargetFramework>
      </PropertyGroup>
    </Project>
    ```

2. Você pode usar uma versão inferior ou superior do .NET Standard, modificando o valor no nó `TargetFramework` do arquivo de projeto.
    
    Versões do .NET Standard são compatíveis com versões anteriores. Isso significa que as bibliotecas `netstandard1.0` são executadas em plataformas `netstandard1.1` e superior. No entanto, não há compatibilidade com versões posteriores: plataformas inferiores do .NET Standard não podem fazer referência às superiores. Isso significa que as bibliotecas `netstandard1.0` não podem fazer de referência a bibliotecas direcionadas a `netstandard1.1` ou superior. Selecione a versão Standard com a combinação de suporte a APIs e plataformas ideal para suas necessidades. É recomendável `netstandard1.4` por enquanto.
    
3. Se desejar direcionar para o .NET Framework versões 4.0 ou inferior ou se desejar usar uma API disponível no .NET Framework, mas não no .NET Standard (por exemplo, `System.Drawing`), leia as seções a seguir para aprender a usar multiplataformas.

## <a name="how-to-target-the-net-framework"></a>Como direcionar o .NET Framework

> [!NOTE]
> Essas instruções pressupõem que você tenha o .NET Framework instalado no seu computador. Consulte os [Pré-requisitos](#prerequisites) para obter as dependências instaladas.

Lembre que algumas das versões do .NET Framework usadas aqui não têm mais suporte. Consulte as [Perguntas Frequentes de Política do Ciclo de Vida de Suporte do .NET Framework](https://support.microsoft.com/gp/framework_faq/en-us) sobre versões sem suporte.

Se desejar alcançar o número máximo de projetos e desenvolvedores, use o .NET Framework 4.0 como seu destino de linha de base. Para direcionar para o .NET Framework, você precisará começar usando o TFM (Moniker da Estrutura de Destino) correto correspondente à versão do .NET Framework à qual você deseja dar suporte.

```
.NET Framework 2.0   --> net20
.NET Framework 3.0   --> net30
.NET Framework 3.5   --> net35
.NET Framework 4.0   --> net40
.NET Framework 4.5   --> net45
.NET Framework 4.5.1 --> net451
.NET Framework 4.5.2 --> net452
.NET Framework 4.6   --> net46
.NET Framework 4.6.1 --> net461
.NET Framework 4.6.2 --> net462
.NET Framework 4.7   --> net47
```

Em seguida, insira esse TFM na seção `TargetFramework` do arquivo de projeto. Por exemplo, aqui está como você escreveria uma biblioteca direcionada ao .NET Framework 4.0:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

E pronto. Embora seja compilado somente para o .NET Framework 4, você pode usar a biblioteca em versões mais recentes do .NET Framework.

## <a name="how-to-multitarget"></a>Como usar Multiplataformas

> [!NOTE]
> As instruções a seguir pressupõem que você tenha o .NET Framework instalado no seu computador. Consulte a seção [Pré-requisitos](#prerequisites) para saber quais dependências você precisa instalar e de onde baixá-las.

Talvez seja necessário direcionar para versões mais antigas do .NET Framework quando seu projeto dá suporte a ambos o .NET Framework e o .NET Core. Nesse cenário, se você quiser usar construções de linguagem e APIs mais recentes para os destinos, use as diretivas `#if` no seu código. Você também pode precisar adicionar diferentes pacotes e dependências para cada plataforma de destino para incluir as diferentes APIs necessárias para cada caso.

Por exemplo, digamos que você tem uma biblioteca que executa operações de rede por meio de HTTP. Para .NET Standard e .NET Framework versões 4.5 ou posterior, você pode usar a classe `HttpClient` do namespace `System.Net.Http`. No entanto, versões anteriores do .NET Framework não tem a classe `HttpClient`, portanto, você pode usar a classe `WebClient` do namespace `System.Net` para elas.

O arquivo de projeto seria semelhante a:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>

  <!-- Need to conditionally bring in references for the .NET Framework 4.0 target -->
  <ItemGroup Condition="'$(TargetFramework)' == 'net40'">
    <Reference Include="System.Net" />
  </ItemGroup>

  <!-- Need to conditionally bring in references for the .NET Framework 4.5 target -->
  <ItemGroup Condition="'$(TargetFramework)' == 'net45'">
    <Reference Include="System.Net.Http" />
    <Reference Include="System.Threading.Tasks" />
  </ItemGroup>
</Project>
```

Você notará três alterações importantes aqui:

1. O nó `TargetFramework` foi substituído pelo `TargetFrameworks` e três TFMs são expressas dentro.
1. Há um nó `<ItemGroup>` para o destino `net40 ` extraindo um que o .NET Framework referencia.
1. Há um nó `<ItemGroup>` para o destino `net45` extraindo dois que o .NET Framework referencia.

O sistema de build reconhece os seguintes símbolos do pré-processador usados nas diretivas `#if`:

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

Aqui está um exemplo fazendo uso de compilação condicional por destino:

```csharp
using System;
using System.Text.RegularExpressions;
#if NET40
// This only compiles for the .NET Framework 4 targets
using System.Net;
#else
 // This compiles for all other targets
using System.Net.Http;
using System.Threading.Tasks;
#endif

namespace MultitargetLib
{
    public class Library
    {
#if NET40
        private readonly WebClient _client = new WebClient();
        private readonly object _locker = new object();
#else
        private readonly HttpClient _client = new HttpClient();
#endif

#if NET40
        // .NET Framework 4.0 does not have async/await
        public string GetDotNetCount()
        {
            string url = "http://www.dotnetfoundation.org/";

            var uri = new Uri(url);

            string result = "";

            // Lock here to provide thread-safety.
            lock(_locker)
            {
                result = _client.DownloadString(uri);
            }

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"Dotnet Foundation mentions .NET {dotNetCount} times!";
        }
#else
        // .NET 4.5+ can use async/await!
        public async Task<string> GetDotNetCountAsync()
        {
            string url = "http://www.dotnetfoundation.org/";

            // HttpClient is thread-safe, so no need to explicitly lock here
            var result = await _client.GetStringAsync(url);

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"dotnetfoundation.org mentions .NET {dotNetCount} times in its HTML!";
        }
#endif
    }
}
```

Se você compilar esse projeto com `dotnet build`, notará três diretórios sob a pasta `bin/`:

```
net40/
net45/
netstandard1.4/
```

Cada um deles contém arquivos `.dll` para cada destino.

## <a name="how-to-test-libraries-on-net-core"></a>Como testar bibliotecas .NET Core

É importante ser capaz de testar em várias plataformas. Você pode usar o [xUnit](http://xunit.github.io/) ou MSTest pronto para uso. Ambos são perfeitamente adequados para realizar o teste da unidade de biblioteca no .NET Core. A maneira de configurar sua solução com projetos de teste dependerá da [estrutura da sua solução](#structuring-a-solution). O exemplo a seguir pressupõe que os diretórios de origem e de teste estão no mesmo diretório de nível superior.

> [!NOTE]
> Ele usa alguns [comandos da CLI do .NET Core](../tools/index.md). Consulte [dotnet new](../tools/dotnet-new.md) e [dotnet sln](../tools/dotnet-sln.md) para obter mais informações.

1. Configure sua solução. Você pode fazer isso usando os seguintes comandos:

   ```bash
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   Isso criará projetos e os conectará em uma solução. O diretório para `SolutionWithSrcAndTest` deve ter esta aparência:

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. Navegue até o diretório do projeto de teste e adicione uma referência a `MyProject.Test` de `MyProject`.

   ```bash
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. Restaure os pacotes e compile projetos:

   ```bash
   dotnet restore
   dotnet build
   ```

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

1. Verifique se o xUnit é executado por meio da execução do comando `dotnet test`. Se você optar por usar o MSTest, o executor de console do MSTest deverá ser executado.
    
E pronto. Agora você pode testar sua biblioteca em todas as plataformas usando as ferramentas de linha de comando. É muito simples testar sua biblioteca agora que está tudo configurado:

1. Faça alterações na sua biblioteca.
1. Execute os testes de linha de comando no diretório de teste com o comando `dotnet test`.

Seu código será recriado automaticamente quando você invoca o comando `dotnet test`.

## <a name="how-to-use-multiple-projects"></a>Como usar vários projetos

Uma necessidade comum das bibliotecas grandes é alocar funcionalidades em diferentes projetos.

Imagine que você deseja compilar uma biblioteca que poderia ser consumida em expressões idiomáticas de C# e F#. Isso significa que os consumidores da sua biblioteca o farão de maneira natural ao C# ou F#. Por exemplo, você poderia consumir a biblioteca em C# dessa forma:

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

No F#, ela poderia assemelhar-se a:

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

Cenários de consumo como esse significam que as APIs que estão sendo acessadas devem ter uma estrutura diferente para C# e F#.  Uma abordagem comum para realizar isso é fatorar toda a lógica de uma biblioteca em um projeto principal, com projetos C# e F# definindo as camadas de API que chamam esse projeto principal.  O restante da seção usará os nomes a seguir:

* **AwesomeLibrary.Core** – Um projeto principal que contém toda a lógica para a biblioteca
* **AwesomeLibrary.CSharp** – Um projeto com APIs públicas destinadas ao consumo em C#
* **AwesomeLibrary.FSharp** – Um projeto com APIs públicas destinadas ao consumo em F#

Você pode executar os comandos a seguir no seu terminal para produzir a mesma estrutura que este guia:

```console
mkdir AwesomeLibrary && cd AwesomeLibrary
dotnet new sln
mkdir AwesomeLibrary.Core && cd AwesomeLibrary.Core && dotnet new classlib
cd ..
mkdir AwesomeLibrary.CSharp && cd AwesomeLibrary.CSharp && dotnet new classlib
cd ..
mkdir AwesomeLibrary.FSharp && cd AwesomeLibrary.FSharp && dotnet new classlib -lang F#
cd ..
dotnet sln add AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
dotnet sln add AwesomeLibrary.CSharp/AwesomeLibrary.CSharp.csproj
dotnet sln add AwesomeLibrary.FSharp/AwesomeLibrary.FSharp.fsproj
```

Isso adicionará os três projetos acima e um arquivo de solução que os vincula. Criar o arquivo de solução e vincular projetos permitirá que você restaure e compile projetos de um nível superior.

### <a name="project-to-project-referencing"></a>Referência projeto a projeto

A melhor maneira de fazer referência a um projeto é usar a CLI do .NET Core para adicionar uma referência de projeto. Dos diretórios dos projetos **AwesomeLibrary.CSharp** e **AwesomeLibrary.FSharp**, você pode executar o seguinte comando:

```console
$ dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

Os arquivos de projeto para **AwesomeLibrary.CSharp** e **AwesomeLibrary.FSharp** agora farão referência a **AwesomeLibrary.Core** como um destino `ProjectReference`.  Você pode verificar isso inspecionando os arquivos de projeto e vendo o seguinte neles:

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

Você pode adicionar esta seção a cada arquivo de projeto manualmente se preferir não usar a CLI do .NET Core.

### <a name="structuring-a-solution"></a>Estruturar uma solução

Outro aspecto importante das soluções multiprojetos é estabelecer uma boa estrutura de projeto geral. Você pode organizar o código da maneira que desejar, e desde que vincule cada projeto ao arquivo de solução com `dotnet sln add`, você poderá executar `dotnet restore` e `dotnet build` no nível da solução.
