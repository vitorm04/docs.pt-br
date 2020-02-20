---
ms.openlocfilehash: 276268d31670b5e7dcd0ae9c0b7a61c3c38ca663
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451871"
---
### <a name="resource-manifest-file-names"></a>Nomes de arquivo de manifesto de recurso

A partir do .NET Core 3,0, o nome do arquivo de manifesto do recurso gerado foi alterado.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="change-description"></a>Alterar descrição

Antes do .NET Core 3,0, quando os metadados do [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) eram definidos para um arquivo de recurso ( *. resx*) no arquivo de projeto do MSBuild, o nome do manifesto gerado era *namespace. ClassName. Resources*. Quando [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) não foi definido, o nome de manifesto gerado era *namespace. ClassName. FolderPathRelativeToRoot. Culture. Resources*.

A partir do .NET Core 3,0, quando um arquivo *. resx* é colocado com um arquivo de origem com o mesmo nome, por exemplo, em aplicativos Windows Forms, o nome do manifesto do recurso é gerado a partir do nome completo do primeiro tipo no arquivo de origem. Por exemplo, se *Type.cs* estiver colocalizado com *Type. resx*, o nome de manifesto gerado será *namespace. ClassName. Resources*. No entanto, se você modificar qualquer um dos atributos na propriedade `EmbeddedResource` para o arquivo *. resx* , o nome do arquivo de manifesto gerado poderá ser diferente:

- Se o atributo `LogicalName` na propriedade `EmbeddedResource` for definido, esse valor será usado como o nome do arquivo de manifesto do recurso.

  Exemplos:

  ```xml
  <EmbeddedResource Include="X.resx" LogicalName="SomeName.resources" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" LogicalName="SomeName.resources" />
  ```

  **Nome do arquivo de manifesto de recurso gerado**: *somename. Resources* (independentemente do nome do arquivo *. resx* ou da cultura ou de qualquer outro metadado).

- Se `LogicalName` não estiver definido, mas o atributo `ManifestResourceName` na propriedade `EmbeddedResource` for definido, seu valor, combinado com a extensão de arquivo *. Resources*, será usado como o nome do arquivo de manifesto de recurso.

  Exemplos:

  ```xml
  <EmbeddedResource Include="X.resx" ManifestResourceName="SomeName" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" ManifestResourceName="SomeName.fr-FR" />
  ```

  **Nome do arquivo de manifesto de recurso gerado**: *somename. Resources* ou *somename.fr-fr. Resources*.

- Se as regras anteriores não se aplicarem e o atributo `DependentUpon` no elemento `EmbeddedResource` for definido como um arquivo de origem, o nome do tipo da primeira classe no arquivo de origem será usado no nome do arquivo de manifesto do recurso. Mais especificamente, o nome de arquivo gerado é *namespace. Classname\[. Culture]. Resources*.

  Exemplos:

  ```xml
  <EmbeddedResource Include="X.resx" DependentUpon="MyTypes.cs">
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" DependentUpon="MyTypes.cs">
  ```

  **Nome do arquivo de manifesto de recurso gerado**: *namespace. ClassName. Resources* ou *namespace.ClassName.fr-fr. Resources* (em que `Namespace.Classname` é o nome da primeira classe em *myTypes.cs*).

- Se as regras anteriores não se aplicarem, `EmbeddedResourceUseDependentUponConvention` é `true` (o padrão para .NET Core) e há um arquivo de origem colocalizado com um arquivo *. resx* que tem o mesmo nome de arquivo base, o arquivo *. resx* é tornado dependente do arquivo de origem correspondente e o nome gerado é o mesmo da regra anterior. Essa é a regra de "configurações padrão" para projetos do .NET Core.
  
  Exemplos:
  
  Os arquivos *myTypes.cs* e *myTypes. resx* ou *myTypes.fr-fr. resx* existem na mesma pasta.
  
  **Nome do arquivo de manifesto de recurso gerado**: *namespace. ClassName. Resources* ou *namespace.ClassName.fr-fr. Resources* (em que `Namespace.Classname` é o nome da primeira classe em *myTypes.cs*).
    
- Se nenhuma das regras anteriores se aplicar, o nome do arquivo de manifesto de recurso gerado será *RootNamespace. RelativePathWithDotsForSlashes.\[Culture.] recursos*do. O caminho relativo é o valor do atributo `Link` do elemento `EmbeddedResource` se ele estiver definido. Caso contrário, o caminho relativo é o valor do atributo `Identity` do elemento `EmbeddedResource`. No Visual Studio, esse é o caminho da raiz do projeto para o arquivo em Gerenciador de Soluções.

#### <a name="recommended-action"></a>Ação recomendada

Se você não estiver satisfeito com os nomes de manifesto gerados, poderá:

- Modifique os metadados do arquivo de recursos de acordo com uma das regras de nomenclatura descritas anteriormente.

- Defina `EmbeddedResourceUseDependentUponConvention` para `false` no arquivo de projeto para recusar totalmente a nova Convenção:

   ```xml
   <EmbeddedResourceUseDependentUponConvention>false</EmbeddedResourceUseDependentUponConvention>
   ```

   > [!NOTE]
   > Se os atributos `LogicalName` ou `ManifestResourceName` estiverem presentes, seus valores ainda serão usados para o nome de arquivo gerado.

#### <a name="category"></a>Categoria

MSBuild

#### <a name="affected-apis"></a>APIs afetadas

N/D
