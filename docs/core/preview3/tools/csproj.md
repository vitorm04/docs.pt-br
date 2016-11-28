---
title: "Referência csproj | .NET Core SDK"
description: "Saiba mais sobre as diferenças entre arquivos existentes e de csproj do .NET Core"
keywords: "referência, csproj, .NET Core"
author: blackdwarf
ms.author: mairaw
manager: wpickett
ms.date: 10/12/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: bdc29497-64f2-4d11-a21b-4097e0bdf5c9
translationtype: Human Translation
ms.sourcegitcommit: 1a84c694945fe0c77468eb77274ab46618bccae6
ms.openlocfilehash: af32bc592762d7e8cb4e3b180656d9c3464df4a5

---

<a name="additions-to-csproj-format-for-net-core"></a>Adições ao formato csproj para .NET Core
----------------------------------------

# <a name="overview"></a>Visão Geral 
Este documento descreve as alterações adicionadas aos arquivos csproj como parte da mudança do project.json para csproj e [MSBuild](https://github.com/Microsoft/MSBuild). Este documento descreve **apenas os deltas para arquivos não essenciais csproj**. Se precisar de mais informações sobre a sintaxe e a referência do arquivo de projeto geral, consulte a documentação [do arquivo de projeto MSBuild](). 

> **Observação:** novas informações serão incluídas neste documento no futuro, por isso, verifique-o novamente para vê-las. 

# <a name="additions"></a>Adições

## <a name="packagereference"></a>PackageReference
Especifica uma dependência NuGet no projeto. O atributo `Include` especifica a ID do pacote. 

```xml
<PackageReference Include="<package-id>">
    <Version></Version>
    <PrivateAssets></PrivateAssets>
    <IncludeAssets></IncludeAssets>
    <ExcludeAssets></ExcludeAssets>
</PackageReference>
```

### <a name="version"></a>Versão
`<Version>` especifica a versão do pacote para restauração. O elemento respeita as regras do esquema de controle de versão do NuGet.

### <a name="includeassets"></a>IncludeAssets
O elemento filho `<IncludeAssets>` especifica quais ativos pertencem ao pacote especificado pelo pai `<PackageReference>` devem ser consumidos. 

O elemento pode conter um ou mais dos seguintes valores:

* Compilação � Os conteúdos da pasta lib estão disponíveis para compilação?
* Tempo de Execução � Os conteúdos da pasta de tempo de execução são distribuídos?
* ContentFiles � Os conteúdos da pasta contentfiles são usados?
* Build � As propriedades/destinos na pasta build são usados?
* Nativo – Os conteúdos de ativos nativos são copiados para a pasta de saída para o tempo de execução?
* Analisadores � Os analisadores são usados?

Como alternativa, o elemento pode conter:

* Nenhum � nenhum dos valores acima é usado
* Todos � todos os valores acima são usados.

### <a name="excludeassets"></a>ExcludeAssets
O elemento filho `<ExcluseAssets>` especifica quais ativos pertencem ao pacote especificado pelo pai `<PackageReference>` não devem ser consumidos.

O elemento pode conter um ou mais dos seguintes valores:

* Compilação � Os conteúdos da pasta lib estão disponíveis para compilação?
* Tempo de Execução � Os conteúdos da pasta de tempo de execução são distribuídos?
* ContentFiles � Os conteúdos da pasta contentfiles são usados?
* Build � As propriedades/destinos na pasta build são usados?
* Nativo – Os conteúdos de ativos nativos são copiados para a pasta de saída para o tempo de execução?
* Analisadores � Os analisadores são usados?

Como alternativa, o elemento pode conter:

* Nenhum � nenhum dos valores acima é usado
* Todos � todos os valores acima são usados.

### <a name="privateassets"></a>PrivateAssets
O elemento filho `<PrivateAssets>` especifica quais ativos pertencem ao pacote especificado pelo pai `<PackageReference>` devem ser consumidos, mas que eles não devem fluir para o próximo projeto. 

> **Observação:** esse é um novo termo para o elemento `SupressParent` project.json/xproj. 

O elemento pode conter um ou mais dos seguintes valores:

* Compilação � Os conteúdos da pasta lib estão disponíveis para compilação?
* Tempo de Execução � Os conteúdos da pasta de tempo de execução são distribuídos?
* ContentFiles � Os conteúdos da pasta contentfiles são usados?
* Build � As propriedades/destinos na pasta build são usados?
* Nativo – Os conteúdos de ativos nativos são copiados para a pasta de saída para o tempo de execução?
* Analisadores � Os analisadores são usados?

Como alternativa, o elemento pode conter:

* Nenhum � nenhum dos valores acima é usado
* Todos � todos os valores acima são usados.

## <a name="dotnetclitoolreference"></a>DotnetCliToolReference
O elemento `<DotnetCliToolReference>` especifica a ferramenta CLI que o usuário deseja restaurar no contexto do projeto. É uma substituição para o nó `tools` em `project.json`. 

### <a name="version"></a>Versão
`<Version>` especifica a versão do pacote para restauração. O elemento respeita as regras do esquema de controle de versão do NuGet.

## <a name="runtimeidentifiers"></a>RuntimeIdentifiers
O elemento `<RuntimeIdentifiers>` permite especificar uma lista delimitada por ponto e vírgula de [Identificadores de Tempo de Execução](../../rid-catalog.md) para o projeto. Eles permitem publicar implantações autocontidas. 




<!--HONumber=Nov16_HO3-->


