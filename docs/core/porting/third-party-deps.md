---
title: Analisar as dependências para fazer a portabilidade do código para o .NET Core
description: Aprenda a analisar as dependências externas para fazer a portabilidade de seu projeto do .NET Framework para o .NET Core.
author: cartermp
ms.date: 10/22/2019
ms.custom: seodec18
ms.openlocfilehash: 5fa5a20e9a2b5427401835a0c1c6e1845d86c3ef
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72798789"
---
# <a name="analyze-your-dependencies-to-port-code-to-net-core"></a>Analisar suas dependências para fazer a portabilidade do código para o .NET Core

Para fazer a portabilidade de seu código para o .NET Core ou .NET Standard, é preciso compreender suas dependências. Dependências externas são os pacotes NuGet ou `.dll`s que você faz referência em seu projeto, mas que você não se compila.

## <a name="migrate-your-nuget-packages-to-packagereference"></a>Migre seus pacotes NuGet para `PackageReference`

O .NET Core usa [PackageReference](/nuget/consume-packages/package-references-in-project-files) para especificar as dependências do pacote. Se você estiver usando [Packages. config](/nuget/reference/packages-config) para especificar seus pacotes em seu projeto, precisará convertê-lo no formato de `PackageReference` porque `packages.config` não tem suporte no .NET Core.

Para saber como migrar, consulte o artigo [migrar de Packages. config para PackageReference](/nuget/reference/migrate-packages-config-to-package-reference) .

## <a name="upgrade-your-nuget-packages"></a>Atualizar seus pacotes NuGet

Depois de migrar seu projeto para o formato de `PackageReference`, você precisa verificar se os pacotes são compatíveis com o .NET Core.

Primeiro, atualize seus pacotes para a versão mais recente que você pode. Isso pode ser feito com a interface do usuário do Gerenciador de pacotes NuGet no Visual Studio. É provável que as versões mais recentes das suas dependências de pacote já sejam compatíveis com o .NET Core.

## <a name="analyze-your-package-dependencies"></a>Analisar suas dependências de pacote

Se você ainda não verificou que suas dependências de pacote convertidas e atualizadas funcionam no .NET Core, há algumas maneiras de conseguir isso:

### <a name="analyze-nuget-packages-using-nugetorg"></a>Analisar pacotes NuGet usando nuget.org

