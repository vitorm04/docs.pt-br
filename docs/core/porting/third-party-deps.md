---
title: Analisar as dependências para fazer a portabilidade do código para o .NET Core
description: Aprenda a analisar as dependências externas para fazer a portabilidade de seu projeto do .NET Framework para o .NET Core.
author: cartermp
ms.date: 10/22/2019
ms.openlocfilehash: 2aa09e551a99358d3a6961fafcfc0aa8dbd976b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398961"
---
# <a name="analyze-your-dependencies-to-port-code-to-net-core"></a>Analisar suas dependências para fazer a portabilidade do código para o .NET Core

Para fazer a portabilidade de seu código para o .NET Core ou .NET Standard, é preciso compreender suas dependências. Dependências externas são os pacotes NuGet ou `.dll` arquivos que você faz referência em seu projeto, mas que você não se constrói.

## <a name="migrate-your-nuget-packages-to-packagereference"></a>Migre seus pacotes NuGet para`PackageReference`

O .NET Core usa [PackageReference](/nuget/consume-packages/package-references-in-project-files) para especificar as dependências do pacote. Se você estiver usando [packages.config](/nuget/reference/packages-config) para especificar seus pacotes `PackageReference` em `packages.config` seu projeto, converta-o para o formato, porque não é suportado no .NET Core.

Para saber como migrar, consulte o [artigo Migrar de pacotes.config para PackageReference.](/nuget/reference/migrate-packages-config-to-package-reference)

## <a name="upgrade-your-nuget-packages"></a>Atualize seus pacotes NuGet

Depois de migrar seu `PackageReference` projeto para o formato, verifique se seus pacotes são compatíveis com o .NET Core.

Primeiro, atualize seus pacotes para a versão mais recente que puder. Isso pode ser feito com a UI NuGet Package Manager no Visual Studio. É provável que as versões mais recentes das dependências do pacote já sejam compatíveis com o .NET Core.

## <a name="analyze-your-package-dependencies"></a>Analise suas dependências de pacotes

Se você ainda não verificou que suas dependências de pacotes convertidos e atualizados funcionam no .NET Core, existem algumas maneiras de conseguir isso:

### <a name="analyze-nuget-packages-using-nugetorg"></a>Analisar pacotes NuGet usando nuget.org

