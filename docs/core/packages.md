---
title: Pacotes, metapacotes e estruturas-.NET Core
description: Aprenda a terminologia para pacotes, metapacotes e estruturas.
author: richlander
ms.date: 04/29/2020
ms.openlocfilehash: a6575226feb71b96f1fe5070406c118081a8cbf0
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595579"
---
# <a name="packages-metapackages-and-frameworks"></a>Pacotes, metapacotes e estruturas

O .NET Core é uma plataforma composta por pacotes NuGet. Algumas experiências de produtos aproveitam melhor a definição refinada de pacotes, enquanto para outros a alta granularidade é melhor. Para acomodar essa duplaidade, o .NET Core é distribuído como um conjunto refinado de pacotes e em partes mais grosseiras com um tipo de pacote informalmente chamado de [metapacote](#metapackages).

Cada um dos pacotes do .NET Core dá suporte à execução em várias implementações do .NET, representadas como estruturas. Algumas dessas estruturas são estruturas tradicionais, como `net46`, que representam o .NET Framework. Outro conjunto são as novas estruturas que podem ser consideradas como "estruturas baseadas em pacote", que estabelecem um novo modelo para definir estruturas. Essas estruturas baseadas em pacote são totalmente criadas e definidas como pacotes, formando uma relação forte entre pacotes e estruturas.

## <a name="packages"></a>Pacotes

O .NET Core é dividido em um conjunto de pacotes que fornecem primitivos, tipos de dados de nível superior, tipos de composição de aplicativo e utilitários comuns. Cada um desses pacotes representa um único assembly de mesmo nome. Por exemplo, o [pacote System. Runtime](https://www.nuget.org/packages/System.Runtime) contém System. Runtime. dll.

Há vantagens em definir pacotes de forma refinada:

- Pacotes refinados podem ser fornecidos em seu próprio cronograma, com testes relativamente limitados de outros pacotes.
- Pacotes refinados podem fornecer suporte a sistemas operacionais e CPUs diferentes.
- Pacotes refinados podem ter dependências específicas em apenas uma biblioteca.
- Os aplicativos são menores, pois os pacotes não referenciados não se tornam parte da distribuição do aplicativo.

Alguns desses benefícios são usados somente em determinadas circunstâncias. Por exemplo, pacotes .NET Core geralmente são fornecidos no mesmo cronograma que o suporte de plataforma. No caso de manutenção, as correções podem ser distribuídas e instaladas como atualizações de único pacote pequeno. Devido ao escopo restrito de alteração, a validação e o tempo para disponibilizar uma correção ficam limitados ao que é necessário para uma única biblioteca.

Veja a seguir uma lista dos principais pacotes NuGet para .NET Core:

- [System. Runtime](https://www.nuget.org/packages/System.Runtime) -o pacote do .NET Core mais fundamental, <xref:System.Object>incluindo <xref:System.String>, <xref:System.Array>, <xref:System.Action>, e <xref:System.Collections.Generic.IList%601>.
- [System.Collections](https://www.nuget.org/packages/System.Collections) – Um conjunto de coleções basicamente genéricas, incluindo <xref:System.Collections.Generic.List%601> e <xref:System.Collections.Generic.Dictionary%602>.
- [System.Net.Http](https://www.nuget.org/packages/System.Net.Http) – Um conjunto de tipos para comunicação de rede HTTP, incluindo <xref:System.Net.Http.HttpClient> e <xref:System.Net.Http.HttpResponseMessage>.
- [System.IO.FileSystem](https://www.nuget.org/packages/System.IO.FileSystem) – Um conjunto de tipos de leitura e gravação para armazenamento de disco local ou em rede, incluindo <xref:System.IO.File> e <xref:System.IO.Directory>.
- [System.Linq](https://www.nuget.org/packages/System.Linq) – Um conjunto de tipos para consultar objetos, incluindo `Enumerable` e <xref:System.Linq.ILookup%602>.
- [System. Reflection](https://www.nuget.org/packages/System.Reflection) -um conjunto de tipos para carregar, inspecionar e ativar tipos, incluindo <xref:System.Reflection.Assembly> <xref:System.Reflection.TypeInfo> e. <xref:System.Reflection.MethodInfo>

Normalmente, em vez de incluir cada pacote, é mais fácil e mais robusto incluir um [metapacote](#metapackages). No entanto, quando você precisa de um único pacote, é possível incluí-lo como no exemplo a seguir, fazendo referência ao pacote [System.Runtime](https://www.nuget.org/packages/System.Runtime/).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.6</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

## <a name="metapackages"></a>Metapacotes

Um metapacote é uma Convenção de pacote NuGet para descrever um conjunto de pacotes que são significativos em conjunto. Um metapacote representa esse conjunto de pacotes, tornando-os dependências. O metapacote pode, opcionalmente, estabelecer uma estrutura para o conjunto de pacotes, especificando uma estrutura.

As versões anteriores das ferramentas do .NET Core (ferramentas baseadas em *Project. JSON* e * \*. csproj* ), por padrão, especificavam uma estrutura e um metapacote. Atualmente, no entanto, o metapacote é referenciado implicitamente pela estrutura de destino, para que cada metapacote seja vinculado a uma estrutura de destino. Por exemplo, a `netstandard1.6` estrutura referencia o metapacote do netstandard. library versão 1.6.0. Da mesma forma, a estrutura `netcoreapp2.1` referencia o metapacote Microsoft.NETCore.App Versão 2.1.0. Para obter mais informações, consulte [Referência implícita de pacote de metapacote no SDK do .NET Core](https://github.com/dotnet/core/blob/master/release-notes/1.0/sdk/1.0-rc3-implicit-package-refs.md).

Direcionar uma estrutura e referenciar implicitamente um metapacote significa que, na verdade, você está adicionando uma referência a cada um de seus pacotes dependentes como um único gesto. Isso disponibiliza todas as bibliotecas nesses pacotes para o IntelliSense (ou uma experiência semelhante) e para publicação do aplicativo.

Há vantagens em usar metapacotes:

- Fornece uma experiência de usuário conveniente para fazer referência a um grande conjunto de pacotes refinados.
- Define um conjunto de pacotes (incluindo versões específicas) que são testados e funcionam bem em conjunto.

O metapacote da .NET Standard é:

- [Netstandard. library](https://www.nuget.org/packages/NETStandard.Library) -descreve as bibliotecas que fazem parte do .net Standard. Aplica-se a todas as implementações do .NET que dão suporte a .NET Standard (por exemplo, .NET Framework, .NET Core e mono). Estabelece a `netstandard` estrutura.

Os principais metapacotes do .NET Core são:

- [Microsoft.NETCore.App](https://www.nuget.org/packages/Microsoft.NETCore.App) – Descreve as bibliotecas que fazem parte da distribuição do .NET Core. Estabelece a `.NETCoreApp` estrutura. Conta com o `NETStandard.Library` menor.
- [Microsoft.AspNetCore.All](https://www.nuget.org/packages/Microsoft.AspNetCore.App) – inclui todos os pacotes com suporte do ASP.NET Core e Entity Framework Core, com exceção daqueles que contêm dependências de terceiros. Para saber mais, confira [Metapacote Microsoft.AspNetCore.App para ASP.NET Core](/aspnet/core/fundamentals/metapackage-app).
- [Microsoft.AspNetCore.All](https://www.nuget.org/packages/Microsoft.AspNetCore.All) – inclui todos os pacotes com suporte do ASP.NET Core, Entity Framework Core e dependências internas e de terceiros usadas pelo ASP.NET Core e pelo Entity Framework Core. Consulte [Metapacote do Microsoft.AspNetCore.All para ASP.NET Core 2.x](/aspnet/core/fundamentals/metapackage) para obter mais informações.
- [Microsoft.NETCore.Portable.Compatibility](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) – Um conjunto de fachadas de compatibilidade que permitem que PCLs (Bibliotecas de Classes Portáteis) baseadas em mscorlib sejam executadas no .NET Core.

## <a name="frameworks"></a>Estruturas

Cada pacote do .NET Core dá suporte a um conjunto de estruturas de runtime. As estruturas descrevem um conjunto de APIs disponível (e possivelmente outras características) com os quais você pode contar ao direcionar uma determinada estrutura. Eles têm controle de versão à medida que novas APIs são adicionadas.

Por exemplo, [System.IO.FileSystem](https://www.nuget.org/packages/System.IO.FileSystem) dá suporte às seguintes estruturas:

- .NETFramework,Version=4.6
- .NETStandard,Version=1.3
- Plataformas 6 Xamarin (por exemplo, xamarinios10)

É útil comparar as duas primeiras dessas estruturas, pois são exemplos das duas maneiras diferentes pelas quais as estruturas são definidas:

- A `.NETFramework,Version=4.6` estrutura representa as APIs disponíveis no .NET Framework 4,6. Você pode produzir bibliotecas compiladas com os assemblies de referência do .NET Framework 4,6 e, em seguida, distribuir essas bibliotecas em pacotes NuGet em uma pasta net46 lib. Ele será usado para aplicativos direcionados .NET Framework 4,6 ou que são compatíveis com ele. Essa é a maneira como todas as estruturas tradicionalmente funcionam.

- A estrutura `.NETStandard,Version=1.3` é uma estrutura baseada em pacote. Ela se baseia em pacotes direcionados para a estrutura definir e expor as APIs com relação à estrutura.

## <a name="package-based-frameworks"></a>Estruturas baseadas em pacote

Há uma relação bidirecional entre estruturas e pacotes. A primeira parte é definir as APIs disponíveis para uma determinada estrutura, por exemplo `netstandard1.3`. Pacotes direcionados a `netstandard1.3` (ou estruturas compatíveis, como o `netstandard1.0`) definem as APIs disponíveis para `netstandard1.3`. Isso pode parecer uma definição circular, mas não é. Por ser "baseada em pacote", a definição da API para a estrutura vem dos pacotes. A estrutura em si não define nenhuma APIs.

A segunda parte da relação é a seleção de ativo. Pacotes podem conter ativos para várias estruturas. Dada uma referência a um conjunto de pacotes e/ou metapacotes, a estrutura é necessária para determinar qual ativo será selecionado, por exemplo `net46` ou `netstandard1.3`. É importante selecionar o ativo correto. Por exemplo, um ativo `net46` provavelmente não é compatível com .NET Framework 4.0 ou .NET Core 1.0.

Veja essa relação na imagem a seguir. A *API* é voltada para a *estrutura* e a define. A *estrutura* é usada para *seleção de ativo*. O *ativo* fornece a API.

![Composição de estrutura baseada em pacote](./media/packages/package-framework.png)

As duas principais estruturas baseadas em pacote usadas com o .NET Core são:

- `netstandard`
- `netcoreapp`

### <a name="net-standard"></a>.NET Standard

A estrutura .net Standard ([target Framework moniker](../standard/frameworks.md): `netstandard`) representa as APIs definidas por e criadas com base em [.net Standard](../standard/net-standard.md). Bibliotecas destinadas a execução em vários runtimes devem ter essa estrutura como alvo. Eles terão suporte em qualquer tempo de execução compatível com .NET Standard, como .NET Core, .NET Framework e mono/Xamarin. Cada um desses runtimes dá suporte a um conjunto de versões do .NET Standard, dependendo de quais APIs eles implementam.

A `netstandard` estrutura referencia implicitamente o [`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library) metapacote. Por exemplo, o seguinte arquivo de projeto do MSBuild indica que o `netstandard1.6`projeto tem como destino, que faz referência ao metapacote da [ `NETStandard.Library` versão 1,6](https://www.nuget.org/packages/NETStandard.Library/1.6.0) .

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.6</TargetFramework>
  </PropertyGroup>
</Project>
```

Ao adicionar o `<NetStandardImplicitPackageVersion>` elemento ao arquivo de projeto, que especifica implicitamente uma versão de metapacote, você pode especificar uma versão de estrutura inferior à versão do metapacote. O `<NetStandardImplicitPackageVersion>` elemento só é aplicável ao direcionar .NET Core e .net Standard. Por exemplo, o arquivo de projeto a seguir é válido.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

Pode parecer estranho apontar para `netstandard1.3`, mas use a versão 1.6.0 do `NETStandard.Library`. Esse é um caso de uso válido, pois o metapacote mantém o suporte para versões mais antigas do `netstandard`. Pode ser o caso de você já ter padronizado a versão 1.6.0 do metapacote e tê-la usado para todas as suas bibliotecas, que são voltadas para diversas versões do `netstandard`. Com essa abordagem, você só precisará restaurar a `NETStandard.Library` 1.6.0 e não versões anteriores.

O inverso não seria válido: direcionar `netstandard1.6` com a versão 1.3.0 do `NETStandard.Library`. Você não pode direcionar uma estrutura mais elevada com um metapacote menos elevado, visto que a versão do metapacote inferior não exporá os ativos para essa estrutura superior. O esquema de controle de versão para metapacotes declara que os metapacotes correspondem à versão mais alta da estrutura descrita por eles. Devido a esse esquema de controle de versão, a primeira versão do `NETStandard.Library` é v1.6.0, já que ele contém ativos `netstandard1.6`. (Para simetria com o exemplo anterior, v 1.3.0 é usado aqui, mas ele não existe de fato.)

### <a name="net-core-application"></a>Aplicativo .NET Core

A estrutura .NET Core ([target Framework moniker](../standard/frameworks.md): `netcoreapp`) representa os pacotes e as APIs associadas que acompanham a distribuição do .NET Core e o modelo de aplicativo de console que ele fornece. Aplicativos .NET Core devem usar essa estrutura, devido ao direcionamento do modelo de aplicativo de console, assim como as bibliotecas que devem ser executados apenas em .NET Core. Usar essa estrutura restringe a bibliotecas à execução apenas no .NET Core.

O metapacote `Microsoft.NETCore.App` é direcionado para a estrutura `netcoreapp`. Ele fornece acesso a ~60 bibliotecas, ~ 40 fornecida pelo pacote `NETStandard.Library` e mais ~20 adicionais. Você pode referenciar outras bibliotecas direcionadas ao `netcoreapp` ou estruturas compatíveis, como o `netstandard`, para obter acesso a APIs adicionais.

A maioria das bibliotecas adicionais fornecidas pelo `Microsoft.NETCore.App` também são direcionadas para `netstandard`, considerando que suas dependências foram atendidas por outras bibliotecas `netstandard`. Isso significa que bibliotecas `netstandard` também podem fazer referência a esses pacotes como dependências.
