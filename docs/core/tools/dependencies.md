---
title: Gerenciamento de dependências das ferramentas do .NET Core
description: Explica como gerenciar suas dependências com as ferramentas do .NET Core.
ms.date: 03/06/2017
ms.openlocfilehash: 916daca0240c10dc63ca96048590a426bc51d450
ms.sourcegitcommit: feb42222f1430ca7b8115ae45e7a38fc4a1ba623
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/02/2020
ms.locfileid: "76965614"
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
> Se você não estiver familiarizado com a sintaxe Project-File, consulte a documentação de [referência do projeto MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) para obter mais informações.

Use condições para adicionar uma dependência que está disponível somente em um destino específico, conforme mostrado no exemplo a seguir:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

A dependência só será válida se a compilação estiver acontecendo para o destino fornecido. O `$(TargetFramework)` na condição é uma propriedade do MSBuild que está sendo definida no projeto. Para aplicativos .NET Core mais comuns, não será necessário fazer isso.

## <a name="add-a-dependency-to-the-project"></a>Adicionar uma dependência ao projeto

Adicionar uma dependência ao projeto é simples. Veja um exemplo de como adicionar a versão `9.0.1` do Json.NET ao seu projeto. Obviamente, isso se aplica a qualquer outra dependência NuGet.

O arquivo de projeto tem dois ou mais nós de `<ItemGroup>`. Um dos nós já tem `<PackageReference>` elementos. Você pode adicionar sua nova dependência a este nó ou criar uma nova; o resultado será o mesmo.

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
