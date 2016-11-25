---
title: "Implantação do .NET Core Application"
description: "Implantação do .NET Core Application"
keywords: "Implantação do .NET e .NET Core"
author: rpetrusha
manager: wpickett
ms.date: 09/08/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: da7a31a0-8072-4f23-82aa-8a19184cb701
translationtype: Human Translation
ms.sourcegitcommit: 663f4102b82512e64ab39d8046c7298a7cf37de7
ms.openlocfilehash: 5509f09b3f7957049194ea7af9952bb6b5ec7539

---

# <a name="net-core-application-deployment"></a>Implantação do .NET Core Application #

Você pode criar dois tipos de implantações de aplicativos do .NET Core: 

- Implantação dependente de estrutura. Como o nome implica, a FDD (implantação dependente de estrutura) se baseia em uma versão compartilhada em todo o sistema do .NET Core para existir no sistema de destino. Como o .NET Core já está presente, seu aplicativo também é portátil entre instalações do .NET Core. Seu aplicativo conterá somente seu próprio código e as dependências de terceiros que estiverem fora de bibliotecas .NET Core. FDDs contêm arquivos .dll que podem ser iniciados usando o [utilitário dotnet](../tools/dotnet.md) da linha de comando. Por exemplo, `dotnet app.dll` executa um aplicativo chamado `app`.

- Implantação autocontida. Diferentemente da FDD, a SDC (implantação autocontida) não se baseia em nenhum componente compartilhado para existir no sistema de destino. Todos os componentes, incluindo bibliotecas e tempo de execução .NET Core, são incluídos com o aplicativo e isolados de outros aplicativos .NET Core. SCDs incluem um arquivo executável (como o `app.exe` em plataformas Windows para um aplicativo chamado `app`), que é uma versão renomeada de host específico da plataforma .NET Core e um arquivo .dll (como `app.dll`), que é o aplicativo real.

## <a name="framework-dependent-deployments-fdd"></a>FDD (implantação dependente de estrutura) ##

Para uma FDD, seu aplicativo é implantado apenas em dependências de terceiros. Você não precisa implantar o .NET Core, pois seu aplicativo usará a versão do .NET Core presente no sistema de destino. Este é o modelo de implantação padrão para aplicativos .NET Core.

### <a name="why-create-a-framework-dependent-deployment"></a>Por que criar uma implantação dependente de estrutura? ###

Implantar uma FDD traz uma série de vantagens:

- Você não precisa definir previamente em quais sistemas operacionais de destino seu aplicativo .NET Core será executado. Como o .NET Core usa um formato comum de arquivo PE comum para executáveis e bibliotecas independentemente do sistema operacional, ele pode executar seu aplicativo independentemente do sistema operacional subjacente. Para obter mais informações sobre o formato de arquivo PE, consulte [Formato de Arquivo do Assembly .NET](../../standard/assembly-format.md).

- O tamanho do seu pacote de implantação é pequeno. Você precisa implantar seu aplicativo e suas dependências, não o .NET Core em si.

- Vários aplicativos usam a mesma instalação do .NET Core, o que reduz o uso de memória e espaço em disco nos sistemas host.

Contudo, também há algumas desvantagens:

- Seu aplicativo poderá ser executado somente se a versão do .NET Core de destino, ou uma versão posterior, já estiver instalada no sistema host.

- É possível que o tempo de execução e bibliotecas do .NET Core sejam alteradas sem seu conhecimento em versões futuras. Em casos raros, isso pode alterar o comportamento do seu aplicativo.

### <a name="deploying-a-framework-dependent-deployment"></a>Implantando uma implantação dependente de estrutura ###

Implantar uma implantação dependente de estrutura sem dependências de terceiros significa simplesmente compilar, testar e publicar o aplicativo. Um exemplo simples criado em C# ilustra o processo. O exemplo usa o [utilitário dotnet](../tools/dotnet.md) da linha de comando; no entanto, você também pode usar um ambiente de desenvolvimento, como o Visual Studio ou o Visual Studio Code, para compilar, testar e publicar o exemplo.

