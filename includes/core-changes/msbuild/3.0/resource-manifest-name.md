---
ms.openlocfilehash: 16ee73bfc0ab33b04ea3e2fa6d0eec521a9b8634
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78968253"
---
### <a name="resource-manifest-file-names"></a>Nomes de arquivos de manifesto de recursos

A partir do .NET Core 3.0, o nome do arquivo de manifesto de recurso gerado foi alterado.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="change-description"></a>Descrição da alteração

Antes do .NET Core 3.0, quando [dependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) metadata foi definido para um arquivo de recurso *(.resx)* no arquivo do projeto MSBuild, o nome do manifesto gerado era *Namespace.Classname.resources*. Quando [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) não foi definido, o nome do manifesto gerado era *Namespace.Classname.FolderPathRelativeToRoot.Culture.resources*.

A partir do .NET Core 3.0, quando um arquivo *.resx* é localizado com um arquivo de origem de mesmo nome, por exemplo, nos aplicativos Do Windows Forms, o nome do manifesto de recursos é gerado a partir do nome completo do primeiro tipo no arquivo de origem. Por exemplo, se *Type.cs* for localizado com *Type.resx,* o nome do manifesto gerado é *Namespace.Classname.resources*. No entanto, se você modificar `EmbeddedResource` qualquer um dos atributos na propriedade para o arquivo *.resx,* o nome do arquivo manifesto gerado pode ser diferente:

- Se `LogicalName` o atributo na `EmbeddedResource` propriedade for definido, esse valor será usado como o nome do arquivo manifesto de recursos.

  Exemplos:

  ```xml
  <EmbeddedResource Include="X.resx" LogicalName="SomeName.resources" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" LogicalName="SomeName.resources" />
  ```

  **Nome do arquivo de manifesto de recursos gerado**: *SomeName.resources* (independentemente do nome ou cultura do arquivo *.resx* ou qualquer outro metadados).

- Se `LogicalName` não for definido, mas o atributo `ManifestResourceName` na `EmbeddedResource` propriedade for definido, seu valor, combinado com a extensão de arquivo *.resources,* é usado como o nome do arquivo manifesto de recursos.

  Exemplos:

  ```xml
  <EmbeddedResource Include="X.resx" ManifestResourceName="SomeName" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" ManifestResourceName="SomeName.fr-FR" />
  ```

  **Nome do arquivo de manifesto de recursos gerado:** *SomeName.resources* ou *SomeName.fr-FR.resources*.

- Se as regras anteriores não `DependentUpon` se aplicarem e o atributo no `EmbeddedResource` elemento for definido como um arquivo de origem, o nome de tipo da primeira classe no arquivo de origem será usado no nome do arquivo manifesto de recursos. Mais especificamente, o nome do arquivo gerado é *\[Namespace.Classname . Cultura].recursos*.

  Exemplos:

  ```xml
  <EmbeddedResource Include="X.resx" DependentUpon="MyTypes.cs">
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" DependentUpon="MyTypes.cs">
  ```

  **Nomea** *namespace.classname.resources* ou *recursos Namespace.Classname.fr-FR.(onde* `Namespace.Classname` está o nome da primeira classe em *MyTypes.cs*).

- Se as regras anteriores `EmbeddedResourceUseDependentUponConvention` não `true` se aplicarem, é (o padrão para .NET Core), e há um arquivo de origem localizado com um arquivo *.resx* que tem o mesmo nome de arquivo base, o arquivo *.resx* é feito dependendo do arquivo de origem correspondente, e o nome gerado é o mesmo que na regra anterior. Esta é a regra "configurações padrão" para projetos .NET Core.
  
  Exemplos:
  
  Os *arquivos MyTypes.cs* e *MyTypes.resx* ou *MyTypes.fr-FR.resx* existem na mesma pasta.
  
  **Nomea** *namespace.classname.resources* ou *recursos Namespace.Classname.fr-FR.(onde* `Namespace.Classname` está o nome da primeira classe em *MyTypes.cs*).

- Se nenhuma das regras anteriores se aplicar, o nome do arquivo de manifesto de recurso gerado é *RootNamespace.RelativePathWithDotsForSlashes.\[ Cultura.] recursos*. O caminho relativo é `Link` o `EmbeddedResource` valor do atributo do elemento se ele estiver definido. Caso contrário, o caminho relativo `Identity` é `EmbeddedResource` o valor do atributo do elemento. No Visual Studio, este é o caminho da raiz do projeto para o arquivo no Solution Explorer.

#### <a name="recommended-action"></a>Ação recomendada

Se você não está satisfeito com os nomes manifestos gerados, você pode:

- Modifique os metadados do arquivo de recursos de acordo com uma das regras de nomeação descritas anteriormente.

- `EmbeddedResourceUseDependentUponConvention` Defina `false` em seu arquivo de projeto para desativar totalmente a nova convenção:

   ```xml
   <EmbeddedResourceUseDependentUponConvention>false</EmbeddedResourceUseDependentUponConvention>
   ```

   > [!NOTE]
   > Se `LogicalName` os `ManifestResourceName` atributos estiverem presentes, seus valores ainda serão usados para o nome do arquivo gerado.

#### <a name="category"></a>Categoria

MSBuild

#### <a name="affected-apis"></a>APIs afetadas

N/D
