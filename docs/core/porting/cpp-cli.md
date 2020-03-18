---
title: Migrando projetos C++/CLI para .NET Core
description: Aprenda a portar projetos C++/CLI para o .NET Core.
author: mjrousos
ms.date: 01/10/2020
ms.openlocfilehash: eb03f2a5ff42e8279fd3ebd6ee6fb6d955f6798d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75964926"
---
# <a name="how-to-port-a-ccli-project-to-net-core"></a>Como portar um projeto C++/CLI para o .NET Core

Começando com o .NET Core 3.1 e o Visual Studio 2019 versão 16.4, [os projetos C++/CLI](/cpp/dotnet/dotnet-programming-with-cpp-cli-visual-cpp) podem atingir o .NET Core. Esse suporte torna possível portar aplicativos de desktop do Windows com camadas de interop C++/CLI para .NET Core. Este artigo descreve como portar projetos C++/CLI de .NET Framework para .NET Core 3.1.

## <a name="ccli-net-core-limitations"></a>C++/CLI .NET Principais limitações

Existem algumas limitações importantes para portar projetos C++/CLI para .NET Core em comparação com outros idiomas:

* O suporte a C++/CLI para .NET Core é apenas para Windows.
* Os projetos C++/CLI não podem atingir o .NET Standard, apenas o .NET Core (ou .NET Framework).
* Os projetos C++/CLI não suportam o novo formato de arquivo de projeto no estilo SDK. Em vez disso, mesmo ao direcionar o .NET Core, os projetos C++/CLI usam o formato de arquivo vcxproj existente.
* Os projetos C++/CLI não podem segmentar várias plataformas .NET. Se você precisar construir um projeto C++/CLI para o .NET Framework e o .NET Core, use arquivos de projeto separados.
* O .NET Core `-clr:pure` não `-clr:safe` suporta ou `-clr:netcore` compila, apenas a `-clr` nova opção (que equivale a .NET Framework).

## <a name="port-a-ccli-project"></a>Porta um projeto C++/CLI

Para portar um projeto C++/CLI para .NET Core, faça as seguintes alterações no arquivo vcxproj. Essas etapas de migração diferem das etapas necessárias para outros tipos de projeto porque os projetos C++/CLI não usam arquivos de projeto no estilo SDK.

1. Substitua `<CLRSupport>true</CLRSupport>` `<CLRSupport>NetCore</CLRSupport>`as propriedades por . Esta propriedade está frequentemente em grupos de propriedades específicos da configuração, então você pode precisar substituí-la em vários lugares.
2. Substitua `<TargetFrameworkVersion>` `<TargetFramework>netcoreapp3.1</TargetFramework>`as propriedades por .
3. Remova quaisquer referências do `<Reference Include="System" />`Quadro .NET (como ). Os conjuntos .NET Core SDK são `<CLRSupport>NetCore</CLRSupport>`automaticamente referenciados ao usar .
4. Atualize o uso da API em arquivos cpp, conforme necessário, para remover APIs indisponíveis para .NET Core. Como os projetos C++/CLI tendem a ser camadas de interop bastante finas, muitas vezes não são necessárias muitas mudanças. O [Analisador de Portabilidade .NET](../../standard/analyzers/portability-analyzer.md) pode ser usado para identificar APIs .NET não suportadas usadas por binários C++/CLI, assim como com binários puramente gerenciados. As diretrizes para determinar a portabilidade de código e atualizar projetos para trabalhar com APIs do Núcleo .NET estão disponíveis na [orientação de portabilidade](./libraries.md#determine-portability)da biblioteca .

### <a name="wpf-and-windows-forms-usage"></a>Uso de Formulários WPF e Windows

Os projetos .NET Core C++/CLI podem usar formulários do Windows e APIs do WPF. Para usar essas APIs de desktop do Windows, você precisa adicionar referências de estrutura explícitas às bibliotecas de ida e fiscal. Projetos no estilo SDK que usam APIs de desktop do `Microsoft.NET.Sdk.WindowsDesktop` Windows fazem referência às bibliotecas de estruturas necessárias automaticamente usando o SDK. Como os projetos C++/CLI não usam o formato de projeto no estilo SDK, eles precisam adicionar referências de estrutura explícitas ao direcionar o .NET Core.

Para usar apis do Windows Forms, adicione esta referência ao arquivo vcxproj:

```xml
<!-- Reference all of Windows Forms -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App.WindowsForms" />
```

Para usar as APIs do WPF, adicione esta referência ao arquivo vcxproj:

```xml
<!-- Reference all of WPF -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App.WPF" />
```

Para usar tanto os Formulários do Windows quanto as APIs do WPF, adicione esta referência ao arquivo vcxproj:

```xml
<!-- Reference the entirety of the Windows desktop framework:
     Windows Forms, WPF, and the types that provide integration between them -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App" />
```

Atualmente, não é possível adicionar essas referências usando o gerente de referência do Visual Studio. Em vez disso, atualize o arquivo do projeto manualmente. Esta atualização pode ser feita no Visual Studio descarregando o projeto e, em seguida, editando o arquivo do projeto. Você também pode usar outro editor como VS Code.

## <a name="build-without-msbuild"></a>Construir sem MSBuild

Também é possível construir projetos C++/CLI sem usar o MSBuild. Siga estas etapas para construir um projeto C++/CLI para .NET Core diretamente com *cl.exe* e *link.exe*:

1. Ao compilar, `-clr:netcore` passe para *cl.exe*.
2. Montagem de referência necessária .NET Core.
3. Ao vincular, forneça o diretório de host `LibPath` do aplicativo .NET Core como um (para que *ijwhost.lib* possa ser encontrado).
4. Copie *ijwhost.dll* (do diretório de host do aplicativo .NET Core) para o diretório de saída do projeto.
5. Certifique-se de que existe um arquivo [runtimeconfig.json](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) para o primeiro componente do aplicativo que executará o código gerenciado. Se o aplicativo tiver um ponto `runtime.config` de entrada gerenciado, um arquivo será criado e copiado automaticamente. Se o aplicativo tiver um ponto de entrada `runtimeconfig.json` nativo, porém, você precisa criar um arquivo para a primeira biblioteca C++/CLI para usar o tempo de execução do .NET Core.

## <a name="known-issues"></a>Problemas conhecidos

Existem alguns problemas conhecidos a serem atentos ao trabalhar com projetos C++/CLI direcionados ao .NET Core.

* Uma referência de estrutura do WPF em projetos .NET Core C++/CLI atualmente causa alguns avisos estranhos sobre não poder importar símbolos. Esses avisos podem ser ignorados com segurança e devem ser corrigidos em breve.
* Se o aplicativo tiver um ponto de entrada nativo, a biblioteca C++/CLI que primeiro executa o código gerenciado precisa de um arquivo [runtimeconfig.json.](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) Este arquivo de configuração é usado quando o tempo de execução do .NET Core é iniciado. Os projetos C++/CLI `runtimeconfig.json` ainda não criam arquivos automaticamente no tempo de compilação, então o arquivo deve ser gerado manualmente. Se uma biblioteca C++/CLI for chamada a partir de um ponto de entrada `runtimeconfig.json` gerenciado, a biblioteca C++/CLI não precisará de um arquivo (uma vez que o conjunto de pontos de entrada terá um usado ao iniciar o tempo de execução). Um simples `runtimeconfig.json` arquivo de amostra é mostrado abaixo. Para obter mais informações, consulte a [especificação no GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).

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
