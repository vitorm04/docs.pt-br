---
title: Desenvolvendo bibliotecas com as Ferramentas de Plataforma Cruzada
description: Desenvolvendo bibliotecas com as Ferramentas de Plataforma Cruzada
keywords: .NET, .NET Core
author: cartermp
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 9f6e8679-bd7e-4317-b3f9-7255a260d9cf
translationtype: Human Translation
ms.sourcegitcommit: 0882a5ca2f7814e2fd168dce40705d11b199f102
ms.openlocfilehash: de44f103bef6006dd1a952c48c1e172f6277a95b

---

# <a name="developing-libraries-with-cross-platform-tools"></a>Desenvolvendo bibliotecas com as Ferramentas de Plataforma Cruzada

**Alguns detalhes estão sujeitos a alterações à medida que a cadeia de ferramentas evolui.**

Esse artigo aborda como escrever bibliotecas para .NET usando as ferramentas de plataforma cruzada da CLI.  A CLI fornece uma experiência eficiente e de baixo nível que funciona em qualquer sistema operacional com suporte.  Você ainda pode criar bibliotecas com o Visual Studio e, se essa for sua experiência preferida, [consultar o guia do Visual Studio](libraries-with-vs.md).

## <a name="prerequisites"></a>Pré-requisitos

Você precisa da [CLI e do SDK do .NET Core](https://www.microsoft.com/net/core) instalados no seu computador.

Para as seções deste documento que tratam de versões do .NET Framework ou de PCL (Bibliotecas de Classes Portáteis), é necessário ter o [.NET Framework](http://getdotnet.azurewebsites.net/) instalado em um computador Windows.  

Além disso, se você quiser dar suporte a destinos do .NET Framework mais antigos, você precisará instalar pacotes de direcionamento/desenvolvedor para versões mais antigas de estrutura na [página de plataformas de destino do .NET](http://getdotnet.azurewebsites.net/target-dotnet-platforms.html).  Consulte esta tabela:

| Versão do .NET Framework | O que baixar |
| ---------------------- | ----------------- |
| 4.6.1 | Pacote de Direcionamento do .NET Framework 4.6.1 |
| 4.6 | Pacote de Direcionamento do .NET Framework 4.6 |
| 4.5.2 | Pacote de Desenvolvedor do .NET Framework 4.5.2 |
| 4.5.1 | Pacote de Desenvolvedor do .NET Framework 4.5.1 |
| 4.5 | Software Development Kit do Windows (SDK do Windows) para Windows 8 |
| 4.0 | SDK do Windows para Windows 7 e .NET Framework 4 |
| 2.0, 3.0 e 3.5 | Tempo de Execução do .NET Framework 3.5 SP1 (ou versão do Windows 8 ou superior) |

## <a name="how-to-target-the-net-standard"></a>Como direcionar para o .NET Standard

Se você não estiver bem familiarizada com o .NET Standard, consulte a [.NET Standard Library](../../standard/library.md) para saber mais.

Nesse artigo, há uma tabela que mapeia as versões do .NET Standard para várias implementações:

| Nome da Plataforma | Alias |  |  |  |  |  | | |
| :---------- | :--------- |:--------- |:--------- |:--------- |:--------- |:--------- |:--------- |:--------- |
|.NET Standard | netstandard | 1.0 | 1.1 | 1.2 | 1.3 | 1.4 | 1.5 | 1.6 |
|.NET Core|netcoreapp|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|1.0|
|.NET Framework|net|&rarr;|4.5|4.5.1|4.6|4.6.1|4.6.2|4.6.3|
|Plataformas Mono/Xamarin||&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|*|
|Plataforma Universal do Windows|uap|&rarr;|&rarr;|&rarr;|&rarr;|10.0|||
|Windows|win|&rarr;|8.0|8.1|||||
|Windows Phone|wpa|&rarr;|&rarr;|8.1|||||
|Windows Phone Silverlight|wp|8.0|||||||

Veja aqui o que essa tabela significa para fins de criação de uma biblioteca:

A versão do .NET Platform Standard que você escolher será uma escolha entre acessar as APIs mais recentes e a capacidade de direcionar para mais plataformas .NET e versões do Framework.  Você controla o intervalo das plataformas que podem ser destinos e as versões escolhendo uma versão de `netstandardX.X` (em que `X.X` é um número de versão) e adicioná-lo ao seu arquivo `project.json`.

Além disso, o [pacote NuGet correspondente para dependência](https://www.nuget.org/packages/NETStandard.Library/) é o `NETStandard.Library` versão `1.6.0`.  Embora nada impeça que você dependa de `Microsoft.NETCore.App` como com os aplicativos de console, em geral isso não é recomendável.  Se você precisar de APIs de um pacote não especificado no `NETStandard.Library`, sempre poderá especificar esse pacote além de `NETStandard.Library` na seção `dependencies` do seu arquivo `project.json`.

Você tem três opções principais ao direcionar para o .NET Standard, dependendo das suas necessidades.

1. Você pode usar a versão mais recente do .NET Standard, `netstandard1.6`, que serve para quando você desejar acesso a mais APIs e não se incomodar em ter menor alcance entre as implementações.
2. Você pode usar uma versão anterior do .NET Standard para direcionar as implementações do .NET anteriores. O custo disso aqui é não ter acesso a algumas das APIs mais recentes.
    
    Por exemplo, se você quiser ter garantia de compatibilidade com o .NET Framework 4.6 e posterior, deverá escolher `netstandard1.3`:

    ```json
    {
        "dependencies":{
            "NETStandard.Library":"1.6.0"
        },
        "frameworks":{
            "netstandard1.3":{}
        }
    }
    ```
    
    Versões do .NET Standard são compatíveis com versões anteriores. Isso significa que as bibliotecas `netstandard1.0` são executadas em plataformas `netstandard1.1` e superior.  No entanto, não há compatibilidade com versões posteriores: plataformas inferiores do .NET Standard não podem fazer referência às superiores.  Isso significa que as bibliotecas `netstandard1.0` não podem fazer de referência a bibliotecas direcionadas a `netstandard1.1` ou superior.  Selecione a versão Standard com a combinação de suporte a APIs e plataformas ideal para suas necessidades.
    
3. Se desejar direcionar para o .NET Framework versões 4.0 ou inferior ou se desejar usar uma API disponível no .NET Framework, mas não no .NET Standard (por exemplo, `System.Drawing`), leia as seções a seguir para aprender a usar multiplataformas.

## <a name="how-to-target-the-net-framework"></a>Como direcionar o .NET Framework

> [!NOTE]
> Essas instruções pressupõem que você tenha o .NET Framework instalado no seu computador.  Consulte os [Pré-requisitos](#prerequisites) para obter as dependências instaladas.

Lembre que algumas das versões do .NET Framework usadas aqui não têm mais suporte.  Consulte as [Perguntas Frequentes de Política do Ciclo de Vida de Suporte do .NET Framework](https://support.microsoft.com/gp/framework_faq/en-us) sobre versões sem suporte.

Se deseja alcançar o número máximo de projetos e desenvolvedores, use o .NET Framework 4 como seu destino de linha de base. Para direcionar para o .NET Framework, você precisará começar usando o TFM (Moniker da Estrutura de Destino) correto correspondente à versão do .NET Framework à qual você deseja dar suporte.

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
.NET Framework 4.6.3 --> net463
```

Por exemplo, mostramos aqui como você escreveria uma biblioteca direcionada ao .NET Framework 4:

```json
{
    "frameworks":{
        "net40":{}
    }
}
```

E pronto.  Embora seja compilado somente para o .NET Framework 4, você pode usar a biblioteca em versões mais recentes do .NET Framework.

## <a name="how-to-target-a-portable-class-library-pcl"></a>Como direcionar uma PCL (Biblioteca de Classes Portátil)

> [!NOTE]
> Essas instruções pressupõem que você tenha o .NET Framework instalado no seu computador.  Consulte os [Pré-requisitos](#prerequisites) para obter as dependências instaladas.

Direcionando um perfil de PCL é um pouco mais complicado do que direcionar para o .NET Framework ou .NET Standard.  Para os iniciantes, [consulte essa lista de perfis de PCL](http://embed.plnkr.co/03ck2dCtnJogBKHJ9EjY/preview) para localizar o destino do NuGet que corresponde ao perfil de PCL de destino.

Depois disso, você precisará fazer o seguinte:

1. Crie uma nova entrada em `frameworks` no seu `project.json`, denominado `.NETPortable,Version=v{version},Profile=Profile{profile}`, em que `{version}` e `{profile}` correspondem a um número de versão da PCL e ao número de Perfil, respectivamente.
2. Na nova entrada, liste cada assembly usado para esse destino em uma entrada `frameworkAssemblies`.  Isso inclui `mscorlib`, `System` e `System.Core`.
3. Se estiver usando multiplataforma (consulte a próxima seção), você deverá listar explicitamente as dependências para cada destino em suas entradas de destino.  Você não poderá mais usar uma entrada `dependencies` global.

Veja a seguir um exemplo de direcionamento para a PCL Perfil 328. O Perfil 328 dá suporte a: .NET Standard 1.4, .NET Framework 4, Windows 8, Windows Phone 8.1, Windows Phone Silverlight 8.1 e Silverlight 5.

```json
{
    "frameworks":{
        ".NETPortable,Version=v4.0,Profile=Profile328":{
            "frameworkAssemblies":{
                "mscorlib":"",
                "System":"",
                "System.Core":""
            }
        }
    }
}
```

Quando você compila um projeto que inclui a PCL Perfil 328 como uma estrutura no arquivo *project.json*, ele terá essa subpasta na pasta */bin/debug*:

```
portable-net40+sl50+netcore45+wpa81+wp8/
```

Esta pasta contém os arquivos `.dll` necessários para executar sua biblioteca.

## <a name="how-to-multitarget"></a>Como usar Multiplataformas

> [!NOTE]
> As instruções a seguir pressupõem que você tenha o .NET Framework instalado no seu computador.  Consulte a seção [Pré-requisitos](#prerequisites) para saber quais dependências você precisa instalar e de onde baixá-las.

Talvez seja necessário direcionar para versões mais antigas do .NET Framework quando seu projeto dá suporte a ambos o .NET Framework e o .NET Core. Nesse cenário, se você quiser usar construções de linguagem e APIs mais recentes para os destinos, use as diretivas `#if` no seu código. Você também pode precisar adicionar diferentes pacotes e dependências no seu `project.json file` para cada plataforma de destino para incluir as diferentes APIs necessárias para cada caso.

Por exemplo, digamos que você tem uma biblioteca que executa operações de rede por meio de HTTP. Para .NET Standard e .NET Framework versões 4.5 ou posterior, você pode usar a classe `HttpClient` do namespace `System.Net.Http`. No entanto, versões anteriores do .NET Framework não tem a classe `HttpClient`, portanto, você pode usar a classe `WebClient` do namespace `System.Net` para elas.

Dessa forma, o arquivo `project.json` seria semelhante a:

```json
{
    "frameworks":{
        "net40":{
            "frameworkAssemblies": {
                "System.Net":"",
                "System.Text.RegularExpressions":""
            }
        },
        "net452":{
            "frameworkAssemblies":{
                "System.Net":"",
                "System.Net.Http":"",
                "System.Text.RegularExpressions":"",
                "System.Threading.Tasks":""
            }
        },
        "netstandard1.6":{
            "dependencies": {
                "NETStandard.Library":"1.6.0",
            }
        }
    }
}
```

Observe que os assemblies do .NET Framework precisam ser referenciado explicitamente no destino `net40` e `net452`, e as referências de NuGet também são explicitamente listadas no destino `netstandard1.6`.  Isso é necessário em cenários multiplataforma.

Em seguida, as instruções `using` no arquivo de origem podem ser ajustadas dessa forma:

```csharp
#if NET40
// This only compiles for the .NET Framework 4 targets
using System.Net;
#else
// This compiles for all other targets
using System.Net.Http;
using System.Threading.Tasks;
#endif
```

O sistema de build reconhece os seguintes símbolos do pré-processador usados nas diretivas `#if`:

```
.NET Framework 2.0   --> NET20
.NET Framework 3.5   --> NET35
.NET Framework 4.0   --> NET40
.NET Framework 4.5   --> NET45
.NET Framework 4.5.1 --> NET451
.NET Framework 4.5.2 --> NET452
.NET Framework 4.6   --> NET46
.NET Framework 4.6.1 --> NET461
.NET Framework 4.6.2 --> NET462
.NET Standard 1.0    --> NETSTANDARD1_0
.NET Standard 1.1    --> NETSTANDARD1_1
.NET Standard 1.2    --> NETSTANDARD1_2
.NET Standard 1.3    --> NETSTANDARD1_3
.NET Standard 1.4    --> NETSTANDARD1_4
.NET Standard 1.5    --> NETSTANDARD1_5
.NET Standard 1.6    --> NETSTANDARD1_6
```

E, em meio à origem, você pode usar as diretivas `#if` para usar essas bibliotecas condicionalmente. Por exemplo:

```csharp
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
            
            return $"dotnetfoundation.orgmentions .NET {dotNetCount} times in its HTML!";
        }
#endif
    }
```

Quando você compila um projeto que inclui `net40`, `net45` e `netstandard1.6` como estruturas no arquivo *project.json*, ele terá essas subpastas na *pasta /bin/debug*:

```
net40/
net45/
netstandard1.6/
```

### <a name="but-what-about-multitargeting-with-portable-class-libraries"></a>Mas e quanto à multiplataforma com Bibliotecas de Classes Portáteis?

Se você deseja realizar compilação cruzada em um destino de PCL, você deve adicionar uma definição de build ao seu arquivo `project.json` em `buildOptions` no seu destino PCL.  Você pode usar as diretivas `#if` na origem, as quais usam a definição de build como um símbolo do pré-processador.

Por exemplo, se você quiser direcionar para o [PCL Perfil 328](http://embed.plnkr.co/03ck2dCtnJogBKHJ9EjY/preview) (o .NET Framework 4, Windows 8, Windows Phone Silverlight 8, Windows Phone 8.1 e Silverlight 5), você poderia fazer referência a ele como "PORTABLE328" durante a compilação cruzada.  Basta adicioná-lo ao arquivo `project.json` como um atributo `buildOptions`:

```json
{
    "frameworks":{
        "netstandard1.6":{
           "dependencies":{
                "NETStandard.Library":"1.6.0",
            }
        },
        ".NETPortable,Version=v4.0,Profile=Profile328":{
            "buildOptions": {
                "define": [ "PORTABLE328" ]
            },
            "frameworkAssemblies":{
                "mscorlib":"",
                "System":"",
                "System.Core":"",
                "System.Net"
            }
        }
    }
}

```

Agora você pode compilar condicionalmente em relação a esse destino:

```csharp
#if !PORTABLE328
using System.Net.Http;
using System.Threading.Tasks;
// Potentially other namespaces which aren't compatible with Profile 328
#endif
```

Como `PORTABLE328` agora é reconhecido pelo compilador, a biblioteca de PCL Perfil 328 gerada por um compilador não incluirá `System.Net.Http` ou `System.Threading.Tasks`.

Quando você compila um projeto que inclui o PCL Perfil 328 e `netstandard1.6` como estruturas no arquivo *project.json*, ele terá essas subpastas na pasta */bin/debug*:

```
portable-net40+sl50+netcore45+wpa81+wp8/
netstandard1.6/
```

## <a name="how-to-use-native-dependencies"></a>Como usar dependências nativas

Pode ser útil escrever uma biblioteca que depende de um arquivo `.dll` nativo.  Se você estiver escrevendo uma biblioteca, terá duas opções:

1. faça referência ao `.dll` nativo diretamente no seu `project.json`.
2. Empacote esse `.dll` em seu próprio pacote NuGet e crie a dependência do pacote.

Para a primeira opção, você precisará incluir o seguinte no seu arquivo `project.json`:

1. Definindo `allowUnsafe` para `true` em uma seção `buildOptions`.
2. Especificando um [RID (Identificador de Tempo de Execução)](../rid-catalog.md) em uma seção `runtimes`.
3. Especificando o caminho para os arquivos `.dll` nativos aos quais você está fazendo referência.

Veja esse `project.json` de exemplo para um arquivo `.dll` nativo no diretório raiz do projeto que é executado no Windows:

```json
{
    "buildOptions":{
        "allowUnsafe":true
    },
    "runtimes":{
        "win10-x64":{}
    },
    "packOptions":{
        "files":{
            "mappings":{
                "runtimes/win10-x64/native":{
                    "includeFiles":[ "native-lib.dll"]
                }
            }            
        }
    }
}
```

Se você estiver distribuindo sua biblioteca como um pacote, será recomendável colocar o arquivo `.dll` no nível raiz do seu projeto.

Como a segunda opção, você precisará criar um pacote NuGet dos seus arquivos `.dll`, hospedá-lo em um feed NuGet ou MyGet e criar a dependência dele diretamente.  Você ainda precisará definir `allowUnsafe` como `true` na seção `buildOptions` do seu `project.json`.  Veja esse exemplo (considerando que `MyNativeLib` é um pacote Nuget na versão `1.2.0`):

```json
{
    "buildOptions":{
        "allowUnsafe":true
    },
    "dependencies":{
        "MyNativeLib":"1.2.0"
    }
}
```

Para ver um exemplo de empacotamento de binários nativos de plataforma cruzada, confira o [Pacote ASP.NET Libuv](https://github.com/aspnet/libuv-package) e a [referência correspondente no KestrelHttpServer](https://github.com/aspnet/KestrelHttpServer/blob/1.0.0/src/Microsoft.AspNetCore.Server.Kestrel/project.json#L19).

## <a name="how-to-test-libraries-on-net-core"></a>Como testar bibliotecas .NET Core

É importante ser capaz de testar em várias plataformas.  É mais fácil usar o [xUnit](http://xunit.github.io/), que também é a ferramenta de teste usada pelos projetos .NET Core.  A maneira de configurar sua solução com projetos de teste dependerá da [estrutura da sua solução](#structuring-a-solution).  O exemplo a seguir pressupõe que todos os projetos de origem estejam em uma pasta `/src` de nível superior e todos os projetos de teste estejam em uma pasta `/test` de nível superior.

1. Verifique se você tem um arquivo `global.json` no nível da solução que compreende onde estão os projetos de teste:
    
    ```json
    {
        "projects":[ "src", "test"]
    }
    ```
    
    A estrutura de pastas de solução deverá ser semelhante à seguinte:
    
    ```
    /SolutionWithSrcAndTest
    |__global.json
    |__/src
    |__/test
    ```
    
2. Crie um novo projeto de teste em uma pasta de projeto na sua pasta `/test` e um arquivo `project.json` na pasta do novo projeto.  Para criar o arquivo `project.json`, você pode executar o comando `dotnet new` e modificar o arquivo `project.json` posteriormente.  O arquivo deverá ter o seguinte:

   * `netcoreapp1.0` listado como a única entrada em `frameworks`.
   * Uma referência para `Microsoft.NETCore.App` versão `1.0.0`.
   * Uma referência para xUnit versão `2.2.0-beta2-build3300`.
   * Uma referência para `dotnet-test-xunit` versão `2.2.0-preview2-build1029`
   * Uma referência de projeto para a biblioteca que está sendo testada.
   * A entrada `"testRunner":"xunit"`.
   
   Veja este exemplo (`LibraryUnderTest` versão `1.0.0` é a biblioteca que está sendo testada):
   
   ```json
   {
        "testRunner":"xunit",
        "dependencies":{
            "LibraryUnderTest":{
                "version":"1.0.0",
                "target":"project"
            },
            "Microsoft.NETCore.App":{
                "version":"1.0.0",
                "type":"platform"
            },
            "xunit":"2.2.0-beta2-build3300",
            "dotnet-test-xunit":"2.2.0-preview2-build1029",
        },
        "frameworks":{
            "netcoreapp1.0":{}
        }
   }
   ```
3. Restaure os pacotes executando `dotnet restore`.  Você deverá fazer isso no nível da solução se ainda não tiver restaurado os pacotes.

4. Navegue até seu projeto de teste e execute os testes com `dotnet test`:

    ```
    $ cd path-to-your-test-project
    $ dotnet test
    ```

E pronto.  Agora você pode testar sua biblioteca em todas as plataformas usando as ferramentas de linha de comando.  É muito simples testar sua biblioteca agora que está tudo configurado:

1. Faça alterações na sua biblioteca.
2. Execute os testes de linha de comando no diretório de teste com o comando `dotnet test`.

Seu código será recriado automaticamente quando você invoca o comando `dotnet test`.

Lembre-se de executar `dotnet restore` na linha de comando sempre que adicionar uma nova dependência e você estará pronto para começar.

## <a name="how-to-use-multiple-projects"></a>Como usar vários projetos

Uma necessidade comum das bibliotecas grandes é alocar funcionalidades em diferentes projetos.

Imagine que você deseja compilar uma biblioteca que poderia ser consumida em expressões idiomáticas de C# e F#.  Isso significa que os consumidores da sua biblioteca o farão de maneira natural ao C# ou F#.  Por exemplo, você poderia consumir a biblioteca em C# dessa forma:

```csharp
var convertResult = await AwesomeLibrary.ConvertAsync(data);
var result = AwesomeLibrary.Process(convertResult);
```  

No F#, ela poderia assemelhar-se a:

```fsharp
let result =
    data
    |> AwesomeLibrary.convertAsync 
    |> Async.RunSynchronously 
    |> AwesomeLibrary.process
```

Cenários de consumo como esse significam que as APIs que estão sendo acessadas devem ter uma estrutura diferente para C# e F#.  Uma abordagem comum para realizar isso é fatorar toda a lógica de uma biblioteca em um projeto principal, com projetos C# e F# definindo as camadas de API que chamam esse projeto principal.  O restante da seção usará os nomes a seguir:

* **AwesomeLibrary.Core** – Um projeto principal que contém toda a lógica para a biblioteca
* **AwesomeLibrary.CSharp** – Um projeto com APIs públicas destinadas ao consumo em C#
* **AwesomeLibrary.FSharp** – Um projeto com APIs públicas destinadas ao consumo em F#

### <a name="project-to-project-referencing"></a>Referência projeto a projeto

A melhor maneira de fazer referência a um projeto é fazer o seguinte:

1. Verifique se o projeto ao qual que você deseja fazer referência tem um bom nome para a pasta recipiente no disco.  Esse será o nome usado para fazer referência ao seu projeto.
2. Faça referência ao nome de (1) no arquivo `project.json` do projeto de consumo especificando `"target":"project"`.

Os arquivos `project.json` para **AwesomeLibrary.CSharp** e **AwesomeLibrary.FSharp** agora precisam fazer referência a **AwesomeLibrary.Core** como um destino `project`.  Se você não usar multiplataformas, poderá usar a entrada `dependencies` global:

```json
{
    "dependencies":{
        "AwesomeLibrary.Core":{
            "target":"project"
        }
    }
}
```

Se você usar multiplataforma, não poderá usar uma entrada `dependencies` global, sendo necessário fazer referência a **AwesomeLibrary.Core** em uma entrada `dependencies` no nível do destino.  Por exemplo, se você estiver direcionando `netstandard1.6`, poderia fazê-lo dessa forma:

```json
{
    "frameworks":{
        "netstandard1.6":{
            "dependencies":{
                "AwesomeLibrary.Core":{
                    "target":"project"
                }
            }
        }
    }
}
```

### <a name="structuring-a-solution"></a>Estruturando uma solução

Outro aspecto importante das soluções multiprojetos é estabelecer uma boa estrutura de projeto geral. Para estruturar uma biblioteca multiprojetos, você deve usar as pastas `/src` e `/test` de nível superior:

```
/AwesomeLibrary
|__global.json
|__/src
   |__/AwesomeLibrary.Core
      |__Source Files
      |__project.json
   |__/AwesomeLibrary.CSharp
      |__Source Files
      |__project.json
   |__/AwesomeLibrary.FSharp
      |__Source Files
      |__project.json
|__/test
   |__/AwesomeLibrary.Core.Tests
      |__Test Files
      |__project.json
   |__/AwesomeLibrary.CSharp.Tests
      |__Test Files
      |__project.json
   |__/AwesomeLibrary.FSharp.Tests
      |__Test Files
      |__project.json
```

O arquivo `global.json` para essa solução seria semelhante a:

```json
{
    "projects":["src", "test"]
}
```

Essa abordagem segue o mesmo padrão estabelecido pelos modelos de projeto no comando establish do `dotnet new`, em que todos os projetos são colocados em um diretório `/src` e todos os testes são colocados em um diretório `/test`.

Veja a seguir como você pode restaurar, compilar e testar os pacotes de todo o projeto:

```
$ dotnet restore
$ cd src/AwesomeLibrary.FSharp
$ dotnet build
$ cd ../AwesomeLibrary.CSharp
$ dotnet build
$ cd ../../test/AwesomeLibrary.Core.Tests
$ dotnet test
$ cd ../AwesomeLibrary.CSharp.Tests
$ dotnet test
$ cd ../AwesomeLibrary.FSharp.Tests
$ dotnet test
```

E pronto.



<!--HONumber=Nov16_HO4-->


