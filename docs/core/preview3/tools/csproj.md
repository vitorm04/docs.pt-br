---
title: "Referência csproj | .NET Core SDK"
description: "Saiba mais sobre as diferenças entre arquivos existentes e de csproj do .NET Core"
keywords: "referência, csproj, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 10/12/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: bdc29497-64f2-4d11-a21b-4097e0bdf5c9
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 1a0178cc5763f06213d45b9b3826c56ce970776c

---

# <a name="additions-to-csproj-format-for-net-core"></a>Adições ao formato csproj para .NET Core

Este documento descreve as alterações adicionadas aos arquivos csproj como parte da mudança do project.json para csproj e [MSBuild](https://github.com/Microsoft/MSBuild). Este documento descreve **apenas os deltas para arquivos não essenciais csproj**. Se precisar de mais informações sobre a sintaxe e a referência do arquivo de projeto geral, consulte a documentação [do arquivo de projeto MSBuild](). 

> ![OBSERVAÇÃO] Novas informações serão incluídas neste documento no futuro, por isso, verifique-o novamente para vê-las. 

## <a name="additions"></a>Adições

### <a name="packagereference"></a>PackageReference
Especifica uma dependência NuGet no projeto. O atributo `Include` especifica a ID do pacote. 

```xml
<PackageReference Include="<package-id>">
    <Version></Version>
    <PrivateAssets></PrivateAssets>
    <IncludeAssets></IncludeAssets>
    <ExcludeAssets></ExcludeAssets>
</PackageReference>
```

#### <a name="version"></a>Versão
`<Version>` especifica a versão do pacote para restauração. O elemento respeita as regras do esquema de controle de versão do NuGet.

#### <a name="includeassets"></a>IncludeAssets
O elemento filho `<IncludeAssets>` especifica quais ativos pertencem ao pacote especificado pelo pai `<PackageReference>` devem ser consumidos. 

O elemento pode conter um ou mais dos seguintes valores:

* Compilação – o conteúdo da pasta lib está disponível para compilação?
* Tempo de Execução – o conteúdo da pasta de tempo de execução é distribuído?
* ContentFiles – o conteúdo da pasta contentfiles é usado?
* Build – as propriedades/destinos na pasta build são usados?
* Nativo – o conteúdo de ativos nativos é copiado para a pasta de saída para o tempo de execução?
* Analisadores – os analisadores são usados?

Como alternativa, o elemento pode conter:

* Nenhum – nenhum dos valores acima é usado
* Todos – todos os valores acima são usados.

#### <a name="excludeassets"></a>ExcludeAssets
O elemento filho `<ExcludeAssets>` especifica quais ativos pertencem ao pacote especificado pelo pai `<PackageReference>` não devem ser consumidos.

O elemento pode conter um ou mais dos seguintes valores:

* Compilação – o conteúdo da pasta lib está disponível para compilação?
* Tempo de Execução – o conteúdo da pasta de tempo de execução é distribuído?
* ContentFiles – o conteúdo da pasta contentfiles é usado?
* Build – as propriedades/destinos na pasta build são usados?
* Nativo – o conteúdo de ativos nativos é copiado para a pasta de saída para o tempo de execução?
* Analisadores – os analisadores são usados?

Como alternativa, o elemento pode conter:

* Nenhum – nenhum dos valores acima é usado
* Todos – todos os valores acima são usados.

#### <a name="privateassets"></a>PrivateAssets
O elemento filho `<PrivateAssets>` especifica quais ativos pertencem ao pacote especificado pelo pai `<PackageReference>` devem ser consumidos, mas que eles não devem fluir para o próximo projeto. 

> [!NOTE]
> Esse é um novo termo para o elemento `SuppressParent` project.json/xproj. 

O elemento pode conter um ou mais dos seguintes valores:

* Compilação – o conteúdo da pasta lib está disponível para compilação?
* Tempo de Execução – o conteúdo da pasta de tempo de execução é distribuído?
* ContentFiles – o conteúdo da pasta contentfiles é usado?
* Build – as propriedades/destinos na pasta build são usados?
* Nativo – o conteúdo de ativos nativos é copiado para a pasta de saída para o tempo de execução?
* Analisadores – os analisadores são usados?

Como alternativa, o elemento pode conter:

* Nenhum – nenhum dos valores acima é usado
* Todos – todos os valores acima são usados.

### <a name="dotnetclitoolreference"></a>DotnetCliToolReference
O elemento `<DotnetCliToolReference>` especifica a ferramenta CLI que o usuário deseja restaurar no contexto do projeto. É uma substituição para o nó `tools` em `project.json`. 

#### <a name="version"></a>Versão
`<Version>` especifica a versão do pacote para restauração. O elemento respeita as regras do esquema de controle de versão do NuGet.

### <a name="runtimeidentifiers"></a>RuntimeIdentifiers
O elemento `<RuntimeIdentifiers>` permite especificar uma lista delimitada por ponto e vírgula de [Identificadores de Tempo de Execução](../../rid-catalog.md) para o projeto. Eles permitem publicar implantações autocontidas. 




<!--HONumber=Jan17_HO3-->


