---
title: Controle de versão da linguagem C# – Guia de C#
description: Saiba como a versão c# do idioma é determinada com base no seu projeto e nas razões por trás dessa escolha. Saiba como substituir o padrão manualmente.
ms.date: 02/21/2020
ms.openlocfilehash: ef7275aad7638f52ecbfca1dfbdb962ae242fb48
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399535"
---
# <a name="c-language-versioning"></a>Controle de versão da linguagem C#

O compilador do C# mais recente determina uma versão da linguagem padrão com base nas estruturas de destino do projeto. O Visual Studio não fornece uma ui para alterar o valor, mas você pode alterá-lo editando o arquivo *csproj.* A escolha do padrão garante que você use a versão de idioma mais recente compatível com sua estrutura de destino. Você se beneficia do acesso aos recursos de idioma mais recentes compatíveis com o destino do seu projeto. Essa escolha padrão também garante que você não use um idioma que exija tipos ou comportamento em tempo de execução não disponível em sua estrutura de destino. Escolher uma versão de idioma mais recente do que o padrão pode causar erros difíceis de diagnosticar tempo de compilação e tempo de execução.

As regras deste artigo se aplicam ao compilador entregue com o Visual Studio 2019 ou o .NET Core 3.0 SDK. Os compiladores do C# que fazem parte da instalação do Visual Studio 2017 ou de versões anteriores do SDK do .NET Core são direcionados ao C# 7.0 por padrão.

C# 8.0 (e superior) é suportado apenas em .NET Core 3.x e versões mais recentes. Muitos dos recursos mais novos exigem recursos de biblioteca e tempo de execução introduzidos no .NET Core 3.x:

- A implementação padrão do membro da interface requer novos recursos no .NET Core 3.0 CLR.
- Os fluxos assíncronos requerem os novos tipos <xref:System.IAsyncDisposable?displayProperty=nameWithType> <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType>e <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>.
- Índices e faixas requerem <xref:System.Index?displayProperty=nameWithType> <xref:System.Range?displayProperty=nameWithType>os novos tipos e .
- Os tipos de referência anulados fazem uso de vários [atributos](../nullable-attributes.md) para fornecer melhores avisos. Esses atributos foram adicionados no .NET Core 3.0. Outros quadros de alvo não foram anotados com nenhum desses atributos. Isso significa que os avisos anulados podem não refletir com precisão problemas potenciais.

## <a name="defaults"></a>Padrões

O compilador determina um padrão com base nestas regras:

|Estrutura de destino|version|Padrão da versão da linguagem C#|
|----------------|-------|---------------------------|
|.NET Core|3.x|C# 8.0|
|.NET Core|2. x|C# 7.3|
|.NET Standard|2.1|C# 8.0|
|.NET Standard|2,0|C# 7.3|
|.NET Standard|1.x|C# 7.3|
|.NET Framework|all|C# 7.3|

Quando seu projeto se destina a uma estrutura de visualização que tem uma versão da linguagem correspondente da visualização, a versão de linguagem usada é a de visualização. Você usa os recursos mais recentes com essa visualização em qualquer ambiente, sem afetar projetos que visam uma versão lançada do .NET Core.

## <a name="override-a-default"></a>Substituir um padrão

Se precisar especificar sua versão do C# explicitamente, poderá fazer isso de várias maneiras:

- Edite manualmente o [arquivo de projeto](#edit-the-project-file).
- Definir a versão da linguagem [para vários projetos em um subdiretório](#configure-multiple-projects).
- Configure a [ `-langversion` opção compilador](compiler-options/langversion-compiler-option.md).

### <a name="edit-the-project-file"></a>Editar o arquivo de projeto

É possível definir a versão da linguagem em seu arquivo de projeto. Por exemplo, se você quiser explicitamente acesso às versões prévias dos recursos, adicione um elemento como este:

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

O valor `preview` usa a versão prévia mais recente da linguagem C# compatível com seu compilador.

### <a name="configure-multiple-projects"></a>Configurar vários projetos

Para configurar vários projetos, você pode criar um arquivo **Directory.Build.props** que contém o `<LangVersion>` elemento. Normalmente, você faz isso no diretório da solução. Adicione o seguinte a um arquivo **Directory.Build.props** em seu diretório de solução:

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

As compilações em todos os subdiretórios do diretório que contêm esse arquivo usarão a versão de pré-visualização C#. Para obter mais informações, confira o artigo sobre como [personalizar o build](/visualstudio/msbuild/customize-your-build).

## <a name="c-language-version-reference"></a>Referência à versão da linguagem C#

A tabela a seguir mostra todas as versões atuais da linguagem C#. Seu compilador pode não entender necessariamente todos os valores se for mais velho. Se você instalar o .NET Core 3.0 ou posterior, então você terá acesso a tudo listado.

|Valor|Significado|
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
|ISO-2|O compilador aceita apenas a sintaxe incluída no ISO/IEC 23270:2006 C# (2.0). |
|ISO-1|O compilador aceita apenas a sintaxe incluída no ISO/IEC 23270:2003 C# (1.0/1.2). |
