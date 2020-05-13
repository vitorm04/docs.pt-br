---
ms.openlocfilehash: f24a29a00a1bff34a452c43716d76bf72ef277b5
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206230"
---
### <a name="resource-manifest-file-name-change"></a>Alteração de nome de arquivo de manifesto de recurso

A partir do .NET Core 3,0, no caso padrão, o MSBuild gera um nome de arquivo de manifesto diferente para os arquivos de recurso.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="change-description"></a>Descrição da alteração

Antes do .NET Core 3,0, se nenhum `LogicalName` `ManifestResourceName` metadado, ou `DependentUpon` foi especificado para um `EmbeddedResource` item no arquivo de projeto, o MSBuild gerou um nome de arquivo de manifesto no padrão `<RootNamespace>.<ResourceFilePathFromProjectRoot>.resources` . Se `RootNamespace` não estiver definido no arquivo de projeto, o padrão será o nome do projeto. Por exemplo, o nome de manifesto gerado para um arquivo de recurso chamado *Form1. resx* no diretório do projeto raiz era *MyProject. Form1. Resources*.

A partir do .NET Core 3,0, se um arquivo de recurso estiver colocalizado com um arquivo de origem com o mesmo nome (por exemplo, *Form1. resx* e *Form1.cs*), o MSBuild usará informações de tipo do arquivo de origem para gerar o nome do arquivo de manifesto no padrão `<Namespace>.<ClassName>.resources` . O namespace e o nome da classe são extraídos do primeiro tipo no arquivo de origem colocalizado. Por exemplo, o nome de manifesto gerado para um arquivo de recurso chamado *Form1. resx* que está colocalizado com um arquivo de origem chamado *Form1.cs* é *MyNamespace. Form1. Resources*. O importante a observar é que a primeira parte do nome do arquivo é diferente para as versões anteriores do .NET Core (*MyNamespace* em vez de *MyProject*).

> [!NOTE]
> Se você tiver `LogicalName` `ManifestResourceName` o, o ou os `DependentUpon` metadados especificados em um `EmbeddedResource` item no arquivo de projeto, essa alteração não afetará esse arquivo de recurso.

Essa alteração significativa foi introduzida com a adição da `EmbeddedResourceUseDependentUponConvention` Propriedade aos projetos do .NET Core. Por padrão, os arquivos de recurso não são explicitamente listados em um arquivo de projeto do .NET Core, portanto, não têm `DependentUpon` metadados para especificar como nomear o arquivo *. Resources* gerado. Quando `EmbeddedResourceUseDependentUponConvention` é definido como `true` , que é o padrão, o MSBuild procura um arquivo de origem colocalizado e extrai um namespace e um nome de classe desse arquivo. Se você definir `EmbeddedResourceUseDependentUponConvention` como `false` , o MSBuild gerará o nome do manifesto de acordo com o comportamento anterior, que combina `RootNamespace` e o caminho do arquivo relativo.

#### <a name="recommended-action"></a>Ação recomendada

Na maioria dos casos, nenhuma ação é necessária na parte do desenvolvedor e seu aplicativo deve continuar a funcionar. No entanto, se essa alteração interromper seu aplicativo, você poderá:

- Altere seu código para esperar o novo nome do manifesto.

- Cancele a nova Convenção de nomenclatura definindo `EmbeddedResourceUseDependentUponConvention` como `false` em seu arquivo de projeto.

  ```xml
  <PropertyGroup>
    <EmbeddedResourceUseDependentUponConvention>false</EmbeddedResourceUseDependentUponConvention>
  </PropertyGroup>
  ```

#### <a name="category"></a>Categoria

MSBuild

#### <a name="affected-apis"></a>APIs afetadas

N/D
