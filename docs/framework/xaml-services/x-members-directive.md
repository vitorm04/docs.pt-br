---
title: Diretiva x:Members
ms.date: 03/30/2017
ms.assetid: 155b393d-3b49-4c5a-8c9e-b3d9893af4e4
ms.openlocfilehash: d23e6b459af932e0a6f69309f26a1cce70a9d256
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938886"
---
# <a name="xmembers-directive"></a>Diretiva x:Members
Contém um conjunto de membros que são definidos na marcação, que se aplicam à classe: x do elemento pai.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```  
<object x:Class="className">  
  <x:Members>  
    oneOrMoreMembers  
  </x:Members  
</object>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`className`|Nome da classe de suporte ou classe parcial para a produção de XAML. Consulte Observações.|  
|`oneOrMoreMembers`|Um ou mais elementos de objeto que representa as definições de membro. Normalmente, esses são `x:Property` elementos de objeto. Consulte Observações.|  
  
## <a name="remarks"></a>Comentários  
 Na implementação de serviços de XAML do .NET Framework, há nenhuma classe de suporte ou a implementação subjacente de membro para `x:Members`. `x:Members` é um membro XAML especial que pode existir como um membro em qualquer tipo. Em um fluxo de nó XAML `x:Members` é representado como um membro chamado `Members`, do namespace XAML de linguagem XAML. O membro `Members` contém uma lista somente leitura genérica de `Member` objetos. Na marcação típica, os membros individuais são especificados como `x:Property` elementos de propriedade. `x:Property` é um tipo mais preciso especificamente para propriedades de tipos e pode ser atribuída à `x:Member`. Para obter mais informações, consulte [x: propriedade diretiva](x-property-directive.md).  
  
 Para dar suporte a um uso prático de `x:Members` como um meio para especificar definições de membro na marcação, os membros devem ser associados a uma classe que pode ser modificada. O modelo desejado é que `x:Members` existe como um membro de um tipo que especifica um `x:Class`. No entanto, o mecanismo para a associação de tipos e membros ou para a produção de definições de membro dinâmico não tem suporte no nível de serviços de XAML do .NET Framework. Isso é deixado para estruturas individuais que têm modelos de aplicativos que dão suporte a definições de membro de XAML. Normalmente, ações de build do MSBUILD que o XAML e qualquer um de compilação de marcação integração-lo com code-behind ou produzir puro do XAML assemblies são necessários para dar suporte a esse recurso.  
  
## <a name="xmembers-for-windows-workflow-foundation"></a>x: membros para o Windows Workflow Foundation  
 Para o Windows Workflow Foundation, `x:Members` contém os membros de uma atividade personalizada composta inteiramente em XAML ou XAML – definido membros dinâmicos para um designer de atividade com code-behind. `x:Class` também deve ser especificado no elemento raiz da produção de XAML. Isso não é um requisito no nível de serviços de XAML do .NET Framework, mas se torna uma necessidade quando a produção de XAML é carregada pelas ações de build do MSBUILD que dão suporte a atividades personalizadas e XAML do Windows Workflow Foundation em geral. `x:Members` deve ser o primeiro elemento filho na marcação do elemento de objeto que declara o `x:Class`.
