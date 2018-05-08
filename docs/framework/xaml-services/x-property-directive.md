---
title: Diretiva x:Property
ms.date: 03/30/2017
ms.assetid: 618555a8-c893-455c-810f-ac54cd24ef10
ms.openlocfilehash: 0d554d8ba4d69b4c2d4cc01f3965ade7e508bb0e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="xproperty-directive"></a>Diretiva x:Property
Declara uma propriedade XAML na marcação.  
  
## <a name="xaml-object-element-usage"></a>Uso de elemento Object do XAML  
  
```  
<object x:Class="className">  
  <x:Members>  
    <x:Property Name="propertyName" Type="propertyType/>  
    additionalProperties  
  </x:Members>  
</object>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`className`|Nome da classe de backup ou classe parcial para a produção de XAML.|  
|`propertyName`|Nome da propriedade que está sendo definida.|  
|`propertyType`|Digite um nome (ou outro formato de cadeia de caracteres, específica da estrutura) que especifica o tipo desta propriedade.|  
  
## <a name="remarks"></a>Comentários  
 Na implementação de serviços XAML do .NET Framework. `x:Property` não tem um tipo direto fazendo, mas há suporte para o <xref:System.Windows.Markup.PropertyDefinition> classe. Em um fluxo do nó XAML, uma `x:Property` elemento é representado como um membro chamado `Property`, do namespace XAML de linguagem XAML. O membro `Property` conter atributos como declarado pela marcação.  
  
 O significado de `Name` e `Type` não são atribuídos no nível de serviços XAML do .NET Framework. Eles são armazenados no fluxo do nó XAML inicial como valores de cadeia de caracteres, deve ser interpretado posteriormente com as regras que podem ser impostas por estruturas específicas. O significado pode alinhar um nome XAML e o tipo XAML que significa ou somente pode ser válido em um sistema de tipo de backup, dependendo da implementação.  
  
 Para dar suporte a um uso prático de `x:Members` como um meio para especificar definições de membro na marcação, os membros devem ser associados uma classe que pode ser modificada. O modelo desejado é que `x:Members` existe como um membro de um tipo que especifica um `x:Class`. No entanto, o mecanismo para a associação de tipos e membros ou para a produção de definições de membro dinâmico não tem suporte no nível de serviços XAML do .NET Framework. Isso é da esquerda para estruturas individuais que têm modelos de aplicativos que dão suporte a definições de membro de XAML. Normalmente, as ações de compilação MSBUILD que a compilação de marcação XAML e um integração-lo com code-behind ou produzir somente de XAML assemblies são necessários para dar suporte a esse recurso.  
  
## <a name="xproperty-for-windows-workflow-foundation"></a>Propriedade x: para Windows Workflow Foundation  
 Para Windows Workflow Foundation, `x:Property` define os membros de uma atividade personalizada composta inteiramente em XAML ou XAML – definido membros dinâmicos para um designer de atividade com code-behind. `x:Class` também deve ser especificado no elemento raiz da produção XAML. Isso não é um requisito no nível de serviços XAML do .NET Framework, mas se torna um requisito quando a produção de XAML é carregada pelas ações de compilação do MSBUILD que dão suporte a atividades personalizadas e XAML do Windows Workflow Foundation em geral. O Windows Workflow Foundation não usa o nome de tipo XAML puro como seu valor desejado para o `x:Property` `Type` de atributo e, em vez disso, usa uma convenção de que não está documentada aqui. Para obter mais informações, consulte [criação dinâmica de atividade](http://msdn.microsoft.com/library/dd807392.aspx).
