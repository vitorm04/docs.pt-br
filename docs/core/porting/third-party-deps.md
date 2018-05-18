---
title: Portabilidade para .NET Core – Analisar as dependências de terceiros
description: Aprenda a analisar as dependências de terceiros para fazer a portabilidade do seu projeto do .NET Framework para o .NET Core.
author: cartermp
ms.author: mairaw
ms.date: 02/15/2018
ms.openlocfilehash: a5affd8f1c493a87b2a4f7cd4096d168d404626a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="analyze-your-third-party-dependencies"></a>Analisar as dependências de terceiros

Se você tem a intenção de portar seu código para o .NET Core ou o .NET Standard, a primeira etapa no processo de portabilidade é entender as dependências de terceiros. As dependências de terceiros são [pacotes NuGet](#analyze-referenced-nuget-packages-on-your-project) ou [DLLs](#analyze-dependencies-that-arent-nuget-packages) aos quais você faz referência em seu projeto. Avalie cada dependência e desenvolva um plano de contingência para as dependências que não são compatíveis com o .NET Core. Este artigo mostra como determinar se a dependência é compatível com o .NET Core.

## <a name="analyze-referenced-nuget-packages-in-your-project"></a>Analisar os pacotes NuGet referenciados em seu projeto

Se você estiver fazendo referência a pacotes NuGet em seu projeto, é necessário verificar se eles são compatíveis com o .NET Core.
Há duas maneiras de fazer isso:

* [Usando o aplicativo Explorador de Pacotes NuGet](#analyze-nuget-packages-using-nuget-package-explorer) (o método mais confiável).
* [Usando o site nuget.org](#analyze-nuget-packages-using-nugetorg).

Depois de analisar os pacotes, se eles não forem compatíveis com o .NET Core e destinarem-se apenas ao .NET Framework, você poderá verificar se o [modo de compatibilidade do .NET Framework](#net-framework-compatibility-mode) pode ajudar no processo de portabilidade.

### <a name="analyze-nuget-packages-using-nuget-package-explorer"></a>Analisar pacotes NuGet usando o Explorador de Pacotes NuGet

Um pacote NuGet é um conjunto de pastas que contêm assemblies específicos de plataforma. Portanto, você precisa verificar se há uma pasta que contém um assembly compatível dentro do pacote.

A maneira mais fácil de inspecionar a pastas do pacote NuGet é usar a ferramenta [Explorador de Pacotes NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer). Depois da instalação, use as seguintes etapas para ver os nomes de pasta:

1. Abra o Explorador de Pacotes NuGet.
2. Clique em **Abrir pacote de feed online**.
3. Pesquise o nome do pacote.
4. Selecione o nome do pacote nos resultados da pesquisa e clique em **abrir**.
5. Expanda a pasta *lib* no lado direito e observe os nomes de pasta.

Procure uma pasta com qualquer um dos seguintes nomes:

```
netstandard1.0
netstandard1.1
netstandard1.2
netstandard1.3
netstandard1.4
netstandard1.5
netstandard1.6
netstandard2.0
netcoreapp1.0
netcoreapp1.1
netcoreapp2.0
portable-net45-win8
portable-win8-wpa8
portable-net451-win81
portable-net45-win8-wpa8-wpa81
```

Esses valores são [TFMs (Monikers da Estrutura de Destino)](../../standard/frameworks.md), que são mapeados para versões do [.NET Standard](../../standard/net-standard.md), .NET Core e perfis de PCL (Biblioteca de Classes Portátil) tradicionais que são compatíveis com .NET Core.

> [!IMPORTANT]
> Ao analisar os TFMs compatíveis com um pacote, observe que o `netcoreapp*`, embora compatível, serve somente para projetos do .NET Core e não para projetos do .NET Standard.
> Uma biblioteca destinada somente a `netcoreapp*` e não a `netstandard*` só pode ser consumida por outros aplicativos do .NET Core.

Também há alguns TFMs herdados usados em versões de pré-lançamento do .NET Core que podem ser compatíveis:

```
dnxcore50
dotnet5.0
dotnet5.1
dotnet5.2
dotnet5.3
dotnet5.4
dotnet5.5
```

Embora esses TMFs provavelmente funcionem com o seu código, não há nenhuma garantia de compatibilidade. Pacotes com esses TFMs foram compilados com pacotes de pré-lançamento do .NET Core. Anote quando (ou se) os pacotes que usam esses TFMs serão atualizados para tornarem-se baseados em .NET Standard.

> [!NOTE]
> Para usar um pacote direcionado a uma PCL tradicional ou destinado ao .NET Core de pré-lançamento, você deve usar o elemento `PackageTargetFallback` do MSBuild no seu arquivo de projeto.
> Para obter mais informações sobre este elemento do MSBuild, consulte [`PackageTargetFallback`](../tools/csproj.md#packagetargetfallback).

### <a name="analyze-nuget-packages-using-nugetorg"></a>Analisar pacotes NuGet usando nuget.org

Como alternativa, você pode ver os TFMs que são compatíveis com cada pacote em [nuget.org](https://www.nuget.org/), na seção **Dependências** da página do pacote.

Embora o uso do site seja um método mais fácil para verificar a compatibilidade, as informações de **Dependências** não estão disponíveis no site para todos os pacotes.

### <a name="net-framework-compatibility-mode"></a>Modo de compatibilidade do .NET framework

Depois de analisar os pacotes NuGet, você pode chegar à conclusão de que eles se destinam apenas ao .NET Framework, como a maioria dos pacotes NuGet.

O modo de compatibilidade do .NET Framework foi introduzido a partir do .NET Standard 2.0. Esse modo de compatibilidade permite que os projetos do .NET Standard e do .NET Core referenciem bibliotecas do .NET Framework. Fazer referência a bibliotecas do .NET Framework não funciona para todos os projetos, como nos casos em que a biblioteca usa APIs do WPF (Windows Presentation Foundation), mas isso desbloqueia muitos cenários de portabilidade.

Ao fazer referência a pacotes NuGet que se destinam ao .NET Framework em seu projeto, como [Huitian.PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections), você receberá um aviso de fallback do pacote ([NU1701](/nuget/reference/errors-and-warnings#nu1701)) semelhante ao exemplo a seguir:

`NU1701: Package ‘Huitian.PowerCollections 1.0.0’ was restored using ‘.NETFramework,Version=v4.6.1’ instead of the project target framework ‘.NETStandard,Version=v2.0’. This package may not be fully compatible with your project.`

Esse aviso será exibido quando você adicionar o pacote e sempre que você compilar, para que você não se esqueça de testar o pacote com o projeto. Se o projeto está funcionando como esperado, você pode suprimir esse aviso, editando as propriedades do pacote no Visual Studio ou editando manualmente o arquivo de projeto em seu editor de código favorito.

Para suprimir o aviso editando o arquivo de projeto, localize a entrada `PackageReference` do pacote em que você deseja suprimir o aviso e adicione o atributo `NoWarn`. O atributo `NoWarn` aceita uma lista separada por vírgulas de todas as IDs de aviso. O exemplo a seguir mostra como suprimir o aviso `NU1701` do pacote `Huitian.PowerCollections` por meio da edição manual do arquivo de projeto:

```xml
<ItemGroup>
  <PackageReference Include="Huitian.PowerCollections" Version="1.0.0" NoWarn="NU1701" />
</ItemGroup>
```

Para obter mais informações sobre como suprimir avisos do compilador no Visual Studio, consulte [Suprimir avisos de pacotes NuGet](/visualstudio/ide/how-to-suppress-compiler-warnings#suppressing-warnings-for-nuget-packages).

### <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a>O que fazer quando a dependência de pacote NuGet não é executada no .NET Core

Há algumas coisas que você pode fazer se um pacote NuGet do qual você depende não for executado no .NET Core:

1. Se o projeto for um software livre e estiver hospedado em algum lugar como o GitHub, você poderá entrar em contato diretamente com os desenvolvedores.
2. Você pode entrar em contato diretamente com o autor no [nuget.org](https://www.nuget.org/). Pesquise o pacote e clique em **Entrar em contato com os proprietários** no lado esquerdo da página do pacote.
3. Você pode pesquisar outro pacote que seja executado no .NET Core e realize a mesma tarefa que o pacote que você estava usando.
4. Você pode tentar escrever por conta própria o código do que o pacote estava fazendo.
5. Você pode eliminar a dependência do pacote alterando a funcionalidade do aplicativo, pelo menos até que uma versão compatível do pacote fique disponível.

Lembre-se que os mantenedores de projetos de software livre e os editores de pacote NuGet geralmente são voluntários. Elas contribuem porque se importam com um determinado domínio, fazem-no gratuitamente e geralmente têm um trabalho diferente durante dia. Portanto, lembre-se disso ao entrar em contato com eles para solicitar suporte para o .NET Core.

Se você não puder resolver o problema com nenhuma das opções acima, talvez seja necessário realizar a portabilidade para o .NET Core posteriormente.

A equipe do .NET gostaria de saber quais bibliotecas são as mais importantes para compatibilidade com o .NET Core. Você pode enviar um email para dotnet@microsoft.com, informando sobre as bibliotecas que você deseja usar.

## <a name="analyze-dependencies-that-arent-nuget-packages"></a>Analisar dependências que não são pacotes NuGet

Você pode ter uma dependência que não seja um pacote NuGet, tal como uma DLL no sistema de arquivos. A única maneira de determinar a portabilidade dessa dependência é executar a ferramenta [.NET Portability Analyzer](https://github.com/Microsoft/dotnet-apiport). A ferramenta pode analisar assemblies direcionados ao .NET Framework e identificar as APIs que não são portáteis para outras plataformas do .NET, como o .NET Core. Você pode executar a ferramenta como um aplicativo de console ou uma [extensão do Visual Studio](../../standard/analyzers/portability-analyzer.md).

## <a name="next-steps"></a>Próximas etapas

Se você estiver portando uma biblioteca, consulte [Portando suas bibliotecas](libraries.md).
