---
title: 'C# atributos reservados: Atributos globais'
ms.date: 04/09/2020
description: Atributos fornecem metadados que o compilador usa para entender mais semântica do seu programa
ms.openlocfilehash: f855f32cd7349da34ffbd20fededdf42c3023938
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389852"
---
# <a name="reserved-attributes-assembly-level-attributes"></a>Atributos reservados: Atributos de nível de montagem

A maioria dos atributos são aplicados aos elementos específicos de linguagem, como classes ou métodos. No entanto, alguns atributos são globais. Eles se aplicam a um assembly inteiro ou módulo. Por exemplo, o atributo <xref:System.Reflection.AssemblyVersionAttribute> pode ser usado para inserir informações de versão em um assembly, desta maneira:

```csharp
[assembly: AssemblyVersion("1.0.0.0")]
```

Atributos globais aparecem no código-fonte após quaisquer diretivas de nível `using` superior e antes de qualquer tipo, módulo ou declarações de namespace. Os atributos globais podem aparecer em vários arquivos de origem, mas os arquivos devem ser compilados em uma única passagem de compilação. O Visual Studio adiciona atributos globais ao arquivo AssemblyInfo.cs em projetos .NET Framework. Esses atributos não são adicionados aos projetos .NET Core.

Os atributos de assembly são valores que fornecem informações sobre um assembly. Eles se enquadram nas seguintes categorias:

- Atributos de identidade do assembly
- Atributos informativos
- Atributos de manifesto do assembly

## <a name="assembly-identity-attributes"></a>Atributos de identidade do assembly

Três atributos (com um nome forte, se aplicável) determinam a identidade de um assembly: nome, versão e cultura. Esses atributos formam o nome completo do assembly e são necessários ao fazer referência a ele no código. Você pode definir a versão e a cultura de um assembly, usando atributos. No entanto, o valor do nome é definido pelo compilador, pelo Visual Studio IDE na [Caixa de Diálogo de Informações de Montagem](/visualstudio/ide/reference/assembly-information-dialog-box)ou pelo Linker de Montagem (Al.exe) quando a montagem é criada. O nome da assembléia é baseado no manifesto da assembléia. O atributo <xref:System.Reflection.AssemblyFlagsAttribute> especifica se várias cópias do assembly podem coexistir.

A tabela a seguir mostra os atributos de identidade.

|Atributo|Finalidade|
|---------------|-------------|
|<xref:System.Reflection.AssemblyVersionAttribute>|Especifica a versão de um assembly.|
|<xref:System.Reflection.AssemblyCultureAttribute>|Especifica a qual cultura o assembly dá suporte.|
|<xref:System.Reflection.AssemblyFlagsAttribute>|Especifica se um assembly dá suporte à execução lado a lado no mesmo computador, no mesmo processo ou no mesmo domínio do aplicativo.|

## <a name="informational-attributes"></a>Atributos informativos

Você usa atributos informativos para fornecer informações adicionais da empresa ou do produto para uma montagem. A tabela a seguir mostra os atributos informativos definidos no namespace <xref:System.Reflection?displayProperty=nameWithType>.

|Atributo|Finalidade|
|---------------|-------------|
|<xref:System.Reflection.AssemblyProductAttribute>|Especifica um nome de produto para um manifesto de montagem.|
|<xref:System.Reflection.AssemblyTrademarkAttribute>|Especifica uma marca registrada para um manifesto de montagem.|
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|Especifica uma versão informacional para um manifesto de montagem.|
|<xref:System.Reflection.AssemblyCompanyAttribute>|Especifica um nome da empresa para um manifesto de montagem.|
|<xref:System.Reflection.AssemblyCopyrightAttribute>|Define um atributo personalizado que especifica os direitos autorais para um manifesto do assembly.|
|<xref:System.Reflection.AssemblyFileVersionAttribute>|Define um número de versão específico para o recurso de versão do arquivo Win32.|
|<xref:System.CLSCompliantAttribute>|Indica se o assembly está em conformidade com a CLS (Common Language Specification).|

## <a name="assembly-manifest-attributes"></a>Atributos de manifesto do assembly

Você pode usar atributos de manifesto do assembly para fornecer informações no manifesto do assembly. Os atributos incluem título, descrição, alias padrão e configuração. A tabela a seguir mostra os atributos de manifesto do assembly definidos no namespace <xref:System.Reflection?displayProperty=nameWithType>.

|Atributo|Finalidade|
|---------------|-------------|
|<xref:System.Reflection.AssemblyTitleAttribute>|Especifica um título de montagem para um manifesto de montagem.|
|<xref:System.Reflection.AssemblyDescriptionAttribute>|Especifica uma descrição da montagem para um manifesto de montagem.|
|<xref:System.Reflection.AssemblyConfigurationAttribute>|Especifica uma configuração de montagem (como varejo ou depuração) para um manifesto de montagem.|
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|Define um alias amigável padrão para um manifesto do assembly|
