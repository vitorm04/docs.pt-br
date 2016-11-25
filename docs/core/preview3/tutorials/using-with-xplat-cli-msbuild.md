---
title: "Introdução ao .NET Core no Windows/Linux/macOS usando a linha de comando (Visualização 3 do SDK)"
description: "Introdução ao .NET Core no Windows, Linux ou macOS usando a CLI (Interface de Linha de Comando) do .NET Core"
keywords: .NET, .NET Core
author: cartermp
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: be988f09-7349-43b0-97fb-3a703d4587ce
translationtype: Human Translation
ms.sourcegitcommit: ab71aab99505f211fe4adc86957eda4707761f1c
ms.openlocfilehash: 01b17021e79bcdb2dc69f97b709f4aa63dbab9aa

---

# <a name="getting-started-with-net-core-on-windowslinuxmacos-using-the-command-line-sdk-preview-3"></a>Introdução ao .NET Core no Windows/Linux/macOS usando a linha de comando (Visualização 3 do SDK)

Este guia mostrará como usar as ferramentas de CLI do .NET Core para criar aplicativos de console de plataforma cruzada.  Ele começará com o aplicativo de console mais básico e eventualmente abrangerá vários projetos, incluindo testes. Você adicionará esses recursos passo a passo, avançando com base no que você já viu e criou.

Se você não estiver familiarizado com o conjunto de ferramentas da CLI do .NET Core, leia a [Visão geral do SDK do .NET Core](../tools/dotnet.md).

## <a name="prerequisites"></a>Pré-requisitos

