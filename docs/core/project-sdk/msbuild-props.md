---
title: Propriedades MSBuild para Microsoft.NET.Sdk
description: Referência para as propriedades MSBuild que são compreendidas pelo .NET Core SDK.
ms.date: 02/14/2020
ms.topic: reference
ms.openlocfilehash: d4a204a1e0216313418d278ec3bd333f72db8751
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399178"
---
# <a name="msbuild-properties-for-net-core-sdk-projects"></a>Propriedades MSBuild para projetos .NET Core SDK

Esta página descreve as propriedades mSBuild para configurar projetos .NET Core.

> [!NOTE]
> Esta página é um trabalho em andamento e não lista todas as propriedades úteis do MSBuild para o .NET Core SDK. Para obter uma lista de propriedades comuns do MSBuild, consulte [Propriedades Comuns do MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).

## <a name="framework-properties"></a>Propriedades do framework

- [TargetFramework](#targetframework)
- [TargetFrameworks](#targetframeworks)
- [NetStandardImplicitPackageVersion](#netstandardimplicitpackageversion)

### <a name="targetframework"></a>TargetFramework

A `TargetFramework` propriedade especifica a versão de quadro de destino para o aplicativo, que faz referência implícita a um [metapacote](../packages.md#metapackages). Para obter uma lista de apelidos de quadro de destino válidos, consulte [Frameworks target em projetos estilo SDK](../../standard/frameworks.md#supported-target-framework-versions).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

Para obter mais informações, consulte [Frameworks target em projetos no estilo SDK](../../standard/frameworks.md).

### <a name="targetframeworks"></a>TargetFrameworks

Use `TargetFrameworks` a propriedade quando quiser que seu aplicativo tenha como alvo várias plataformas. Para obter uma lista de apelidos de quadro de destino válidos, consulte [Frameworks target em projetos estilo SDK](../../standard/frameworks.md#supported-target-framework-versions).

> [!NOTE]
> Esta propriedade é `TargetFramework` ignorada se (singular) for especificado.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
  </PropertyGroup>
</Project>
```

Para obter mais informações, consulte [Frameworks target em projetos no estilo SDK](../../standard/frameworks.md).

### <a name="netstandardimplicitpackageversion"></a>NetStandardImplicitPackageVersion

> [!NOTE]
> Esta propriedade só se `netstandard1.x`aplica a projetos usando . Não se aplica a projetos `netstandard2.x`que usam.

Use `NetStandardImplicitPackageVersion` a propriedade quando quiser especificar uma versão de framework menor que a versão [metapacote.](../packages.md#metapackages) O arquivo do projeto no `netstandard1.3` exemplo a seguir é alvo, mas usa a versão 1.6.0 de `NETStandard.Library`.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

## <a name="publish-properties"></a>Publicar propriedades

- [RuntimeIdentifier](#runtimeidentifier)
- [RuntimeIdentifiers](#runtimeidentifiers)
- [UseAppHost](#useapphost)

### <a name="runtimeidentifier"></a>RuntimeIdentifier

A `RuntimeIdentifier` propriedade permite especificar um único [identificador de tempo de execução (RID)](../rid-catalog.md) para o projeto. O RID permite a publicação de uma implantação autossuficiente.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
  </PropertyGroup>
</Project>
```

### <a name="runtimeidentifiers"></a>RuntimeIdentifiers

A `RuntimeIdentifiers` propriedade permite especificar uma lista delimitada de [rids (runtime) deponto e](../rid-catalog.md) ponto e vírgula para o projeto. Use esta propriedade se você precisar publicar para vários tempos de execução. `RuntimeIdentifiers`é usado no momento de restauração para garantir que os ativos certos estejam no gráfico.

> [!TIP]
> `RuntimeIdentifier`(singular) pode fornecer compilações mais rápidas quando apenas um único tempo de execução é necessário.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

### <a name="useapphost"></a>UseAppHost

A `UseAppHost` propriedade foi introduzida na versão 2.1.400 do .NET Core SDK. Ele controla se um executável nativo é criado ou não para uma implantação. Um executável nativo é necessário para implantações independentes.

Nas versões .NET Core 3.0 e posteriores, um executável dependente de estrutura é criado por padrão. Defina `UseAppHost` a `false` propriedade para desativar a geração do executável.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <UseAppHost>false</UseAppHost>
  </PropertyGroup>
</Project>
```

Para obter mais informações sobre a implantação, consulte [a implantação do aplicativo .NET Core](../deploying/index.md).

## <a name="compile-properties"></a>Compilar propriedades

### <a name="langversion"></a>LangVersion

A `LangVersion` propriedade permite especificar uma versão específica do idioma de programação. Por exemplo, se você quiser acessar os `LangVersion` `preview`recursos de visualização C#, definido como .

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <LangVersion>preview</LangVersion>
  </PropertyGroup>
</Project>
```

Para obter mais informações, consulte [a versão do idioma C#](../../csharp/language-reference/configure-language-version.md#override-a-default).

## <a name="nuget-packages"></a>Pacotes NuGet

- [PackageReference](#packagereference)
- [AssetTargetFallback](#assettargetfallback)

### <a name="packagereference"></a>PackageReference

O `PackageReference` item permite especificar uma dependência nuGet. Por exemplo, você pode querer referenciar um único pacote em vez de um [metapacote](../packages.md#metapackages). O atributo `Include` especifica a ID do pacote. O trecho do arquivo do projeto no exemplo a seguir faz referência ao pacote [System.Runtime.](https://www.nuget.org/packages/System.Runtime/)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

Para obter mais informações, consulte [referências de pacote em arquivos de projeto](/nuget/consume-packages/package-references-in-project-files).

### <a name="assettargetfallback"></a>AssetTargetFallback

A `AssetTargetFallback` propriedade permite que você especifique versões de estrutura compatíveis adicionais para projetos que seu projeto faz referência sustais e pacotes NuGet que seu projeto consome. Por exemplo, se você especificar `PackageReference` uma dependência de pacote usando, mas esse `TargetFramework`pacote `AssetTargetFallback` não contiver ativos compatíveis com os de seus projetos, a propriedade entra em jogo. A compatibilidade do pacote referenciado é recontrolada usando cada estrutura `AssetTargetFallback`de destino especificada em .

Você pode `AssetTargetFallback` definir a propriedade como uma ou mais [versões de quadro-alvo](../../standard/frameworks.md#supported-target-framework-versions).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <PropertyGroup>
    <AssetTargetFallback>net461</AssetTargetFallback>
  </PropertyGroup>
</Project>
```

### <a name="pack-and-restore-targets"></a>Embalar e restaurar alvos

O MSBuild 15.1 introduziu `pack` e `restore` tem como objetivos criar e restaurar pacotes NuGet como parte de uma compilação. Para obter informações sobre as propriedades MSBuild para esses alvos, incluindo `PackageTargetFallback`, consulte [NuGet pack e restore como alvos MSBuild](/nuget/reference/msbuild-targets).

## <a name="see-also"></a>Confira também

- [Referência de esquema MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [Propriedades Comuns do MSBuild](/visualstudio/msbuild/common-msbuild-project-properties)
- [Propriedades MSBuild para pacote NuGet](/nuget/reference/msbuild-targets#pack-target)
- [Propriedades mSBuild para restauração NuGet](/nuget/reference/msbuild-targets#restore-properties)
- [Personalize uma compilação](/visualstudio/msbuild/customize-your-build)
