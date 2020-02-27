---
title: Controle de versão da linguagem C# – Guia de C#
description: Saiba mais sobre como C# a versão de idioma é determinada com base no seu projeto e os motivos por trás dessa escolha. Saiba como substituir o padrão manualmente.
ms.date: 02/21/2020
ms.openlocfilehash: 2be76fdac471a7175b661d896b0da2910b3609f3
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626758"
---
# <a name="c-language-versioning"></a>Controle de versão da linguagem C#

O compilador do C# mais recente determina uma versão da linguagem padrão com base nas estruturas de destino do projeto. O Visual Studio não fornece uma interface do usuário para alterar o valor, mas você pode alterá-lo editando o arquivo *csproj* . A escolha do padrão garante que você use a versão de idioma mais recente compatível com a estrutura de destino. Você se beneficia do acesso aos recursos de linguagem mais recentes compatíveis com o destino do seu projeto. Essa opção padrão também garante que você não use uma linguagem que exija tipos ou comportamento de tempo de execução não disponível em sua estrutura de destino. Escolher uma versão de idioma mais recente do que o padrão pode causar dificuldade para diagnosticar erros de tempo de compilação e Runtime.

C#8,0 (e superior) tem suporte apenas no .NET Core 3. x e em versões mais recentes. Muitos dos recursos mais recentes exigem recursos de biblioteca e tempo de execução introduzidos no .NET Core 3. x:

- A implementação de membro de interface padrão requer novos recursos no .NET Core 3,0 CLR.
- Os fluxos assíncronos exigem os novos tipos <xref:System.IAsyncDisposable?displayProperty=nameWithType>, <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType>e <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>.
- Índices e intervalos exigem os novos tipos <xref:System.Index?displayProperty=nameWithType> e <xref:System.Range?displayProperty=nameWithType>.
- Os tipos de referência anuláveis fazem uso de vários [atributos](../nullable-attributes.md) para fornecer avisos melhores. Esses atributos foram adicionados no .NET Core 3,0. Outras estruturas de destino não foram anotadas com nenhum desses atributos. Isso significa que os avisos anuláveis podem não refletir com precisão possíveis problemas.

## <a name="defaults"></a>Padrões

O compilador determina um padrão com base nestas regras:

|Estrutura de destino|version|Padrão da versão da linguagem C#|
|----------------|-------|---------------------------|
|.NET Core|3.x|C# 8.0|
|.NET Core|2. x|C# 7.3|
|.NET Standard|2.1|C# 8.0|
|.NET Standard|2,0|C# 7.3|
|.NET Standard|1.x|C# 7.3|
|{1&gt;.NET Framework&lt;1}|all|C# 7.3|

Quando seu projeto se destina a uma estrutura de visualização que tem uma versão da linguagem correspondente da visualização, a versão de linguagem usada é a de visualização. Você usa os recursos mais recentes com essa visualização em qualquer ambiente, sem afetar projetos direcionados a uma versão lançada do .NET Core.

## <a name="override-a-default"></a>Substituir um padrão

Se precisar especificar sua versão do C# explicitamente, poderá fazer isso de várias maneiras:

- Edite manualmente o [arquivo de projeto](#edit-the-project-file).
- Definir a versão da linguagem [para vários projetos em um subdiretório](#configure-multiple-projects).
- Configurar a opção [`-langversion` do compilador](compiler-options/langversion-compiler-option.md).

### <a name="edit-the-project-file"></a>Editar o arquivo de projeto

É possível definir a versão da linguagem em seu arquivo de projeto. Por exemplo, se você quiser explicitamente acesso às versões prévias dos recursos, adicione um elemento como este:

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

O valor `preview` usa a versão prévia mais recente da linguagem C# compatível com seu compilador.

### <a name="configure-multiple-projects"></a>Configurar vários projetos

Para configurar vários projetos, você pode criar um arquivo **Directory. Build. props** que contém o elemento `<LangVersion>`. Normalmente, você faz isso no diretório da solução. Adicione o seguinte a um arquivo **Directory.Build.props** no diretório de solução:

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

As compilações em todos os subdiretórios do diretório que contém esse arquivo usarão C# a versão de visualização. Para obter mais informações, confira o artigo sobre como [personalizar o build](/visualstudio/msbuild/customize-your-build).

## <a name="c-language-version-reference"></a>Referência à versão da linguagem C#

A tabela a seguir mostra todas as versões atuais da linguagem C#. Seu compilador pode não entender necessariamente todos os valores se for mais antigo. Se você instalar o .NET Core 3,0 ou posterior, terá acesso a todos os itens listados.

|{1&gt;Valor&lt;1}|Significado|
|------------|-------------|
|preview|O compilador aceita todas as sintaxes de linguagem válidas da versão prévia mais recente.|
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
|ISO-2|O compilador aceita apenas a sintaxe que está incluída no ISO/IEC C# 23270:2006 (2,0). |
|ISO-1|O compilador aceita apenas a sintaxe que está incluída no ISO/IEC C# 23270:2003 (1.0/1.2). |