Antes de começar, verifique se você tem as [ferramentas da CLI do .NET Core da Visualização 3 ou posterior](https://github.com/dotnet/core/blob/master/release-notes/preview3-download.md).  Você também precisará de um editor de texto.

## <a name="hello-console-app"></a>Olá, Aplicativo de Console.

Primeiro, procure ou crie uma nova pasta com o nome desejado.  “Hello” é o nome escolhido para o código de exemplo, que pode ser encontrado [aqui](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/HelloMsBuild).

Abra um prompt de comando e digite o seguinte:

```
$ dotnet new
$ dotnet restore
$ dotnet run
```

Vejamos um breve passo a passo:

1. `$ dotnet new`

   [`dotnet new`](../tools/dotnet-new.md) cria um arquivo de projeto `Hello.csproj` atualizado com as dependências necessárias para criar um aplicativo de console.  Ele também cria um `Program.cs`, um arquivo básico que contém o ponto de entrada para o aplicativo.
   
   `Hello.csproj`:
   ```xml
    <Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
        <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />
        
        <PropertyGroup>
            <OutputType>Exe</OutputType>
            <TargetFramework>netcoreapp1.0</TargetFramework>
        </PropertyGroup>

        <ItemGroup>
            <Compile Include="**\*.cs" />
            <EmbeddedResource Include="**\*.resx" />
        </ItemGroup>

        <ItemGroup>
            <PackageReference Include="Microsoft.NETCore.App">
                <Version>1.0.1</Version>
            </PackageReference>
            <PackageReference Include="Microsoft.NET.Sdk">
                <Version>1.0.0-alpha-20161104-2</Version>
                <PrivateAssets>All</PrivateAssets>
            </PackageReference>
        </ItemGroup>
        
        <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
    </Project>
   ```

   O arquivo de projeto especifica tudo o que é necessário para restaurar as dependências e compilar o programa.

   * A marca `Import` traz algumas propriedades que são comuns a todos os projetos do .NET Core.
   * A marca `OutputType` especifica que estamos copilando um executável, em outras palavras, um aplicativo de console.
   * A marca `TargetFramework` especifica o tempo de execução do .NET que estamos direcionando. Em um cenário avançado, você pode especificar várias estruturas de destino e compilar todos eles em uma única operação. Neste tutorial, veremos apenas a compilação para .NET Core 1.0.
   * A marca `Compile` informa ao compilador que ele deve compilar todos os arquivos no diretório atual e todos os seus subdiretórios que têm a extensão de arquivo `.cs`, em outras palavras, todas os arquivos C# no projeto. Em cenários avançados, é possível excluir arquivos, mas neste tutorial e na maioria dos cenários simples, essa linha pode ser deixada inalterada.
   * A marca `EmbeddedResource` instrui o sistema de build a inserir arquivos de localização com a extensão `.resx` para o executável compilado. Não usaremos esse recurso neste tutorial.
   * As marcas `PackageReference` especificam quais pacotes de dependência devem ser restaurados e incluídos ao compilar o aplicativo. Cada referência de pacote especifica o nome do pacote sob o atributo `Include` e um número de versão. Em cenários mais avançados, é possível adicionar mais referências de pacote. Também é possível fazer referência a outros projetos no disco.

   `Program.cs`:
   ```csharp
   using System;

   namespace ConsoleApplication
   {
       public class Program
       {
           public static void Main(string[] args)
           {
               Console.WriteLine("Hello World!");
           }
       }
   }
   ```

   O programa é iniciado pelo `using System`, que significa "colocar tudo no namespace `System` no escopo para este arquivo". O namespace `System` inclui construções básicas, como `string` ou tipos numéricos.

   Em seguida, define-se um namespace chamado "ConsoleApplication". Você pode alterar isso de acordo com a sua vontade. Uma classe chamada "Programa" é definida dentro desse namespace, com um método `Main` que usa uma matriz de cadeias de caracteres como argumento. Essa matriz conterá a lista de argumentos passados quando o programa compilado for chamado. Assim, essa matriz não será usada: o que o programa faz é gravar: "Hello World!" no console. Podemos tornar as coisas um pouco mais interessantes alterando o `Console.WriteLine` para o código a seguir.

   ```csharp
   if (args.Length > 0)
   {
       Console.WriteLine($"Hello {args[0]}!");
   }
   else
   {
       Console.WriteLine("Hello World!");
   }
   ```

2. `$ dotnet restore`

   [`dotnet restore`](../tools/dotnet-restore.md) chama o [NuGet](http://nuget.org) para restaurar a árvore de dependências. O NuGet analisa o arquivo `Hello.csproj`, baixa as dependências declaradas no arquivo (ou captura-as de um cache em seu computador) e grava o arquivo `obj/project.assets.json`.  O arquivo `project.assets.json` é necessário para compilação e execução.
   
   O arquivo `project.assets.json` é um conjunto completo e persistente do gráfico de dependências do NuGet e outras informações que descrevem um aplicativo.  Esse arquivo é lido por outras ferramentas, tal como `dotnet build` e `dotnet run`, permitindo que elas processem o código-fonte com um conjunto correto das dependências do NuGet e resoluções de associação.
   
3. `$ dotnet run`

   [`dotnet run`](../tools/dotnet-run.md) chama `dotnet build` para garantir que os destinos de build foram criados e então chama `dotnet <assembly.dll>` para executar o aplicativo de destino.
   
    ```
    $ dotnet run
    Hello World!
    ```

    Como alternativa, também é possível pode executar [`dotnet build`](../tools/dotnet-build.md) para compilar o código sem executar os aplicativos de console de compilação. Isso resulta em um aplicativo compilado `bin/Debug/netcoreapp1.0/Hello.dll` que pode ser executado com `dotnet bin\Debug\netcoreapp1.0\Hello.dll` no Windows e com `dotnet bin/Debug/netcoreapp1.0/Hello.dll` em outros sistemas. É possível especificar um parâmetro adicional na linha de comando (supondo que você está no Windows):

    ```
    $ dotnet bin\Debug\netcoreapp1.0\Hello.dll .NET
    Hello .NET!
    ```

    Como um cenário avançado, é possível compilar o aplicativo como um conjunto independente de arquivos específicos de plataforma que pode ser implantado e executado em um computador que não tem necessariamente o .NET Core instalado. Consulte [Implantação do .NET Core Application](../deploying/index.md) para obter mais informações.

### <a name="augmenting-the-program"></a>Ampliando o programa

Vamos alterar o arquivo um pouco.  Números Fibonacci são divertidos, por isso, vamos experimentá-los:

`Program.cs`:

```csharp
using static System.Console;

namespace ConsoleApplication
{
    public class Program
    {
        public static int FibonacciNumber(int n)
        {
            int a = 0;
            int b = 1;
            int tmp;
            
            for (int i = 0; i < n; i++)
            {
                tmp = a;
                a = b;
                b += tmp;
            }
            
            return a;   
        }
        
        public static void Main(string[] args)
        {
            WriteLine("Hello World!");
            WriteLine("Fibonacci Numbers 1-15:");
            
            for (int i = 0; i < 15; i++)
            {
                WriteLine($"{i+1}: {FibonacciNumber(i)}");
            }
        }
    }
}
```

E executar o programa (supondo que você está no Windows e alterou o nome do diretório de projeto para Fibonacci):

```
$ dotnet build
$ dotnet bin\Debug\netcoreapp1.0\win10-x64\Fibonacci.exe
1: 0
2: 1
3: 1
4: 2
5: 3
6: 5
7: 8
8: 13
9: 21
10: 34
11: 55
12: 89
13: 144
14: 233
15: 377
```

E pronto.  Você pode ampliar `Program.cs` como desejar.

## <a name="adding-some-new-files"></a>Adicionando alguns arquivos novos

Arquivos individuais são adequados para programas únicos simples, porém você provavelmente vai dividir as coisas em vários arquivos se estiver criando qualquer coisa com vários componentes.  Uma maneira de fazer isso é usar vários arquivos.

Crie um novo arquivo e dê a ele um namespace exclusivo:

```csharp
using System;

namespace NumberFun
{
    // code can go here
} 
```

Em seguida, inclua-o no seu arquivo `Program.cs`:

```csharp
using NumberFun;
```

E, por fim, você pode compilar:

`$ dotnet build`

Agora vem a parte divertida: fazer com que o novo arquivo faça alguma coisa!

### <a name="example-a-fibonacci-sequence-generator"></a>Exemplo: um gerador de sequência de Fibonacci

Digamos que você deseja expandir o exemplo de Fibonacci anterior armazenando em cache alguns valores de Fibonacci e adicionando um toque recursivo.  Seu código para um [exemplo melhor de Fibonacci](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/FibonacciBetterMsBuild) pode usar um novo arquivo `FibonacciGenerator.cs` pelo código a seguir.

```csharp
using System;
using System.Collections.Generic;

namespace NumberFun
{
    public class FibonacciGenerator
    {
        private Dictionary<int, int> _cache = new Dictionary<int, int>();
        
        private int Fib(int n) => n < 2 ? n : FibValue(n - 1) + FibValue(n - 2);
        
        private int FibValue(int n)
        {
            if (!_cache.ContainsKey(n))
            {
                _cache.Add(n, Fib(n));
            }
            
            return _cache[n];
        }
        
        public IEnumerable<int> Generate(int n)
        {
            for (int i = 0; i < n; i++)
            {
                yield return FibValue(i);
            }
        }
    }
}
```

Agora, ajuste o método `Main()` no seu arquivo `Program.cs` conforme mostrado abaixo.

```csharp
using System;
using NumberFun;

class Program
{
    static void Main(string[] args)
    {
        var generator = new FibonacciGenerator();
        foreach (var digit in generator.Generate(15))
        {
            Console.WriteLine(digit);
        }
    }
}
```

Por fim, execute-o.

```
$ dotnet run
0
1
1
2
3
5
8
13
21
34
55
89
144
233
377
```

E pronto.

## <a name="conclusion"></a>Conclusão
 
Esperamos que esse guia tenha ajudado você a aprender como criar um aplicativo de console .NET Core, desde os princípios básicos até um sistema multiprojeto com testes de unidade.  A próxima etapa é criar seus próprios aplicativos de console incríveis.
 
Se um exemplo mais avançado de um aplicativo de console lhe interessa, consulte o próximo tutorial: [Organizar e testar projetos com a linha de comando do .NET Core (Visualização 3 do SDK)](using-with-xplat-cli-msbuild-folders.md).



<!--HONumber=Nov16_HO3-->


