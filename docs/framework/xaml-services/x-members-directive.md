---
title: Diretiva x:Members
ms.date: 03/30/2017
ms.assetid: 155b393d-3b49-4c5a-8c9e-b3d9893af4e4
ms.openlocfilehash: ca42079c1c40a8fb3b1ddfc8f4a6f742768fa9e1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053765"
---
# <a name="xmembers-directive"></a>Diretiva x:Members
Mantém um conjunto de membros que são definidos na marcação, que se aplicam a x:Class do elemento pai.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xaml  
<object x:Class="className">  
  <x:Members>  
    oneOrMoreMembers  
  </x:Members  
</object>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`className`|Nome da classe de backup ou da classe parcial para a produção XAML. Consulte Observações.|  
|`oneOrMoreMembers`|Um ou mais elementos de objeto que representam definições de membro. Normalmente, são `x:Property` elementos de objeto. Consulte Observações.|  
  
## <a name="remarks"></a>Comentários  
 Na implementação de serviços XAML .NET Framework, não há nenhuma classe de backup ou implementação de membro subjacente `x:Members`para. `x:Members`é um membro XAML especial que pode existir como um membro de qualquer tipo. Em um fluxo de nó XAML `x:Members` , é representado como um membro `Members`chamado, do namespace XAML da linguagem XAML. O membro `Members` contém uma lista genérica somente leitura de `Member` objetos. Na marcação típica, os membros individuais são especificados `x:Property` como elementos de propriedade. `x:Property`é um tipo mais preciso especificamente para propriedades de tipos e é atribuível ao `x:Member`. Para obter mais informações, consulte [diretiva x:Property](x-property-directive.md).  
  
 Para dar suporte a um uso `x:Members` prático de como um meio de especificar definições de membro na marcação, os membros devem ser associados a uma classe que pode ser modificada. O modelo pretendido é `x:Members` que existe como um membro de um tipo que especifica `x:Class`um. No entanto, o mecanismo para associar tipos e membros ou para produzir definições de membros dinâmicos não tem suporte no nível de serviços .NET Framework XAML. Isso é deixado para estruturas individuais que têm modelos de aplicativo que dão suporte a definições de membro do XAML. Normalmente, as ações de compilação do MSBUILD que marcam a marcação XAML e a integram com code-behind ou geram assemblies puros de XAML são necessários para dar suporte a esse recurso.  
  
## <a name="xmembers-for-windows-workflow-foundation"></a>x:Members para Windows Workflow Foundation  
 Por Windows Workflow Foundation, `x:Members` contém os membros de uma atividade personalizada composta inteiramente em XAML ou membros dinâmicos definidos pelo XAML para um designer de atividade com code-behind. `x:Class`também deve ser especificado no elemento raiz da produção XAML. Isso não é um requisito no nível de serviços .NET Framework XAML, mas torna-se um requisito quando a produção XAML é carregada pelas ações de compilação do MSBUILD que dão suporte a atividades personalizadas e Windows Workflow Foundation XAML em geral. `x:Members`deve ser o primeiro elemento filho na marcação do elemento Object que declara o `x:Class`.
