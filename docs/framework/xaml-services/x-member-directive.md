---
title: Diretiva x:Member
ms.date: 03/30/2017
ms.assetid: 4d8394ef-644c-4331-b6c5-be855d392980
ms.openlocfilehash: dfc08d79bd8206269807d88d2c659f13be487276
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43416816"
---
# <a name="xmember-directive"></a>Diretiva x:Member
Declara um membro XAML na marcação.  
  
## <a name="xaml-object-element-usage"></a>Uso de elemento Object do XAML  
  
```  
<object x:Class="className">  
  <x:Members>  
    <x:Member Name="propertyName"/>  
    additionalMembers  
  </x:Members>  
</object>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`className`|Nome da classe de suporte ou classe parcial para a produção de XAML.|  
|`memberName`|Nome do membro da propriedade que está sendo definida.|  
  
## <a name="remarks"></a>Comentários  
 Na implementação de serviços de XAML do .NET Framework. `x:Member` não tem um tipo direto de fazer, mas é compatível com o <xref:System.Windows.Markup.MemberDefinition> classe. Em um fluxo de nó XAML, uma `x:Member` elemento é representado como um membro chamado `Member`, do namespace XAML de linguagem XAML. O membro `Member` retém os atributos conforme declarado por marcação.  
  
 O significado dos `Name` e `Type` não são atribuídos no nível de serviços de XAML do .NET Framework. Eles são armazenados no fluxo do nó inicial do XAML como valores de cadeia de caracteres, deve ser interpretado mais tarde com as regras que podem ser impostas por estruturas específicas. O significado pode alinhar para um nome XAML e o tipo XAML que significa que, ou talvez só seja válido em um sistema de tipo de backup, dependendo da implementação.  
  
 Para dar suporte a um uso prático de `x:Members` como um meio para especificar definições de membro na marcação, os membros devem ser associados a uma classe que pode ser modificada. O modelo desejado é que `x:Members` existe como um membro de um tipo que especifica um `x:Class`. No entanto, o mecanismo para a associação de tipos e membros ou para a produção de definições de membro dinâmico não tem suporte no nível de serviços de XAML do .NET Framework. Isso é deixado para estruturas individuais que têm modelos de aplicativos que dão suporte a definições de membro de XAML. Normalmente, ações de build do MSBUILD que o XAML e qualquer um de compilação de marcação integração-lo com code-behind ou produzir puro do XAML assemblies são necessários para dar suporte a esse recurso.  
  
## <a name="xproperty-for-windows-workflow-foundation"></a>Propriedade: x para Windows Workflow Foundation  
 Para o Windows Workflow Foundation, `x:Property` define os membros de uma atividade personalizada composta inteiramente em XAML ou XAML – definido membros dinâmicos para um designer de atividade com code-behind. `x:Class` também deve ser especificado no elemento raiz da produção de XAML. Isso não é um requisito no nível de serviços de XAML do .NET Framework, mas se torna uma necessidade quando a produção de XAML é carregada pelas ações de build do MSBUILD que dão suporte a atividades personalizadas e XAML do Windows Workflow Foundation em geral. Windows Workflow Foundation não usa o nome do tipo XAML puro como seu valor pretendido para o `x:Property` `Type` de atributo e, em vez disso, usa uma convenção de que não está documentada aqui. Para obter mais informações, consulte [criação dinâmica de atividade](https://msdn.microsoft.com/library/dd807392.aspx).
