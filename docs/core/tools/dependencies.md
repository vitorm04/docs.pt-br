---
title: Gerenciamento de dependências das ferramentas do .NET Core
description: Explica como gerenciar suas dependências com as ferramentas do .NET Core.
ms.date: 03/06/2017
ms.openlocfilehash: 28280dc05e746cdef4e90870cd4cb528382c45bd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76787868"
---
# <a name="manage-dependencies-with-net-core-sdk-10"></a>Gerenciar dependências com o SDK do .NET Core 1,0

Com a mudança dos projetos do .NET Core de project.json para csproj e o MSBuild, também ocorreu um investimento significativo que resultou na unificação do arquivo de projeto e dos ativos que permitem o acompanhamento de dependências. Para projetos do .NET Core, isso é semelhante ao que o Project. JSON fazia. Não há nenhum arquivo JSON ou XML separado que rastreia dependências do NuGet. Com essa alteração, também apresentamos outro tipo de *referência* para a sintaxe csproj, chamada `<PackageReference>`.

Este documento descreve o novo tipo de referência. Ele também mostra como adicionar uma dependência de pacote usando esse novo tipo de referência para o seu projeto.

## <a name="the-new-packagereference-element"></a>O novo elemento \<PackageReference>

O `<PackageReference>` tem a estrutura básica mostrada a seguir:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

Se você estiver familiarizado com o MSBuild, ele será parecido com outros tipos de referência que já existem. A chave é a instrução `Include`, que especifica a ID do pacote que você deseja adicionar ao projeto. O elemento filho `<Version>` especifica a versão obtida. As versões são especificadas por [Regras de versão do NuGet](/nuget/create-packages/dependency-versions#version-ranges).

> [!NOTE]
> Se você não está familiarizado com a sintaxe `csproj` geral, é possível usar a documentação de [referência de projeto MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) para mais informações.

Pode-se adicionar uma dependência disponível somente em um destino específico usando condições como no exemplo a seguir:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

Isso significa que a dependência só será válida se o build estiver ocorrendo para esse destino específico. O `$(TargetFramework)` na condição é uma propriedade do MSBuild que está sendo definida no projeto. Para aplicativos .NET Core mais comuns, não será necessário fazer isso.

## <a name="add-a-dependency-to-the-project"></a>Adicionar uma dependência ao projeto

Adicionar uma dependência ao projeto é simples. Veja um exemplo de como adicionar a versão `9.0.1` do Json.NET ao seu projeto. Obviamente, isso se aplica a qualquer outra dependência NuGet.

Ao abrir o arquivo de projeto, você verá dois ou mais nós `<ItemGroup>`. Você perceberá que um dos nós já tem elementos `<PackageReference>` contidos nele. Você pode adicionar sua nova dependência a este nó ou criar uma nova; cabe a você, pois o resultado será o mesmo.

O exemplo a seguir usa o modelo padrão Descartado pelo `dotnet new console`. Este é um aplicativo de console simples. Ao abrir o projeto, você encontrará o `<ItemGroup>` já existente `<PackageReference>` nele. Adicione o seguinte a ele:

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

Depois disso, salve o projeto e execute o comando `dotnet restore` para instalar a dependência.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

O projeto completo tem esta aparência:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
  </ItemGroup>
</Project>
```

## <a name="remove-a-dependency-from-the-project"></a>Remover uma dependência do projeto

Para remover uma dependência do arquivo de projeto, simplesmente remova `<PackageReference>` do arquivo de projeto.