1. Crie um diretório para seu projeto e, da linha de comando, digite [dotnet new](../tools/dotnet-new.md) para criar um novo projeto de console em C#.

2. Abra o arquivo `Program.cs` em um editor e substitua o código gerado automaticamente pelo código a seguir. Ele solicitará que o usuário insira texto e exibirá as palavras individuais inseridas pelo usuário. Ele usa a expressão regular `\w+` para separar as palavras no texto de entrada.

    ```cs
    using System;
    using System.Text.RegularExpressions;

    namespace Applications.ConsoleApps
    {
        public class ConsoleParser
        {
            public static void Main()
            {
                 Console.WriteLine("Enter any text, followed by <Enter>:\n");
                 String s = Console.ReadLine();
                 ShowWords(s);
                 Console.Write("\nPress any key to continue... ");
                 Console.ReadKey();
          }

          private static void ShowWords(String s)
          {
              String pattern = @"\w+";
              var matches = Regex.Matches(s, pattern);
              if (matches.Count == 0)
                  Console.WriteLine("\nNo words were identified in your input.");
              else
              {
                  Console.WriteLine("\nThere are {0} words in your string:", matches.Count);
                  for (int ctr = 0; ctr < matches.Count; ctr++)
                      Console.WriteLine("   #{0,2}: '{1}' at position {2}", ctr,
                                        matches[ctr].Value, matches[ctr].Index);
              }
          }
      }
    }
    ```

3. Execute o comando [dotnet restore](../tools/dotnet-restore.md) para restaurar as dependências especificadas em seu projeto.

4. Crie uma versão de depuração do seu aplicativo usando o comando [dotnet build](../tools/dotnet-build.md).

5. Depois de ter depurado e testado o programa, você poderá criar os arquivos a serem implantados com seu aplicativo usando o comando `dotnet publish -f netcoreapp1.0 -c release`. Isso cria uma versão de lançamento (em vez de depuração) do seu aplicativo.

   Os arquivos resultantes são colocados em um diretório chamado `publish` que está em um subdiretório `.\bin\release\netcoreapp1.0` do seu projeto.

6. Junto com os arquivos do aplicativo, o processo de publicação emite um arquivo de banco de dados do programa (.pdb) que contém informações de depuração sobre seu aplicativo. O arquivo é útil principalmente para depurar exceções. Você pode optar por não empacotá-lo com arquivos do aplicativo.

O conjunto completo de arquivos de aplicativo pode ser implantado como você desejar. Por exemplo, você pode empacotá-las em um arquivo zip, usar um simples comando `copy` ou implantá-los com qualquer pacote de instalação de sua escolha.

Além dos binários do aplicativo, o instalador deverá também agrupar o instalador da estrutura compartilhada ou procurar por ele como um pré-requisito como parte da instalação do aplicativo.  A instalação da estrutura compartilhada requer acesso de Administrador/raiz, pois se trata de todo o computador.

### <a name="deploying-a-framework-dependent-deployment-with-third-party-dependencies"></a>Implantando uma implantação dependente de estrutura com dependências de terceiros ###

Implantar uma implantação dependentes de estrutura com uma ou mais dependências de terceiros envolve três etapas adicionais antes de executar o comando `dotnet restore`:

1. Adicione referências a quaisquer bibliotecas de terceiros à seção `dependencies` de seu arquivo `project.json`. A seção `dependencies` a seguir usa Json.NET como uma biblioteca de terceiros.

    ```json
    "dependencies": {
      "Microsoft.NETCore.App": {
        "type": "platform",
        "version": "1.0.0"
      },
      "Newtonsoft.Json": "9.0.1"
    },
    ```