Você pode ver os monikers do Framework de destino (TFMs) que cada pacote dá suporte no [NuGet.org](https://www.nuget.org/) na seção **dependências** da página do pacote.

Embora o uso do site seja um método mais fácil para verificar a compatibilidade, as informações de **dependências** não estão disponíveis no site para todos os pacotes.

### <a name="analyze-nuget-packages-using-nuget-package-explorer"></a>Analisar pacotes NuGet usando o Explorador de Pacotes NuGet

Um pacote NuGet é um conjunto de pastas que contêm assemblies específicos de plataforma. Portanto, você precisa verificar se há uma pasta que contém um assembly compatível dentro do pacote.

A maneira mais fácil de inspecionar a pastas do pacote NuGet é usar a ferramenta [Explorador de Pacotes NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer). Depois da instalação, use as seguintes etapas para ver os nomes de pasta:

1. Abra o Explorador de Pacotes NuGet.
2. Clique em **Abrir pacote de feed online**.
3. Pesquise o nome do pacote.
4. Selecione o nome do pacote nos resultados da pesquisa e clique em **abrir**.
5. Expanda a pasta *lib* no lado direito e observe os nomes de pasta.

Procure uma pasta com nomes usando um dos seguintes padrões: `netstandardX.Y` ou `netcoreappX.Y`.

Esses valores são [TFMs (Monikers da Estrutura de Destino)](../../standard/frameworks.md), que são mapeados para versões do [.NET Standard](../../standard/net-standard.md), .NET Core e perfis de PCL (Biblioteca de Classes Portátil) tradicionais que são compatíveis com .NET Core.

> [!IMPORTANT]
> Ao analisar os TFMs compatíveis com um pacote, observe que o `netcoreapp*`, embora compatível, serve somente para projetos do .NET Core e não para projetos do .NET Standard.
> Uma biblioteca destinada somente a `netcoreapp*` e não a `netstandard*` só pode ser consumida por outros aplicativos do .NET Core.

## <a name="net-framework-compatibility-mode"></a>Modo de compatibilidade do .NET framework

Depois de analisar os pacotes NuGet, talvez você ache que eles se destinam apenas ao .NET Framework.

O modo de compatibilidade do .NET Framework foi introduzido a partir do .NET Standard 2.0. Esse modo de compatibilidade permite que os projetos do .NET Standard e do .NET Core referenciem bibliotecas do .NET Framework. Fazer referência a bibliotecas do .NET Framework não funciona para todos os projetos, como nos casos em que a biblioteca usa APIs do WPF (Windows Presentation Foundation), mas isso desbloqueia muitos cenários de portabilidade.

Ao fazer referência a pacotes NuGet que se destinam ao .NET Framework em seu projeto, como [Huitian.PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections), você receberá um aviso de fallback do pacote ([NU1701](/nuget/reference/errors-and-warnings/nu1701)) semelhante ao exemplo a seguir:

`NU1701: Package ‘Huitian.PowerCollections 1.0.0’ was restored using ‘.NETFramework,Version=v4.6.1’ instead of the project target framework ‘.NETStandard,Version=v2.0’. This package may not be fully compatible with your project.`

Esse aviso será exibido quando você adicionar o pacote e sempre que você compilar, para que você não se esqueça de testar o pacote com o projeto. Se o projeto está funcionando como esperado, você pode suprimir esse aviso, editando as propriedades do pacote no Visual Studio ou editando manualmente o arquivo de projeto em seu editor de código favorito.

Para suprimir o aviso editando o arquivo de projeto, localize a entrada `PackageReference` do pacote em que você deseja suprimir o aviso e adicione o atributo `NoWarn`. O atributo `NoWarn` aceita uma lista separada por vírgulas de todas as IDs de aviso. O exemplo a seguir mostra como suprimir o aviso `NU1701` do pacote `Huitian.PowerCollections` por meio da edição manual do arquivo de projeto:

```xml
<ItemGroup>
  <PackageReference Include="Huitian.PowerCollections" Version="1.0.0" NoWarn="NU1701" />
</ItemGroup>
```

Para obter mais informações sobre como suprimir avisos do compilador no Visual Studio, consulte [Suprimir avisos de pacotes NuGet](/visualstudio/ide/how-to-suppress-compiler-warnings#suppress-warnings-for-nuget-packages).

## <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a>O que fazer quando a dependência de pacote NuGet não é executada no .NET Core

Há algumas coisas que você pode fazer se um pacote NuGet do qual você depende não for executado no .NET Core:

1. Se o projeto for um software livre e estiver hospedado em algum lugar como o GitHub, você poderá entrar em contato diretamente com os desenvolvedores.
2. Você pode entrar em contato com o autor diretamente no [NuGet.org](https://www.nuget.org/). Pesquise o pacote e clique em **contatar proprietários** no lado esquerdo da página do pacote.
3. Você pode pesquisar outro pacote que seja executado no .NET Core e realize a mesma tarefa que o pacote que você estava usando.
4. Você pode tentar escrever por conta própria o código do que o pacote estava fazendo.
5. Você pode eliminar a dependência do pacote alterando a funcionalidade do aplicativo, pelo menos até que uma versão compatível do pacote fique disponível.

Lembre-se que os mantenedores de projetos de software livre e os editores de pacote NuGet geralmente são voluntários. Elas contribuem porque se importam com um determinado domínio, fazem-no gratuitamente e geralmente têm um trabalho diferente durante dia. Portanto, lembre-se disso ao entrar em contato com eles para solicitar suporte para o .NET Core.

Se você não puder resolver o problema com nenhuma das opções acima, talvez seja necessário realizar a portabilidade para o .NET Core posteriormente.

A equipe do .NET gostaria de saber quais bibliotecas são as mais importantes para compatibilidade com o .NET Core. Você pode enviar um email para dotnet@microsoft.com, informando sobre as bibliotecas que você deseja usar.

## <a name="analyze-dependencies-that-arent-nuget-packages"></a>Analisar dependências que não são pacotes NuGet

Você pode ter uma dependência que não seja um pacote NuGet, tal como uma DLL no sistema de arquivos. A única maneira de determinar a portabilidade dessa dependência é executar a ferramenta [.NET Portability Analyzer](https://github.com/Microsoft/dotnet-apiport). A ferramenta pode analisar assemblies direcionados ao .NET Framework e identificar as APIs que não são portáteis para outras plataformas do .NET, como o .NET Core. Você pode executar a ferramenta como um aplicativo de console ou uma [extensão do Visual Studio](../../standard/analyzers/portability-analyzer.md).

>[!div class="step-by-step"]
>[Avançar](libraries.md)
