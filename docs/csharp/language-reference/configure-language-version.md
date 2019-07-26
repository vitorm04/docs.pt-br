---
title: Controle de versão da linguagem C# – Guia de C#
description: Saiba mais como a versão da linguagem C# é determinada com base em seu projeto e os diferentes valores para os quais você pode ajustá-la manualmente.
ms.date: 07/10/2019
ms.openlocfilehash: e35fdf2bcdb1a31b752c760f3f6df59232e498a4
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68236092"
---
# <a name="c-language-versioning"></a>Controle de versão da linguagem C#

O compilador C# determina uma versão da linguagem padrão com base na estrutura de destino ou nas estruturas de seu projeto. Isso ocorre porque a linguagem C# pode ter recursos que dependem de tipos ou de componentes de tempo de execução que não estão disponíveis em todas as implementações do .NET. Com isso, independentemente do destino no qual seu projeto é criado, você obtém a versão da linguagem mais compatível por padrão.

## <a name="defaults"></a>Padrão

O compilador determina um padrão com base nestas regras:

|Estrutura de destino|version|Padrão da versão da linguagem C#|
|----------------|-------|---------------------------|
|.NET Core|3.x|C# 8.0|
|.NET Core|2.x|C# 7.3|
|.NET Standard|all|C# 7.3|
|.NET Framework|all|C# 7.3|

## <a name="default-for-previews"></a>Padrão para versões prévias

Quando seu projeto se destina a uma estrutura de visualização que tem uma versão da linguagem correspondente da visualização, a versão de linguagem usada é a de visualização. Com isso, é possível usar os recursos mais recentes que são garantidos para trabalhar com essa versão prévia em qualquer ambiente sem afetar seus projetos que direcionam uma versão lançada do .NET Core.

## <a name="overriding-a-default"></a>Substituir um padrão

Se precisar especificar sua versão do C# explicitamente, poderá fazer isso de várias maneiras:

- Edite manualmente o [arquivo de projeto](#edit-the-project-file).
- Definir a versão da linguagem [para vários projetos em um subdiretório](#configure-multiple-projects).
- Configurar a opção [`-langversion` do compilador](compiler-options/langversion-compiler-option.md)

### <a name="edit-the-project-file"></a>Editar o arquivo de projeto

É possível definir a versão da linguagem em seu arquivo de projeto. Por exemplo, se você quisesse explicitamente acesso às versões prévias do recurso, poderia adicionar um elemento como este:

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

O valor `preview` usa a versão prévia mais recente da linguagem C# compatível com seu compilador.

### <a name="configure-multiple-projects"></a>Configurar vários projetos

Crie um arquivo **Directory.Build.props** que contém o elemento `<LangVersion>` para configurar vários diretórios. Normalmente, você faz isso no diretório da solução. Adicione o seguinte a um arquivo **Directory.Build.props** no diretório de solução:

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

Agora, os builds de todo subdiretório do diretório que contém esse arquivo usarão a versão do C# da versão prévia. Para obter mais informações, confira o artigo sobre como [personalizar o build](/visualstudio/msbuild/customize-your-build).

## <a name="c-language-version-reference"></a>Referência à versão da linguagem C#

A tabela a seguir mostra todas as versões atuais da linguagem C#. Seu compilador talvez não entenda necessariamente todo valor se for mais antigo. Se instalar o .NET Core 3.0, você terá acesso a tudo que está listado.

|Valor|Significado|
|------------|-------------|
|versão prévia|O compilador aceita todas as sintaxes de linguagem válidas da versão prévia mais recente.|
|mais recente|O compilador aceita a sintaxe da versão lançada mais recente do compilador (incluindo a versão secundária).|
|latestMajor|O compilador aceita a sintaxe da versão principal mais recente lançada do compilador.|
|8.0|O compilador aceita somente a sintaxe incluída no C# 8.0 ou inferior.|
|7.3|O compilador aceita somente a sintaxe incluída no C# 7.3 ou inferior.|
|7.2|O compilador aceita somente a sintaxe incluída no C# 7.2 ou inferior.|
|7.1|O compilador aceita somente a sintaxe incluída no C# 7.1 ou inferior.|
|7|O compilador aceita somente a sintaxe incluída no C# 7.0 ou inferior.|
|6|O compilador aceita somente a sintaxe incluída no C# 6.0 ou inferior.|
|5|O compilador aceita somente a sintaxe incluída no C# 5.0 ou inferior.|
|4|O compilador aceita somente a sintaxe incluída no C# 4.0 ou inferior.|
|3|O compilador aceita somente a sintaxe incluída no C# 3.0 ou inferior.|
|ISO-2|O compilador aceita somente a sintaxe incluída no ISO/IEC 23270:2006 C# (2.0) |
|ISO-1|O compilador aceita somente a sintaxe incluída no ISO/IEC 23270:2003 C# (1.0/1.2) |
