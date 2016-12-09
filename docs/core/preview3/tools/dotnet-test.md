---
title: Comando dotnet-test | SDK do .NET Core
description: "O comando “dotnet test” é usado para executar testes de unidade em um determinado projeto."
keywords: dotnet-test, CLI, comando da CLI, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 10/07/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 3a0fa917-eb0a-4d7e-9217-d06e65455675
translationtype: Human Translation
ms.sourcegitcommit: 1a84c694945fe0c77468eb77274ab46618bccae6
ms.openlocfilehash: 66c9f949980612f6e21b6d441c004cc09f4eb7d3

---

#<a name="dotnet-test"></a>dotnet-test

## <a name="name"></a>Nome

`dotnet-test` – Driver de teste .NET

## <a name="synopsis"></a>Sinopse

`dotnet test [project] [--help] 
    [--settings] [--listTests] [--testCaseFilter] 
    [--testAdapterPath] [--logger] 
    [--configuration] [--output] [--framework] [--diag]
    [--noBuild]`  

## <a name="description"></a>Descrição

O comando `dotnet test` é usado para executar testes de unidade em um determinado projeto. Testes de unidade são projetos de biblioteca de classes que têm dependências na estrutura de teste da unidade (por exemplo, NUnit ou xUnit) e o executor de teste dotnet dessa estrutura de teste de unidade. Eles são empacotados como pacotes NuGet e são restaurados como dependências comuns para o projeto.

Projetos de teste também precisam especificar o executor de teste. Isso é especificado usando um elemento comum `<PackageReference>`, conforme mostrado no exemplo de arquivo de projeto a seguir:

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.0</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <Compile Include="**\*.cs" />
    <EmbeddedResource Include="**\*.resx" />
  </ItemGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.NETCore.App">
      <Version>1.0.1</Version>
    </PackageReference>
    <PackageReference Include="Microsoft.NET.Sdk">
      <Version>1.0.0-alpha-20161104-2</Version>
      <PrivateAssets>All</PrivateAssets>
    </PackageReference>
    <PackageReference Include="Microsoft.NET.Test.Sdk">
      <Version>15.0.0-preview-20161024-02</Version>
    </PackageReference>
    <PackageReference Include="xunit">
      <Version>2.2.0-beta3-build3402</Version>
    </PackageReference>
    <PackageReference Include="xunit.runner.visualstudio">
      <Version>2.2.0-beta4-build1188</Version>
    </PackageReference>
  </ItemGroup>

  <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
</Project>
```

## <a name="options"></a>Opções

`[project]`
    
Especifica um caminho para o projeto de teste. Se for omitido, o padrão será o diretório atual.

`-h|--help`

Imprime uma ajuda breve para o comando.

`-s | --settings <SETTINGS_FILE>`

Configurações para usar ao executar testes. 

`-lt | --listTests`

Lista todos os testes descobertos no projeto atual. 

`-tcf | --testCaseFilter <EXPRESSION>`

Filtra os testes no projeto atual usando a expressão especificada. 

`-tap | --testAdapterPath <TEST_ADAPTER_PATH>`

Usa os adaptadores de teste personalizado do caminho especificado nessa execução de teste. 

`--logger <LOGGER>`

Especificar um agente para resultados do teste. 

`-c|--configuration <Debug|Release>`

Configuração de build. O valor padrão é `Release`. 

`-o|--output [OUTPUT_DIRECTORY]`

Diretório no qual encontram-se os binários para execução.

`-f|--framework [FRAMEWORK]`

Procura os binários de teste para uma estrutura específica.

`-r|--runtime [RUNTIME_IDENTIFIER]`

Procure os binários de teste para o tempo de execução especificado.

`--noBuild` 

Não compila o projeto de teste antes de executá-lo. 

`-d | --diag <DIAGNOSTICS_FILE>`

Habilita o modo de diagnóstico para a plataforma de teste e grava mensagens de diagnóstico para o arquivo especificado. 

## <a name="examples"></a>Exemplos

Execute os testes no projeto no diretório atual:

`dotnet test` 

Execute os testes no projeto test1:

`dotnet test ~/projects/test1/test1.csproj` 

## <a name="see-also"></a>Consulte também

[Estruturas](../../../standard/frameworks.md)

[Catálogo de RID (Identificador de Tempo de Execução)](../../rid-catalog.md)



<!--HONumber=Nov16_HO3-->


