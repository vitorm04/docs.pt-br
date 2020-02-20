---
title: Propriedades do MSBuild para Microsoft. NET. Sdk
description: Referência para as propriedades do MSBuild que são compreendidas pelo SDK do .NET Core.
ms.date: 02/14/2020
ms.topic: reference
ms.openlocfilehash: 00d9152d864ac0727a511f4c3c15abba82aab904
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503814"
---
# <a name="msbuild-properties-for-net-core-sdk-projects"></a>Propriedades do MSBuild para projetos SDK do .NET Core

Esta página descreve as propriedades do MSBuild para configurar projetos do .NET Core.

> [!NOTE]
> Esta página é um trabalho em andamento e não lista todas as propriedades de MSBuild úteis para o SDK do .NET Core. Para obter uma lista de propriedades comuns do MSBuild, consulte [Propriedades comuns do MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).

## <a name="framework-properties"></a>Propriedades da estrutura

- [TargetFramework](#targetframework)
- [TargetFrameworks](#targetframeworks)
- [NetStandardImplicitPackageVersion](#netstandardimplicitpackageversion)

### <a name="targetframework"></a>TargetFramework

A propriedade `TargetFramework` especifica a versão do Framework de destino para o aplicativo, que referencia implicitamente um [metapacote](../packages.md#metapackages). Para obter uma lista de monikers de estrutura de destino válidos, consulte [estruturas de destino em projetos em estilo SDK](../../standard/frameworks.md#supported-target-framework-versions).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

Para obter mais informações, consulte [estruturas de destino em projetos em estilo SDK](../../standard/frameworks.md).

### <a name="targetframeworks"></a>TargetFrameworks

Use a propriedade `TargetFrameworks` quando desejar que seu aplicativo direcione várias plataformas. Para obter uma lista de monikers de estrutura de destino válidos, consulte [estruturas de destino em projetos em estilo SDK](../../standard/frameworks.md#supported-target-framework-versions).

> [!NOTE]
> Essa propriedade será ignorada se `TargetFramework` (singular) for especificado.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
  </PropertyGroup>
</Project>
```

Para obter mais informações, consulte [estruturas de destino em projetos em estilo SDK](../../standard/frameworks.md).

### <a name="netstandardimplicitpackageversion"></a>NetStandardImplicitPackageVersion

> [!NOTE]
> Essa propriedade só se aplica a projetos que usam `netstandard1.x`. Ele não se aplica a projetos que usam `netstandard2.x`.

Use a propriedade `NetStandardImplicitPackageVersion` quando desejar especificar uma versão de estrutura inferior à versão do [metapacote](../packages.md#metapackages) . O arquivo de projeto no exemplo a seguir tem como destino `netstandard1.3`, mas usa a versão 1.6.0 do `NETStandard.Library`.

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

A propriedade `RuntimeIdentifier` permite que você especifique um único [identificador de tempo de execução (RID)](../rid-catalog.md) para o projeto. O RID permite a publicação de uma implantação autossuficiente.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
  </PropertyGroup>
</Project>
```

### <a name="runtimeidentifiers"></a>RuntimeIdentifiers

A propriedade `RuntimeIdentifiers` permite especificar uma lista delimitada por ponto-e-vírgula de [RIDs (identificadores de tempo de execução)](../rid-catalog.md) para o projeto. Use essa propriedade se você precisar publicar para vários tempos de execução. `RuntimeIdentifiers` é usado no momento da restauração para garantir que os ativos corretos estejam no grafo.

> [!TIP]
> `RuntimeIdentifier` (singular) pode fornecer compilações mais rápidas quando apenas um único tempo de execução é necessário.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

### <a name="useapphost"></a>UseAppHost

A propriedade `UseAppHost` foi introduzida na versão 2.1.400 do SDK do .NET Core. Ele controla se um executável nativo é criado para uma implantação ou não. Um executável nativo é necessário para implantações independentes.

No .NET Core 3,0 e versões posteriores, um executável dependente da estrutura é criado por padrão. Defina a propriedade `UseAppHost` como `false` para desabilitar a geração do executável.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <UseAppHost>false</UseAppHost>
  </PropertyGroup>
</Project>
```

Para obter mais informações sobre a implantação, consulte [implantação de aplicativos do .NET Core](../deploying/index.md).

## <a name="compile-properties"></a>Compilar propriedades

### <a name="langversion"></a>LangVersion

A propriedade `LangVersion` permite especificar uma versão de linguagem de programação específica. Por exemplo, se você quiser acesso a C# recursos de visualização, defina `LangVersion` como `preview`.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <LangVersion>preview</LangVersion>
  </PropertyGroup>
</Project>
```

Para obter mais informações, consulte [ C# controle de versão de idioma](../../csharp/language-reference/configure-language-version.md#override-a-default).

## <a name="nuget-packages"></a>Pacotes NuGet

- [PackageReference](#packagereference)

### <a name="packagereference"></a>PackageReference

O `PackageReference` item permite que você especifique uma dependência do NuGet. Por exemplo, talvez você queira fazer referência a um único pacote em vez de um [metapacote](../packages.md#metapackages). O atributo `Include` especifica a ID do pacote. O trecho do arquivo de projeto no exemplo a seguir faz referência ao pacote [System. Runtime](https://www.nuget.org/packages/System.Runtime/) .

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

Para obter mais informações, consulte [referências de pacote em arquivos de projeto](/nuget/consume-packages/package-references-in-project-files).

### <a name="pack-and-restore-targets"></a>Empacotar e restaurar destinos

O MSBuild 15,1 introduziu `pack` e `restore` destinos para criar e restaurar pacotes NuGet como parte de uma compilação. Para obter informações sobre as propriedades do MSBuild para esses destinos, incluindo `PackageTargetFallback`, consulte [o NuGet Pack e restaurar como destinos do MSBuild](/nuget/reference/msbuild-targets).

## <a name="see-also"></a>Confira também

- [Referência de esquema do MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [Propriedades comuns do MSBuild](/visualstudio/msbuild/common-msbuild-project-properties)
- [Propriedades do MSBuild para o pacote NuGet](/nuget/reference/msbuild-targets#pack-target)
- [Propriedades do MSBuild para restauração do NuGet](/nuget/reference/msbuild-targets#restore-properties)
- [Personalizar uma compilação](/visualstudio/msbuild/customize-your-build)