Você pode ver os TFMs (Target Framework Monikers) que cada pacote suporta em [nuget.org](https://www.nuget.org/) na seção **Dependências** da página do pacote.

Embora o uso do site seja um método mais fácil de verificar a compatibilidade, as informações **do Dependencies** não estão disponíveis no site para todos os pacotes.

### <a name="analyze-nuget-packages-using-nuget-package-explorer"></a>Analisar pacotes NuGet usando o Explorador de Pacotes NuGet

Um pacote NuGet é um conjunto de pastas que contêm assemblies específicos de plataforma. Verifique se há uma pasta que contém um conjunto compatível dentro do pacote.

A maneira mais fácil de inspecionar pastas de pacote NuGet é usar a ferramenta [NuGet Package Explorer.](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) Depois da instalação, use as seguintes etapas para ver os nomes de pasta:

1. Abra o Explorador de Pacotes NuGet.
2. Clique em **Abrir pacote de feed online**.
3. Pesquise o nome do pacote.
4. Selecione o nome do pacote nos resultados da pesquisa e clique em **abrir**.
5. Expanda a pasta *lib* no lado direito e observe os nomes de pasta.

Procure uma pasta com nomes usando `netstandardX.Y` um `netcoreappX.Y`dos seguintes padrões: ou .

Esses valores são [TFMs (Monikers da Estrutura de Destino)](../../standard/frameworks.md), que são mapeados para versões do [.NET Standard](../../standard/net-standard.md), .NET Core e perfis de PCL (Biblioteca de Classes Portátil) tradicionais que são compatíveis com .NET Core.

> [!IMPORTANT]
> Ao analisar os TFMs compatíveis com um pacote, observe que o `netcoreapp*`, embora compatível, serve somente para projetos do .NET Core e não para projetos do .NET Standard.
> Uma biblioteca destinada somente a `netcoreapp*` e não a `netstandard*` só pode ser consumida por outros aplicativos do .NET Core.

## <a name="net-framework-compatibility-mode"></a>Modo de compatibilidade do .NET framework

Depois de analisar os pacotes NuGet, você pode descobrir que eles só têm como alvo o Quadro .NET.

O modo de compatibilidade do .NET Framework foi introduzido a partir do .NET Standard 2.0. Esse modo de compatibilidade permite que os projetos do .NET Standard e do .NET Core referenciem bibliotecas do .NET Framework. Fazer referência a bibliotecas do .NET Framework não funciona para todos os projetos, como nos casos em que a biblioteca usa APIs do WPF (Windows Presentation Foundation), mas isso desbloqueia muitos cenários de portabilidade.

Quando você faz referência a pacotes NuGet que visam o .NET Framework em seu projeto, como [Huitian.PowerCollections,](https://www.nuget.org/packages/Huitian.PowerCollections)você recebe um aviso de recuo de pacote[(NU1701)](/nuget/reference/errors-and-warnings/nu1701)semelhante ao seguinte exemplo:

`NU1701: Package ‘Huitian.PowerCollections 1.0.0’ was restored using ‘.NETFramework,Version=v4.6.1’ instead of the project target framework ‘.NETStandard,Version=v2.0’. This package may not be fully compatible with your project.`

Esse aviso será exibido quando você adicionar o pacote e sempre que você compilar, para que você não se esqueça de testar o pacote com o projeto. Se o seu projeto funcionar como esperado, você pode suprimir esse aviso editando as propriedades do pacote no Visual Studio ou editando manualmente o arquivo do projeto no seu editor de código favorito.

Para suprimir o aviso editando o arquivo de projeto, localize a entrada `PackageReference` do pacote em que você deseja suprimir o aviso e adicione o atributo `NoWarn`. O atributo `NoWarn` aceita uma lista separada por vírgulas de todas as IDs de aviso. O exemplo a seguir mostra como suprimir o aviso `NU1701` do pacote `Huitian.PowerCollections` por meio da edição manual do arquivo de projeto:

```xml
<ItemGroup>
  <PackageReference Include="Huitian.PowerCollections" Version="1.0.0" NoWarn="NU1701" />
</ItemGroup>
```

Para obter mais informações sobre como suprimir avisos do compilador no Visual Studio, consulte [Suprimir avisos de pacotes NuGet](/visualstudio/ide/how-to-suppress-compiler-warnings#suppress-warnings-for-nuget-packages).

## <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a>O que fazer quando a dependência de pacote NuGet não é executada no .NET Core

Há algumas coisas que você pode fazer se um pacote NuGet do qual você depende não for executado no .NET Core:

- Se o projeto for um software livre e estiver hospedado em algum lugar como o GitHub, você poderá entrar em contato diretamente com os desenvolvedores.
- Você pode entrar em contato diretamente com o autor sobre [nuget.org](https://www.nuget.org/). Procure o pacote e clique em Entrar em **Contato proprietários** no lado esquerdo da página do pacote.
- Você pode pesquisar outro pacote que seja executado no .NET Core e realize a mesma tarefa que o pacote que você estava usando.
- Você pode tentar escrever por conta própria o código do que o pacote estava fazendo.
- Você pode eliminar a dependência do pacote alterando a funcionalidade do aplicativo, pelo menos até que uma versão compatível do pacote fique disponível.

Lembre-se que os mantenedores de projetos de software livre e os editores de pacote NuGet geralmente são voluntários. Elas contribuem porque se importam com um determinado domínio, fazem-no gratuitamente e geralmente têm um trabalho diferente durante dia. Tenha em contato com eles para solicitar suporte ao .NET Core.

Se você não puder resolver seu problema com qualquer uma dessas opções, você pode ter que portar para .NET Core em uma data posterior.

A equipe do .NET gostaria de saber quais bibliotecas são as mais importantes para compatibilidade com o .NET Core. Você pode enviar um email para dotnet@microsoft.com, informando sobre as bibliotecas que você deseja usar.

## <a name="analyze-dependencies-that-arent-nuget-packages"></a>Analisar dependências que não são pacotes NuGet

Você pode ter uma dependência que não seja um pacote NuGet, tal como uma DLL no sistema de arquivos. A única maneira de determinar a portabilidade dessa dependência é executar a ferramenta [.NET Portability Analyzer](https://github.com/Microsoft/dotnet-apiport). A ferramenta analisa conjuntos que visam o .NET Framework e identifica APIs que não são portáteis para outras plataformas .NET, como .NET Core. Você pode executar a ferramenta como um aplicativo de console ou uma [extensão do Visual Studio](../../standard/analyzers/portability-analyzer.md).

## <a name="next-steps"></a>Próximas etapas

>[!div class="nextstepaction"]
>[Portar bibliotecas](libraries.md)
