---
title: Atributos em controles dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- attributes [Windows Forms]
- attributes [Windows Forms], data binding properties
- attributes [Windows Forms], control properties
- attributes [Windows Forms], classes
ms.assetid: 2c5640e9-6c6c-49d7-a5e4-a768f6be7853
ms.openlocfilehash: 9dd4c2aabe1517b66d8e499de3cf2671bb94e0d6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61954369"
---
# <a name="attributes-in-windows-forms-controls"></a>Atributos em controles dos Windows Forms
O .NET Framework fornece uma variedade de atributos que podem ser aplicados aos membros de seus controles personalizados e componentes. Alguns desses atributos afetam o comportamento de uma classe no tempo de execução, enquanto outros afetam o comportamento no tempo de design.  
  
## <a name="attributes-for-control-and-component-properties"></a>Atributos de propriedades de controles e componentes  
 A tabela a seguir mostra os atributos que podem ser aplicados a propriedades ou outros membros de seus controles e componentes personalizados. Para obter um exemplo que usa muitos desses atributos, consulte [como: Aplicar atributos em controles dos Windows Forms](how-to-apply-attributes-in-windows-forms-controls.md).  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|<xref:System.ComponentModel.AmbientValueAttribute>|Especifica o valor a ser passado para uma propriedade para fazer com que a propriedade obtenha o seu valor de outra origem. Isso é conhecido como *ambiente*.|  
|<xref:System.ComponentModel.BrowsableAttribute>|Especifica se uma propriedade ou evento deve ser exibido em uma janela **Propriedades**.|  
|<xref:System.ComponentModel.CategoryAttribute>|Especifica o nome da categoria na qual grupo de propriedade ou evento quando exibido em uma <xref:System.Windows.Forms.PropertyGrid> controle definido como <xref:System.Windows.Forms.PropertySort.Categorized> modo.|  
|<xref:System.ComponentModel.DefaultValueAttribute>|Especifica o valor padrão de uma propriedade.|  
|<xref:System.ComponentModel.DescriptionAttribute>|Especifica uma descrição de uma propriedade ou evento.|  
|<xref:System.ComponentModel.DisplayNameAttribute>|Especifica o nome de exibição de uma propriedade, evento ou método `public void` que não usa argumentos.|  
|<xref:System.ComponentModel.EditorAttribute>|Especifica o editor que deve ser usado para alterar uma propriedade.|  
|<xref:System.ComponentModel.EditorBrowsableAttribute>|Especifica que uma propriedade ou método é visível em um editor.|  
|<xref:System.ComponentModel.Design.HelpKeywordAttribute>|Especifica a palavra-chave de contexto de uma classe ou membro.|  
|<xref:System.ComponentModel.LocalizableAttribute>|Especifica se uma propriedade deve ser localizada.|  
|<xref:System.ComponentModel.PasswordPropertyTextAttribute>|Indica que a representação de texto de um objeto é obscurecida por caracteres como asteriscos.|  
|<xref:System.ComponentModel.ReadOnlyAttribute>|Especifica se a propriedade à qual esse atributo está associado é somente leitura ou leitura/gravação no tempo de design.|  
|<xref:System.ComponentModel.RefreshPropertiesAttribute>|Indica que a grade de propriedades deve ser atualizada quando o valor da propriedade associada é alterado.|  
|<xref:System.ComponentModel.TypeConverterAttribute>|Especifica o tipo a ser usado como um conversor para o objeto ao qual este atributo está associado.|  
  
## <a name="attributes-for-data-binding-properties"></a>Atributos para propriedades de vinculação de dados  
 A tabela a seguir mostra os atributos que podem ser aplicados para especificar como os controles e componentes personalizados interagem com vinculação de dados.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|<xref:System.ComponentModel.BindableAttribute>|Especifica se uma propriedade normalmente é usada para associação.|  
|<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|Especifica a fonte de dados e as propriedades de membro de dados para um componente.|  
|<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|Especifica a propriedade de associação padrão de um componente.|  
|<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|Especifica a fonte de dados e as propriedades de membro de dados para um componente.|  
|<xref:System.ComponentModel.AttributeProviderAttribute>|Habilita o redirecionamento de atributo.|  
  
## <a name="attributes-for-classes"></a>Atributos para classes  
 A tabela a seguir mostra os atributos que podem ser aplicados para especificar o comportamento dos seus controles e componentes personalizados no tempo de design.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|<xref:System.ComponentModel.DefaultEventAttribute>|Especifica o evento padrão de um componente.|  
|<xref:System.ComponentModel.DefaultPropertyAttribute>|Especifica a propriedade padrão de um componente.|  
|<xref:System.ComponentModel.DesignerAttribute>|Especifica a classe usada para implementar os serviços de tempo de design para um componente.|  
|<xref:System.ComponentModel.DesignerCategoryAttribute>|Especifica que o designer de uma classe pertence a uma determinada categoria.|  
|<xref:System.ComponentModel.ToolboxItemAttribute>|Representa um atributo de um item de caixa de ferramentas.|  
|<xref:System.ComponentModel.ToolboxItemFilterAttribute>|Especifica a cadeia de caracteres de filtro e o tipo de filtro para um item de Caixa de ferramentas.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Attribute>
- [Como: Aplicar atributos em controles dos Windows Forms](how-to-apply-attributes-in-windows-forms-controls.md)
- [Estendendo o suporte ao tempo de design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))
- [Desenvolvendo controles dos Windows Forms personalizados com o .NET Framework](developing-custom-windows-forms-controls.md)
