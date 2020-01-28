---
title: Notificação de alteração na associação de dados
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, data binding
- Windows Forms, adding change notification for data binding
ms.assetid: b5b10f90-0585-41d9-a377-409835262a92
ms.openlocfilehash: 2dffea46bf0db54d28ef55e507767d88bd29ebc2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746353"
---
# <a name="change-notification-in-windows-forms-data-binding"></a>Notificação de alteração na associação de dados do Windows Forms
Um dos conceitos mais importantes da Associação de dados de Windows Forms é a *notificação de alteração*. Para garantir que a fonte de dados e os controles vinculados sempre tenham os dados mais recentes, você deve adicionar a notificação de alteração para a vinculação de dados. Especificamente, você deseja garantir que os controles associados sejam notificados sobre as alterações que foram feitas em sua fonte de dados, e a fonte de dados é notificada sobre as alterações feitas nas propriedades associadas de um controle.  
  
 Há diferentes tipos de notificação de alteração, dependendo do tipo de associação de dados:  
  
- Associação simples, na qual uma única propriedade de controle está associada a uma única instância de um objeto.  
  
- Associação baseada em lista, que pode incluir uma única propriedade de controle associada à propriedade de um item em uma lista ou uma propriedade de controle associada a uma lista de objetos.  
  
 Além disso, se você estiver criando Windows Forms controles que deseja usar para vinculação de dados, deverá aplicar o padrão de *PropertyName*alterado aos controles, de modo que as alterações na propriedade bound de um controle sejam propagadas para a fonte de dados.  
  
## <a name="change-notification-for-simple-binding"></a>Notificação de alteração para associação simples  
 Para associação simples, os objetos comerciais devem fornecer notificação de alteração quando o valor de uma propriedade associada for alterado. Você pode fazer isso expondo um evento *PropertyName*alterado para cada propriedade do seu objeto comercial e associando o objeto de negócios a controles com o <xref:System.Windows.Forms.BindingSource> ou o método preferencial no qual seu objeto comercial implementa a interface <xref:System.ComponentModel.INotifyPropertyChanged> e gera um evento <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> quando o valor de uma propriedade é alterado. Para obter mais informações, consulte [como implementar a interface INotifyPropertyChanged](how-to-implement-the-inotifypropertychanged-interface.md). Quando você usa objetos que implementam a interface <xref:System.ComponentModel.INotifyPropertyChanged>, não é necessário usar o <xref:System.Windows.Forms.BindingSource> para associar o objeto a um controle, mas é recomendável usar o <xref:System.Windows.Forms.BindingSource>.  
  
## <a name="change-notification-for-list-based-binding"></a>Notificação de alteração para associação baseada em lista  
 Windows Forms depende de uma lista associada para fornecer alteração de propriedade (alterações de valor de propriedade de item de lista) e lista alterada (um item é excluído ou adicionado à lista) informações aos controles associados. Portanto, as listas usadas para a vinculação de dados devem implementar o <xref:System.ComponentModel.IBindingList>, que fornece os dois tipos de notificação de alteração. O <xref:System.ComponentModel.BindingList%601> é uma implementação genérica de <xref:System.ComponentModel.IBindingList> e é projetado para uso com Windows Forms Associação de dados. Você pode criar um <xref:System.ComponentModel.BindingList%601> que contém um tipo de objeto comercial que implementa <xref:System.ComponentModel.INotifyPropertyChanged> e a lista converterá automaticamente os eventos de <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> em eventos de <xref:System.ComponentModel.IBindingList.ListChanged>. Se a lista associada não for uma <xref:System.ComponentModel.IBindingList>, você deverá associar a lista de objetos a Windows Forms controles usando o componente <xref:System.Windows.Forms.BindingSource>. O componente de <xref:System.Windows.Forms.BindingSource> fornecerá uma conversão de propriedade a lista semelhante à do <xref:System.ComponentModel.BindingList%601>. Para obter mais informações, consulte [como: gerar notificações de alteração usando uma BindingSource e a interface INotifyPropertyChanged](./controls/raise-change-notifications--bindingsource.md).  
  
## <a name="change-notification-for-custom-controls"></a>Alterar notificação para controles personalizados  
 Por fim, no lado do controle, você deve expor um evento *PropertyName*Changed para cada propriedade criada para ser associada aos dados. As alterações na propriedade de controle são propagadas para a fonte de dados ligada. Para obter mais informações, consulte [como aplicar o padrão PropertyNameChanged](how-to-apply-the-propertynamechanged-pattern.md)  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.ComponentModel.INotifyPropertyChanged>
- <xref:System.ComponentModel.BindingList%601>
- [Vinculação de dados dos Windows Forms](windows-forms-data-binding.md)
- [Fontes de dados com suporte no Windows Forms](data-sources-supported-by-windows-forms.md)
- [Vinculação de dados e os Windows Forms](data-binding-and-windows-forms.md)
