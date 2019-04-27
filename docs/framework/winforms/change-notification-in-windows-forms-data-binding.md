---
title: Notificação de alteração na associação de dados do Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, data binding
- Windows Forms, adding change notification for data binding
ms.assetid: b5b10f90-0585-41d9-a377-409835262a92
ms.openlocfilehash: 559cdee1cce84df1c4b838e249d11ba235a0c636
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011873"
---
# <a name="change-notification-in-windows-forms-data-binding"></a>Notificação de alteração na associação de dados do Windows Forms
Um dos conceitos mais importantes do Windows Forms de vinculação de dados é *notificação de alteração*. Para garantir que sua fonte de dados e controles de ligação sempre tenham os dados mais recentes, você deve adicionar a notificação de alteração para associação de dados. Especificamente, você deseja garantir que os controles associados são notificados das alterações que foram feitas para sua fonte de dados e a fonte de dados é notificada das alterações que foram feitas para as propriedades associadas de um controle.  
  
 Há diferentes tipos de notificação de alteração, dependendo do tipo de associação de dados:  
  
-   Associação Simple, em que uma propriedade de controle único é associada a uma única instância de um objeto.  
  
-   A associação baseada em lista, que pode incluir uma propriedade de controle único associada à propriedade de um item em uma lista ou uma propriedade do controle associado a uma lista de objetos.  
  
 Além disso, se você estiver criando controles de formulários do Windows que você deseja usar para vinculação de dados, você deve aplicar a *PropertyName*alterado o padrão para os controles, para que as alterações à propriedade de um controle associada são propagadas para o fonte de dados.  
  
## <a name="change-notification-for-simple-binding"></a>Notificação de alteração para a associação simples  
 Para a associação simples, objetos de negócios devem fornecer notificação de alteração quando o valor de uma propriedade associada é alterado. Você pode fazer isso, expondo um *PropertyName*evento Changed para cada propriedade do seu objeto de negócios e associando o objeto comercial a controles com o <xref:System.Windows.Forms.BindingSource> ou o método preferencial no qual o objeto comercial implementa o <xref:System.ComponentModel.INotifyPropertyChanged> interface e gera um <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> evento quando o valor de uma propriedade é alterado. Para obter mais informações, confira [Como: Implementar a Interface INotifyPropertyChanged](how-to-implement-the-inotifypropertychanged-interface.md). Quando você usa os objetos que implementam o <xref:System.ComponentModel.INotifyPropertyChanged> interface, você não precisa usar o <xref:System.Windows.Forms.BindingSource> para vincular o objeto a um controle, mas o uso de <xref:System.Windows.Forms.BindingSource> é recomendado.  
  
## <a name="change-notification-for-list-based-binding"></a>Notificação de alteração para associação baseada em lista  
 Windows Forms depende de uma lista ligada para fornecer a alteração de propriedade (altera um valor de propriedade de item de lista) e lista alterado (um item é excluído ou adicionado à lista) informações para controles associados. Portanto, as listas usadas para associação de dados devem implementar o <xref:System.ComponentModel.IBindingList>, que fornece os dois tipos de notificação de alteração. O <xref:System.ComponentModel.BindingList%601> é uma implementação genérica de <xref:System.ComponentModel.IBindingList> e foi projetado para uso com a vinculação de dados de formulários do Windows. Você pode criar uma <xref:System.ComponentModel.BindingList%601> que contém um tipo de objeto de negócios que implementa <xref:System.ComponentModel.INotifyPropertyChanged> e a lista irá converter automaticamente o <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> eventos a serem <xref:System.ComponentModel.IBindingList.ListChanged> eventos. Se a lista associada não é um <xref:System.ComponentModel.IBindingList>, você deve associar a lista de objetos a controles dos Windows Forms usando o <xref:System.Windows.Forms.BindingSource> componente. O <xref:System.Windows.Forms.BindingSource> componente fornecerá a lista de propriedades de conversão semelhante do <xref:System.ComponentModel.BindingList%601>. Para obter mais informações, confira [Como: Gerar notificações de alteração usando um BindingSource e a Interface INotifyPropertyChanged](./controls/raise-change-notifications--bindingsource.md).  
  
## <a name="change-notification-for-custom-controls"></a>Notificação de alteração para controles personalizados  
 Por fim, do lado do controle você deve expor uma *PropertyName*evento Changed para cada propriedade projetado para ser associado a dados. As alterações à propriedade de controle, em seguida, são propagadas para a fonte de dados associada. Para obter mais informações, confira [Como: Aplicar o padrão PropertyNameChanged](how-to-apply-the-propertynamechanged-pattern.md)  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.ComponentModel.INotifyPropertyChanged>
- <xref:System.ComponentModel.BindingList%601>
- [Associação de dados do Windows Forms](windows-forms-data-binding.md)
- [Fontes de dados com suporte nos Windows Forms](data-sources-supported-by-windows-forms.md)
- [Vinculação de dados e os Windows Forms](data-binding-and-windows-forms.md)