2. Se você ainda não o fez, baixe o pacote NuGet contendo a dependência de terceiros. Para baixar o pacote, execute o comando `dotnet restore` depois de adicionar a dependência. Como a dependência é resolvida fora do cache local do NuGet no momento da publicação, ela deve estar disponível no seu sistema.

Observe que uma implantação dependente de estrutura com dependências de terceiros terá a mesma portabilidade que suas dependências de terceiros. Por exemplo, se uma biblioteca de terceiros dá suporte apenas a macOS, o aplicativo não será portátil para sistemas Windows. Isso pode acontecer se a dependência de terceiros em si depender do código nativo. Um bom exemplo disso é o servidor Kestrel. Quando uma FDD é criada para um aplicativo com esse tipo de dependência de terceiros, a saída publicada conterá uma pasta para cada [RID (Identificador de Tempo de Execução)](../rid-catalog.md#what-are-rids) que dá suporte a dependência nativa (e que existe em seu pacote NuGet).

## <a name="self-contained-deployments-scd"></a>SCD (implantação autocontida) ##

Para uma implantação autocontida, você pode implantar não apenas seu aplicativo e dependências de terceiros, mas a versão do .NET Core com a qual você criou seu aplicativo. No entanto, a criação de uma SCD não inclui as próprias [dependências nativas do .NET Core](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) em várias plataformas (por exemplo, OpenSSL no macOS) por isso elas precisam ser instaladas antes de executar o aplicativo. 

### <a name="why-deploy-a-self-contained-deployment"></a>Por que implantar uma implantação autocontida? ###

Implantar uma implantação autocontida apresenta duas vantagens principais:

- Você tem controle exclusivo sobre a versão do .NET Core que é implantada com seu aplicativo. A manutenção do .NET Core só pode ser feita por você.

- É possível ter certeza de que o sistema de destino pode executar seu aplicativo .NET Core, visto que você está fornecendo a versão do .NET Core na qual ele é executado.

Ela também apresenta algumas desvantagens:

- Como o .NET Core é incluído no seu pacote de implantação, você deve selecionar previamente as plataformas de destino para as quais você criará pacotes de implantação.

- O tamanho do seu pacote de implantação é relativamente grande, visto que você precisa incluir o .NET Core, bem como seu aplicativo e suas dependências de terceiros.

- Implantar vários aplicativos .NET Core autocontidos em um sistema pode consumir um volume significativo de espaço em disco, visto que cada aplicativo duplica os arquivos do .NET Core.

### <a name="a-namesimpleselfa-deploying-a-simple-self-contained-deployment"></a><a name="simpleSelf"></a> Implantando uma implantação autocontida simples ###

Implantar uma implantação autocontida sem dependências de terceiros inclui a criação do projeto, modificação do arquivo project.json, compilação, testes e publicação do aplicativo.  Um exemplo simples criado em C# ilustra o processo. O exemplo usa o utilitário `dotnet` da linha de comando; no entanto, você também pode usar um ambiente de desenvolvimento, como o Visual Studio ou o Visual Studio Code, para compilar, testar e publicar o exemplo.

1. Crie um diretório para seu projeto e, da linha de comando, digite `dotnet new` para criar um novo projeto de console em C#.

2. Abra o arquivo `Program.cs` em um editor e substitua o código gerado automaticamente pelo código a seguir. Ele solicitará que o usuário insira texto e exibirá as palavras individuais inseridas pelo usuário. Ele usa a expressão regular `\w+` para separar as palavras no texto de entrada.

    ```cs
    using System;
    using System.Text.RegularExpressions;

    namespace Applications.ConsoleApps
    {
        public class ConsoleParser
        {
            public static void Main()
            {
                 Console.WriteLine("Enter any text, followed by <Enter>:\n");
                 String s = Console.ReadLine();
                 ShowWords(s);
                 Console.Write("\nPress any key to continue... ");
                 Console.ReadKey();
          }

          private static void ShowWords(String s)
          {
              String pattern = @"\w+";
              var matches = Regex.Matches(s, pattern);
              if (matches.Count == 0)
                  Console.WriteLine("\nNo words were identified in your input.");
              else {
                  Console.WriteLine("\nThere are {0} words in your string:", matches.Count);
                  for (int ctr = 0; ctr < matches.Count; ctr++)
                      Console.WriteLine("   #{0,2}: '{1}' at position {2}", ctr,
                                        matches[ctr].Value, matches[ctr].Index);
              }
          }
      }
    }
    ```

3. Abra o arquivo `project.json` e, na seção `frameworks`, remova a linha a seguir:

   ```json
   "type": "platform",
   ```
A seção Estrutura deverá aparecer como mostrado a seguir depois de você modificá-la:

    ```json
    "frameworks": {
      "netcoreapp1.0": {
        "dependencies": {
          "Microsoft.NETCore.App": {
             "version": "1.0.0"
          }
        }
      }
    }
    ```
Remover o atributo `"type": "platform"` indica que a estrutura é fornecida como um conjunto de componentes locais para nosso aplicativo, em vez de um pacote da plataforma de todo o sistema.

4. Crie uma seção `runtimes` em seu arquivo `project.json` que define as plataformas de destino do seu aplicativo e especifique o identificador de tempo de execução de cada plataforma que você selecionar. Consulte o [Catálogo de Identificador de Tempo de Execução](../rid-catalog.md) para obter uma lista de identificadores de tempo de execução. Por exemplo, a seção `runtimes` a seguir indica que o aplicativo é executado em sistemas operacionais Windows 10 de 64 bits e no sistema de operacional OS X Versão 10.10 de 64 bits.

    ```json
        "runtimes": {
          "win10-x64": {},
          "osx.10.10-x64": {}
        }
    ```
Observe que você também precisa adicionar uma vírgula para separar a seção `runtimes` da seção anterior.
Um arquivo de exemplo completo `project.json` aparece mais adiante nesta seção.

6. Execute o comando `dotnet restore` para restaurar as dependências especificadas em seu projeto.

7. Crie versões de depuração do seu aplicativo em cada uma das plataformas de destino usando o comando `dotnet build`. A menos que você especifique o identificador de tempo de execução que gostaria de criar, o comando `dotnet build` cria uma compilação apenas para a ID de tempo de execução do sistema atual. Você pode criar seu aplicativo para ambas as plataformas de destino com os comandos:

    ```console
    dotnet build -r win10-x64
    dotnet build -r osx.10.10-x64
    ```
As versões de depuração do seu aplicativo para cada plataforma serão encontradas no subdiretório `.\bin\Debug\netcoreapp1.0\<runtime_identifier>` do projeto.

8. Depois de ter depurado e testado o programa, você pode criar os arquivos a serem implantados com o aplicativo para cada plataforma de destino usando o comando `dotnet publish` para ambas as plataformas de destino da seguinte maneira:

   ```console
   dotnet publish -c release -r win10-x64
   dotnet publish -c release -r osx.10.10-x64
   ```
Isso cria uma versão de lançamento (em vez de depuração) do seu aplicativo para cada plataforma de destino. Os arquivos resultantes são colocados em um subdiretório chamado `publish` que está no subdiretório `.\bin\release\netcoreapp1.0\<runtime_identifier>` do seu projeto. Observe que cada subdiretório contém o conjunto completo de arquivos (arquivos do seu aplicativo e todos os arquivos do .NET Core) necessários para iniciar seu aplicativo.

9. Junto com os arquivos do aplicativo, o processo de publicação emite um arquivo de banco de dados do programa (.pdb) que contém informações de depuração sobre seu aplicativo. O arquivo é útil principalmente para depurar exceções. Você pode optar por não empacotá-lo com arquivos do aplicativo.

Os arquivos publicados podem ser implantados como você desejar. Por exemplo, você pode empacotá-las em um arquivo zip, usar um simples comando `copy` ou implantá-los com qualquer pacote de instalação de sua escolha. 

Veja a seguir o arquivo `project.json` completo para este projeto.

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
      }
    }
  },
  "runtimes": {
    "win10-x64": {},
    "osx.10.10-x64": {}
  }
}
```

### <a name="deploying-a-self-contained-deployment-with-third-party-dependencies"></a>Implantando uma implantação autocontida com dependências de terceiros ###

Implantar uma implantação autocontida com uma ou mais dependências de terceiros requer adicionar a dependência de terceiros:

1. Adicione referências a quaisquer bibliotecas de terceiros à seção `dependencies` de seu arquivo `project.json`. A seção `dependencies` a seguir usa Json.NET como uma biblioteca de terceiros.

    ```json
    "dependencies": {
      "Microsoft.NETCore.App": "1.0.0",
      "Newtonsoft.Json": "9.0.1"
    },
    ```
2. Se você ainda não o fez, baixe o pacote NuGet que contém a dependência de terceiros para seu sistema. Para disponibilizar a dependência para seu aplicativo, execute o comando `dotnet restore` depois de adicionar a dependência. Como a dependência é resolvida fora do cache local do NuGet no momento da publicação, ela deve estar disponível no seu sistema.

Veja a seguir o arquivo project.json completo para este projeto:

```json
{
  "version": "1.0.0-*",
  "buildOptions": {
    "debugType": "portable",
    "emitEntryPoint": true
  },
  "dependencies": {
    "Microsoft.NETCore.App": "1.0.0",
    "Newtonsoft.Json": "9.0.1"
  },
  "frameworks": {
    "netcoreapp1.0": {
    }
  },
  "runtimes": {
    "win10-x64": {},
    "osx.10.10-x64": {}
  }
}
```

Quando você implanta seu aplicativo, todas as dependências de terceiros usadas em seu aplicativo também contém os arquivos do aplicativo. Bibliotecas de terceiros não precisam existir anteriormente no sistema no qual o aplicativo está em execução.

Observe que você só pode implantar uma implantação autocontida com uma biblioteca de terceiros para plataformas compatíveis com essa biblioteca. Isso é semelhante a ter dependências de terceiros com dependências nativas em sua implantação dependente de estrutura. 

### <a name="deploying-a-self-contained-deployment-with-a-smaller-footprint"></a>Implantar uma implantação autocontida com menor superfície ###

Se a disponibilidade de espaço de armazenamento adequado nos sistemas de destino for um problema em potencial, você poderá reduzir a superfície geral do seu aplicativo excluindo alguns componentes do sistema. Para fazer isso, você deve definir explicitamente os componentes do .NET Core que seu aplicativo inclui no arquivo project.json.

Para criar uma implantação autocontida com uma superfície menor, comece seguindo as duas primeiras etapas para criar uma implantação autocontida. Após executar o comando `dotnet new` e adicionar o código-fonte C# ao aplicativo, faça o seguinte:

1. Aba o arquivo `project.json` e substitua o código na seção `frameworks` pelo seguinte:

    ```json
    "frameworks": {
      "netstandard1.6": { }
    }
    ```
Isso faz duas coisas:

    * Indica que, em vez de usar toda a estrutura `netcoreapp1.0`, que inclui o .NET Core CLR, a .NET Core Library e uma série de outros componentes do sistema, nosso aplicativo usa somente a .NET Standard Library.

    * Remover o atributo `"type": "platform"` indica que a estrutura é fornecida como um conjunto de componentes locais para nosso aplicativo, em vez de um pacote da plataforma de todo o sistema.

2. Substitua a seção `dependencies` pelo seguinte:

    ```json
    "dependencies": {
      "NETStandard.Library": "1.6.0",
      "Microsoft.NETCore.Runtime.CoreCLR": "1.0.2",
      "Microsoft.NETCore.DotNetHostPolicy":  "1.0.1"
    },
    ```
   Isso define os componentes do sistema usados pelo nosso aplicativo. Os componentes do sistema empacotados com nosso aplicativo incluem a .NET Standard Library, o tempo de execução do .NET Core e o host do .NET Core. Isso gera uma implantação autocontida com menor superfície.

3. Como feito no exemplo [Implantar uma implantação autocontida simples](#simpleSelf), crie uma seção `runtimes` no seu arquivo `project.json` que define as plataformas de destino do seu aplicativo e especifique o identificador de tempo de execução de cada plataforma de destino. Consulte o [Catálogo de Identificador de Tempo de Execução](../rid-catalog.md) para obter uma lista de identificadores de tempo de execução. Por exemplo, a seção `runtimes` a seguir indica que o aplicativo é executado em sistemas operacionais Windows 10 de 64 bits e no sistema de operacional OS X Versão 10.10 de 64 bits.

    ```json
        "runtimes": {
          "win10-x64": {},
          "osx.10.10-x64": {}
        }
    ```
Observe que você também precisa adicionar uma vírgula para separar a seção `runtimes` da seção anterior.
Um arquivo de exemplo completo `project.json` aparece mais adiante nesta seção.

4. Execute o comando `dotnet restore` para restaurar as dependências especificadas em seu projeto.

5. Crie versões de depuração do seu aplicativo em cada uma das plataformas de destino usando o comando `dotnet build`. A menos que você especifique o identificador de tempo de execução que gostaria de criar, o comando `dotnet build` cria uma compilação apenas para a ID de tempo de execução do sistema atual. Você pode criar seu aplicativo para ambas as plataformas de destino com os comandos:

    ```console
    dotnet build -r win10-x64
    dotnet build -r osx.10.10-x64
    ```

6. Depois de ter depurado e testado o programa, você pode criar os arquivos a serem implantados com o aplicativo para cada plataforma de destino usando o comando `dotnet publish` para ambas as plataformas de destino da seguinte maneira:

   ```console
   dotnet publish -c release -r win10-x64
   dotnet publish -c release -r osx.10.10-x64
   ```
Isso cria uma versão de lançamento (em vez de depuração) do seu aplicativo para cada plataforma de destino. Os arquivos resultantes são colocados em um subdiretório chamado `publish` que está no subdiretório `.\bin\release\netstandard1.6\<runtime_identifier>` do seu projeto. Observe que cada subdiretório contém o conjunto completo de arquivos (arquivos do seu aplicativo e todos os arquivos do .NET Core) necessários para iniciar seu aplicativo.

7. Junto com os arquivos do aplicativo, o processo de publicação emite um arquivo de banco de dados do programa (.pdb) que contém informações de depuração sobre seu aplicativo. O arquivo é útil principalmente para depurar exceções. Você pode optar por não empacotá-lo com arquivos do aplicativo.

Os arquivos publicados podem ser implantados como você desejar. Por exemplo, você pode empacotá-las em um arquivo zip, usar um simples comando `copy` ou implantá-los com qualquer pacote de instalação de sua escolha. 

Veja a seguir o arquivo `project.json` completo para este projeto.

```json
   {
     "version": "1.0.0-*",
     "buildOptions": {
       "debugType": "portable",
       "emitEntryPoint": true
     },
     "dependencies": {
       "NETStandard.Library": "1.6.0",
       "Microsoft.NETCore.Runtime.CoreCLR": "1.0.2",
       "Microsoft.NETCore.DotNetHostPolicy":  "1.0.1"
     },
     "frameworks": {
       "netstandard1.6": { }
     },
     "runtimes": {
       "win10-x64": {},
       "osx.10.10-x64": {}
     }
   }
```



<!--HONumber=Nov16_HO3-->


