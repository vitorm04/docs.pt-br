---
title: "Introdução ao .NET Core no Windows/Linux/macOS usando a linha de comando"
description: "Introdução ao .NET Core no Windows, Linux ou macOS usando a CLI (Interface de Linha de Comando) do .NET Core"
keywords: .NET, .NET Core
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: be988f09-7349-43b0-97fb-3a703d4587ce
translationtype: Human Translation
ms.sourcegitcommit: 37e14d5cdf1593f6a8b1ecee9d9828647b023548
ms.openlocfilehash: 5493ccb77e62d20d5101728ef8ab1744ea697fb8

---

# <a name="getting-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a>Introdução ao .NET Core no Windows/Linux/macOS usando a linha de comando

Este guia mostrará como usar as ferramentas de CLI do .NET Core para criar aplicativos de console básicos de plataforma cruzada.

Se você não estiver familiarizado com o conjunto de ferramentas da CLI do .NET Core, leia a [Visão geral do SDK do .NET Core](../sdk.md).

## <a name="prerequisites"></a>Pré-requisitos

Antes de começar, verifique se você tem as [ferramentas da CLI do .NET Core mais recentes](https://www.microsoft.com/net/core). Você também precisará de um editor de texto.

## <a name="hello-console-app"></a>Olá, Aplicativo de Console.

Navegue até ou crie uma nova pasta com o nome desejado. “Hello” é o nome escolhido para o código de exemplo, que pode ser encontrado [aqui](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/Hello).

Abra um prompt de comando e digite o seguinte:

```
$ dotnet new
$ dotnet restore
$ dotnet run
```

Vejamos um breve passo a passo:

1. `$ dotnet new`

   [`dotnet new`](../tools/dotnet-new.md) cria um arquivo `project.json` atualizado com dependências NuGet necessárias para criar um aplicativo de console.  Ele também cria um `Program.cs`, um arquivo básico que contém o ponto de entrada para o aplicativo.
   
   `project.json`:
   ```json
   {
        "version": "1.0.0-*",
        "buildOptions": {
            "emitEntryPoint": true
        },
        "dependencies": {
            "Microsoft.NETCore.App": {
                "type": "platform",
                "version": "1.0.0"
            }
        },   
       "frameworks": {
            "netcoreapp1.0": {
                "imports": "dnxcore50"
            }
        }
   }
   ```
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

2. `$ dotnet restore`

   [`dotnet restore`](../tools/dotnet-restore.md) chamadas o NuGet para restaurar a árvore de dependências. O NuGet analisa o arquivo `project.json`, baixa as dependências declaradas no arquivo (ou captura-as de um cache em seu computador) e grava o arquivo `project.lock.json`.  O arquivo `project.lock.json` é necessário para compilação e execução.
   
   O arquivo `project.lock.json` é um conjunto completo e persistente do gráfico de dependências do NuGet e outras informações que descrevem um aplicativo.  Esse arquivo é lido por outras ferramentas, tal como `dotnet build` e `dotnet run`, permitindo que elas processem o código-fonte com um conjunto correto das dependências do NuGet e resoluções de associação.
   
3. `$ dotnet run`

   [`dotnet run`](../tools/dotnet-run.md) chama `dotnet build` para garantir que os destinos de build foram criados e então chama `dotnet <assembly.dll>` para executar o aplicativo de destino.
   
```
$ dotnet run
Hello, World!
```

Você também pode executar [`dotnet build`](../tools/dotnet-build.md) para compilar o código sem executar os aplicativos de console de compilação.

### <a name="building-a-self-contained-application"></a>Criando um aplicativo autocontido

Vamos experimentar compilar um aplicativo autocontido em vez de portátil. Você pode ler mais sobre os [tipos de portabilidade no .NET Core](../deploying/index.md) para saber mais sobre os diferentes tipos de aplicativos e como eles são implantados.

Você precisa fazer algumas alterações no seu arquivo `project.json` para direcionar as ferramentas para compilar um aplicativo autocontido. Você pode ver isso no projeto [HelloNative](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/HelloNative) no diretório de exemplos.

A primeira alteração é remover o elemento `"type": "platform"` de todas as dependências. A única dependência desse projeto até o momento é `"Microsoft.NETCore.App"`. A seção `dependencies` deve se parecer com essa:

```json
"dependencies": {
    "Microsoft.NETCore.App": {
        "version": "1.0.0"
    }
},
```

Em seguida, você precisa adicionar um nó `runtimes` para especificar todos os ambientes de execução de destino. Por exemplo, o nó `runtimes` a seguir instrui o sistema de build a criar executáveis para a versão de 64 bits do Windows 10 e a versão de 64 bits do Mac OS X versão 10.11.
O sistema de build gerará executáveis nativos para o ambiente atual. Se estiver seguindo estas etapas em um computador Windows, você criará um executável do Windows. Se estiver seguindo etapas em um Mac, você criará um executável do OS X.

```json 
"runtimes": {
  "win10-x64": {},
  "osx.10.11-x64": {}
}
```

Consulte a lista completa de tempos de execução com suporte no [Catálogo RID](../rid-catalog.md). 
 
Depois de fazer essas duas alterações, você executará `dotnet restore` seguido por `dotnet build` para criar o executável nativo. Em seguida, você pode ativar o executável nativo gerado. 

O exemplo a seguir mostra os comandos do Windows. O exemplo mostra onde o executável nativo é gerado e supõe que o diretório de projeto seja denominado HelloNative.

```
$ dotnet restore 
$ dotnet build 
$ .\bin\Debug\netcoreapp1.0\win10-x64\HelloNative.exe
Hello World!
```

Você pode perceber que o aplicativo nativo demora ligeiramente mais para ser compilado, porém é executado um pouco mais rápido. Esse comportamento se torna mais perceptível à medida que o aplicativo cresce.

O processo de compilação gera vários outros arquivos quando seu `project.json` cria um build nativo. Esses arquivos são criados no `bin\Debug\netcoreapp1.0\<platform>`, em que `<platform>` é o RID escolhido. Além do `HelloNative.dll` do projeto, há um `HelloNative.exe` que carrega o tempo de execução e inicia o aplicativo.
Observe que o nome do aplicativo gerado mudou porque o nome do diretório do projeto foi alterado.  

Pode ser recomendável empacotar esse aplicativo para executá-lo em um computador que não inclua o tempo de execução do .NET.
Você fazer isso usando o comando `dotnet publish`. O comando `dotnet publish` cria um novo subdiretório no diretório `./bin/Debug/netcoreapp1.0/<platform>` chamado `publish`. Ele copia o executável, todas as DLLs dependentes e a estrutura para esse subdiretório. Você pode empacotar esse diretório para outro computador (ou para um contêiner) e executar o aplicativo nele. 

Vamos comparar isso com o comportamento de `dotnet publish` no primeiro exemplo do Hello World. Esse aplicativo é um *aplicativo portátil*, que é o tipo padrão de aplicativo para .NET Core. Um aplicativo portátil requer que o .NET Core esteja instalado no computador de destino. Aplicativos portáteis podem ser compilados em um computador e executados em qualquer lugar. Aplicativos nativos devem ser compilados separadamente para cada computador de destino. `dotnet publish` cria um diretório que tem a DLL do aplicativo e todas as dlls dependentes que não fazem parte da instalação da plataforma.

### <a name="augmenting-the-program"></a>Ampliando o programa

Vamos alterar o arquivo um pouco.  Números Fibonacci são divertidos, por isso experimentá-los (usando a versão nativa):

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
$ .\bin\Debug\netcoreapp1.0\win10-x64\Fibonacci.exe
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
using static System.Console;
using NumberFun;
```

E, por fim, você pode compilar:

`$ dotnet build`

Agora vem a parte divertida: fazer com que o novo arquivo faça alguma coisa!

### <a name="example-a-fibonacci-sequence-generator"></a>Exemplo: um gerador de sequência de Fibonacci

Digamos que você deseja expandir o [exemplo de Fibonacci](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/Fibonacci) anterior armazenando em cache alguns valores de Fibonacci e adicionando um toque recursivo.  Seu código para um [exemplo de Fibonacci melhor](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/FibonacciBetter) pode assemelhar-se a este:

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

Observe que usar `Dictionary<int, int>` e `IEnumerable<int>` significa incorporar o namespace `System.Collections`.
O pacote `Microsoft.NetCore.App` é um *metapacote* que contém muitos dos assemblies principais do .NET Framework. Ao incluir esse metapacote, você já incluiu o assembly `System.Collections.dll` como parte do seu projeto. Você pode verificar isso executando `dotnet publish` e examinando os arquivos que fazem parte do pacote instalado. Você verá `System.Collections.dll` na lista. 

```json
{ 
  "version": "1.0.0-*", 
  "buildOptions": { 
    "debugType": "portable", 
    "emitEntryPoint": true 
  }, 
  "dependencies": {}, 
  "frameworks": { 
    "netcoreapp1.0": { 
      "dependencies": { 
        "Microsoft.NETCore.App": { 
          "version": "1.0.0" 
        } 
      }, 
      "imports": "dnxcore50" 
    } 
  },
  "runtimes": {
    "win10-x64": {},
    "osx.10.11-x64": {}
  }
}
```

Agora, ajuste o método `Main()` no seu arquivo `Program.cs` conforme mostrado abaixo. O exemplo supõe que `Program.cs` tem uma instrução `using System;`. Se você tiver uma instrução `using static System.Console;`, remova `Console.` do `Console.WriteLine`.  

```csharp
public static void Main(string[] args)
{
    var generator = new FibonacciGenerator();
    foreach (var digit in generator.Generate(15))
    {
        WriteLine(digit);
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

## <a name="using-folders-to-organize-code"></a>Usar pastas para organizar o código

Digamos que você deseja apresentar alguns novos tipos para trabalhar.  Você pode fazer isso adicionando mais arquivos e verificando se eles receberam namespaces que você pode incluir no arquivo `Program.cs`.

```
/MyProject
|__Program.cs
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__project.json
```

Isso funciona muito bem quando o tamanho do projeto é relativamente pequeno.  No entanto, se você tiver um aplicativo maior com vários tipos de dados diferentes e possivelmente várias camadas, poderá ser recomendável organizar as coisas de maneira lógica.  É nesse momento que as pastas entram em cena.  Você pode acompanhar [o projeto de exemplo NewTypes](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/NewTypes) que este guia aborda ou criar seus próprios arquivos e pastas.

Para começar, crie uma nova pasta na raiz do seu projeto.  `/Model` é escolhido aqui.

```
/NewTypes
|__/Model
|__Program.cs
|__project.json
```

Agora adicione alguns novos tipos à pasta:

```
/NewTypes
|__/Model
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__Program.cs
|__project.json
```

Agora, da mesma forma que faria com arquivos no mesmo diretório, conceda a todos eles o mesmo namespace para que você possa incluí-los no seu `Program.cs`.

### <a name="example-pet-types"></a>Exemplo: Tipos de animais de estimação

Esse exemplo cria dois novos tipos, `Dog` e `Cat`, e faz com que eles implementem uma interface, `IPet`.

Estrutura de Pastas:

```
/NewTypes
|__/Pets
   |__Dog.cs
   |__Cat.cs
   |__IPet.cs
|__Program.cs
|__project.json
```

`IPet.cs`:
```csharp
using System;

namespace Pets
{
    public interface IPet
    {
        string TalkToOwner();
    }
}
```

`Dog.cs`:
```csharp
using System;

namespace Pets
{
    public class Dog : IPet
    {
        public string TalkToOwner() => "Woof!";
    }
}
```

`Cat.cs`:
```csharp
using System;

namespace Pets
{
    public class Cat : IPet
    {
        public string TalkToOwner() => "Meow!";
    }
}
```

`Program.cs`:
```csharp
using System;
using Pets;
using System.Collections.Generic;

namespace ConsoleApplication
{
    public class Program
    {
        public static void Main(string[] args)
        {
            List<IPet> pets = new List<IPet>
            {
                new Dog(),
                new Cat()  
            };
            
            foreach (var pet in pets)
            {
                Console.WriteLine(pet.TalkToOwner());
            }
        }
    }
}
```

`project.json`:
```json
{
  "version": "1.0.0-*",
  "buildOptions": {
    "emitEntryPoint": true
  },
  "dependencies": {
    "Microsoft.NETCore.App": {
      "type": "platform",
      "version": "1.0.0"
    }
  },
  "frameworks": {
    "netcoreapp1.0": {
      "imports": "dnxcore50"
    }
  }
}
```

E se você executar isso:

```
$ dotnet restore
$ dotnet run
Woof!
Meow!
```

É possível adicionar novos tipos de animais de estimação (como um `Bird`), estendendo esse projeto.

## <a name="testing-your-console-app"></a>Testando seu Aplicativo de Console

Você provavelmente vai querer testar seus projetos em algum momento.  Aqui está uma boa maneira de fazer isso:

1. Mova o código-fonte do seu projeto existente para uma nova pasta `src`.

   ```
   /Project
   |__/src
   ```

2. Crie um diretório `/test`.

   ```
   /Project
   |__/src
   |__/test
   ```

3. Crie um novo arquivo `global.json`:

   ```
   /Project
   |__/src
   |__/test
   |__global.json
   ```

   `global.json`:
   ```json
   {
      "projects": [
         "src", "test"
      ]
   }
   ```

   Este arquivo informa o sistema de build que este é um sistema multiprojetos, permitindo-o procurar por dependências além da pasta atual na qual ele é executado.  Isso é importante, porque permite colocar uma dependência no código em teste no seu projeto de teste.
   
### <a name="example-extending-the-newtypes-project"></a>Exemplo: Estendendo o projeto NewTypes

Agora que o sistema do projeto está em vigor, você pode criar seu projeto de teste e começar a escrever testes.  A partir daqui, este guia usará e estenderá [o projeto Types de exemplo](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/NewTypes).  Além disso, ele usará a estrutura de teste do [Xunit](https://xunit.github.io/).  Fique à vontade para acompanhá-lo ou criar seu próprio sistema multiprojeto com testes.


A estrutura de todo o projeto deve assemelhar-se a:

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__project.json
|__/test
   |__NewTypesTests
      |__PetTests.cs
      |__project.json
|__global.json
```

Há duas coisas que você precisa ter no seu projeto de teste:

1. Um `project.json` correto com o seguinte:

   * Uma referência a `xunit`
   * Uma referência a `dotnet-test-xunit`
   * Uma referência para o namespace correspondente ao código em teste

2. Uma classe de teste Xunit.

`NewTypesTests/project.json`:
```json
{
  "version": "1.0.0-*",
  "testRunner": "xunit",

  "dependencies": {
    "Microsoft.NETCore.App": {
      "type":"platform",
      "version": "1.0.0"
    },
    "xunit":"2.2.0-beta2-build3300",
    "dotnet-test-xunit": "2.2.0-preview2-build1029",
    "NewTypes": "1.0.0"
  },
  "frameworks": {
    "netcoreapp1.0": {
      "imports": [
        "dnxcore50",
        "portable-net45+win8" 
      ]
    }
  }
}
```

`PetTests.cs`: 
```csharp
using System;
using Xunit;
using Pets;
public class PetTests
{
    [Fact]
    public void DogTalkToOwnerTest()
    {
        string expected = "Woof!";
        string actual = new Dog().TalkToOwner();
        
        Assert.Equal(expected, actual);
    }
    
    [Fact]
    public void CatTalkToOwnerTest()
    {
        string expected = "Meow!";
        string actual = new Cat().TalkToOwner();
        
        Assert.Equal(expected, actual);
    }
}
```
   
Agora você pode executar testes.  O comando [`dotnet test`](../tools/dotnet-test.md) executa o executor de teste que você especificou no seu projeto. Lembre-se de iniciar pelo diretório de nível superior.
 
```
$ dotnet restore
$ cd test/NewTypesTests
$ dotnet test
```
 
A saída deve ser semelhante a esta:
 
```
xUnit.net .NET CLI test runner (64-bit win10-x64)
  Discovering: NewTypesTests
  Discovered:  NewTypesTests
  Starting:    NewTypesTests
  Finished:    NewTypesTests
=== TEST EXECUTION SUMMARY ===
   NewTypesTests  Total: 2, Errors: 0, Failed: 0, Skipped: 0, Time: 0.144s
SUMMARY: Total: 1 targets, Passed: 1, Failed: 0.
```
 
## <a name="conclusion"></a>Conclusão
 
Esperamos que esse guia tenha ajudado você a aprender como criar um aplicativo de console .NET Core, desde os princípios básicos até um sistema multiprojeto com testes de unidade.  A próxima etapa é criar seus próprios aplicativos de console incríveis.
 
Se você tiver interesse em um exemplo avançado de um aplicativo de console, confira o próximo tutorial: [Usando as ferramentas da CLI para escrever aplicativos de console: um guia passo a passo avançado](cli-console-app-tutorial-advanced.md).



<!--HONumber=Nov16_HO4-->


