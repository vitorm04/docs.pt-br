---
title: Migrando C++projetos/CLI para o .NET Core
description: Saiba mais sobre como C++portar projetos de/CLI para o .NET Core.
author: mjrousos
ms.date: 01/10/2020
ms.openlocfilehash: eb03f2a5ff42e8279fd3ebd6ee6fb6d955f6798d
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964926"
---
# <a name="how-to-port-a-ccli-project-to-net-core"></a>Como portar um C++projeto/CLI para o .NET Core

A partir do .NET Core 3,1 e do Visual Studio 2019 versão 16,4, [ C++os projetos/CLI](/cpp/dotnet/dotnet-programming-with-cpp-cli-visual-cpp) podem ter como destino o .NET Core. Esse suporte torna possível a porta de aplicativos da área de C++trabalho do Windows com camadas de interoperabilidade/CLI para o .NET Core. Este artigo descreve como portar C++projetos da/cli do .NET Framework para o .net Core 3,1.

## <a name="ccli-net-core-limitations"></a>C++Limitações do .NET Core/CLI

Há algumas limitações importantes para portar projetos C++/CLI para o .NET Core em comparação com outras linguagens:

* C++O suporte a/CLI para .NET Core é somente Windows.
* C++Os projetos/CLI não podem ter como destino .NET Standard, somente o .NET Core (ou .NET Framework).
* C++Os projetos/CLI não dão suporte ao novo formato de arquivo de projeto em estilo SDK. Em vez disso, mesmo ao direcionar C++o .NET Core, os projetos/CLI usam o formato de arquivo vcxproj existente.
* C++Projetos/CLI não podem ter vários destinos em várias plataformas .NET. Se você precisar criar um C++projeto/CLI para o .NET Framework e o .NET Core, use arquivos de projeto separados.
* O .NET Core não dá suporte à compilação `-clr:pure` ou `-clr:safe`, somente a nova opção `-clr:netcore` (que é equivalente a `-clr` para .NET Framework).

## <a name="port-a-ccli-project"></a>Porta um C++projeto/CLI

Para portar C++um projeto/CLI para o .NET Core, faça as seguintes alterações no arquivo vcxproj. Essas etapas de migração diferem das etapas necessárias para outros tipos C++de projeto porque os projetos/CLI não usam arquivos de projeto em estilo SDK.

1. Substitua `<CLRSupport>true</CLRSupport>` Propriedades por `<CLRSupport>NetCore</CLRSupport>`. Essa propriedade geralmente está em grupos de Propriedades específicos da configuração, portanto, talvez seja necessário substituí-la em vários locais.
2. Substitua `<TargetFrameworkVersion>` Propriedades por `<TargetFramework>netcoreapp3.1</TargetFramework>`.
3. Remova todas as referências de .NET Framework (como `<Reference Include="System" />`). SDK do .NET Core assemblies são automaticamente referenciados ao usar `<CLRSupport>NetCore</CLRSupport>`.
4. Atualize o uso da API em arquivos CPP, conforme necessário, para remover APIs indisponíveis para o .NET Core. Como C++os projetos/CLI tendem a ser bastante finos camadas de interoperabilidade, muitas vezes não há muitas alterações necessárias. O [.net Portability Analyzer](../../standard/analyzers/portability-analyzer.md) pode ser usado para identificar APIs .NET sem suporte usadas por C++binários/CLI, assim como com binários puramente gerenciados. As diretrizes para determinar a portabilidade do código e a atualização de projetos para trabalhar com as APIs do .NET Core estão disponíveis nas [diretrizes de portabilidade da biblioteca](./libraries.md#determine-portability).

### <a name="wpf-and-windows-forms-usage"></a>Uso do WPF e do Windows Forms

Os projetos C++do .NET Core/CLI podem usar Windows Forms e APIs do WPF. Para usar essas APIs de área de trabalho do Windows, você precisa adicionar referências de estrutura explícitas às bibliotecas de interface do usuário. Os projetos no estilo SDK que usam as APIs da área de trabalho do Windows fazem referência automaticamente às bibliotecas de estrutura necessárias usando o SDK do `Microsoft.NET.Sdk.WindowsDesktop`. Como C++os projetos/CLI não usam o formato de projeto no estilo SDK, eles precisam adicionar referências de estrutura explícitas ao direcionar o .NET Core.

Para usar Windows Forms APIs, adicione essa referência ao arquivo vcxproj:

```xml
<!-- Reference all of Windows Forms -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App.WindowsForms" />
```

Para usar APIs do WPF, adicione essa referência ao arquivo vcxproj:

```xml
<!-- Reference all of WPF -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App.WPF" />
```

Para usar as APIs Windows Forms e WPF, adicione essa referência ao arquivo vcxproj:

```xml
<!-- Reference the entirety of the Windows desktop framework:
     Windows Forms, WPF, and the types that provide integration between them -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App" />
```

Atualmente, não é possível adicionar essas referências usando o Gerenciador de referências do Visual Studio. Em vez disso, atualize o arquivo de projeto manualmente. Essa atualização pode ser feita no Visual Studio descarregando o projeto e editando o arquivo de projeto. Você também pode usar outro editor como VS Code.

## <a name="build-without-msbuild"></a>Compilar sem MSBuild

Também é possível criar C++projetos/CLI sem usar o MSBuild. Siga estas etapas para criar um C++projeto/CLI para o .NET Core diretamente com *CL. exe* e *link. exe*:

1. Ao compilar, passe `-clr:netcore` para *CL. exe*.
2. Referência dos assemblies de referência do .NET Core necessários.
3. Ao vincular, forneça o diretório do host do aplicativo .NET Core como um `LibPath` (para que *ijwhost. lib* possa ser encontrado).
4. Copie *ijwhost. dll* (do diretório de host do aplicativo .NET Core) para o diretório de saída do projeto.
5. Verifique se um arquivo [runtimeconfig. JSON](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) existe para o primeiro componente do aplicativo que executará o código gerenciado. Se o aplicativo tiver um ponto de entrada gerenciado, um arquivo de `runtime.config` será criado e copiado automaticamente. No entanto, se o aplicativo tiver um ponto de entrada nativo, você precisará criar um arquivo `runtimeconfig.json` C++para a primeira biblioteca/CLI usar o tempo de execução do .NET Core.

## <a name="known-issues"></a>Problemas conhecidos

Há alguns problemas conhecidos a serem verificados ao trabalhar com C++projetos/CLI visando o .NET Core.

* Uma referência de estrutura do WPF em C++projetos do .NET Core/CLI atualmente faz com que alguns avisos estranhos não conseguirem importar símbolos. Esses avisos podem ser ignorados com segurança e devem ser corrigidos em breve.
* Se o aplicativo tiver um ponto de entrada nativo, C++a biblioteca/CLI que primeiro executa o código gerenciado precisa de um arquivo [runtimeconfig. JSON](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) . Esse arquivo de configuração é usado quando o tempo de execução do .NET Core é iniciado. C++Os projetos/CLI não criam `runtimeconfig.json` arquivos automaticamente no momento da compilação, portanto, o arquivo deve ser gerado manualmente. Se uma C++biblioteca/CLI for chamada de um ponto de entrada gerenciado, a C++biblioteca/CLI não precisará de um arquivo de `runtimeconfig.json` (já que o assembly de ponto de entrada terá um que é usado ao iniciar o tempo de execução). Um arquivo de `runtimeconfig.json` de exemplo simples é mostrado abaixo. Para obter mais informações, consulte a [especificação no GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).

    ```json
    {
          "runtimeOptions": {
             "tfm": "netcoreapp3.1",
             "framework": {
                "name": "Microsoft.NETCore.App",
                "version": "3.1.0"
             }
          }
    }
    ```
