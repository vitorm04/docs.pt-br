---
title: "Notificação de alteração na associação de dados do Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, data binding
- Windows Forms, adding change notification for data binding
ms.assetid: b5b10f90-0585-41d9-a377-409835262a92
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ffafaff2355e89e2127742f2fba5c005492b4580
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="change-notification-in-windows-forms-data-binding"></a>Notificação de alteração na associação de dados do Windows Forms
Um dos mais importantes conceitos de associação de dados de formulários do Windows é *de notificação de alteração*. Para garantir que sua fonte de dados e controles associados sempre tenham os dados mais recentes, você deve adicionar notificação de alteração para associação de dados. Especificamente, para garantir que os controles associados são notificados das alterações que foram feitas para sua fonte de dados, e a fonte de dados é notificada sobre as alterações feitas às propriedades de um controle associadas.  
  
 Há tipos diferentes de notificação de alteração, dependendo do tipo de associação de dados:  
  
-   Associação Simple, em que uma propriedade de controle único está associada a uma única instância de um objeto.  
  
-   Associação baseada em lista, que pode incluir uma propriedade de controle único associada à propriedade de um item em uma lista ou uma propriedade de controle associada a uma lista de objetos.  
  
 Além disso, se você estiver criando controles de formulários do Windows que você deseja usar para associação de dados, você deve aplicar o *PropertyName*alterado padrão para os controles, para que as alterações de propriedade associada de um controle são propagadas para o fonte de dados.  
  
## <a name="change-notification-for-simple-binding"></a>Notificação de alteração para associação simples  
 Para associação simple, objetos de negócios devem fornecer notificação de alteração quando altera o valor de uma propriedade associada. Você pode fazer isso ao expor um *PropertyName*evento Changed para cada propriedade do seu objeto de negócios e associando o objeto comercial a controles com o <xref:System.Windows.Forms.BindingSource> ou o método preferido, em que implementa o objeto comercial o <xref:System.ComponentModel.INotifyPropertyChanged> interface e gera um <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> evento quando o valor de uma propriedade é alterado. Para obter mais informações, consulte [como: implementar a INotifyPropertyChanged Interface](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md). Quando você usa os objetos que implementam o <xref:System.ComponentModel.INotifyPropertyChanged> interface, você não precisa usar o <xref:System.Windows.Forms.BindingSource> para vincular o objeto a um controle, mas usando o <xref:System.Windows.Forms.BindingSource> é recomendado.  
  
## <a name="change-notification-for-list-based-binding"></a>Notificação de alteração para associação baseada em lista  
 Windows Forms depende de uma lista associada para fornecer a alteração de propriedade (um valor de propriedade de item de lista altera) e alterado (um item é excluído ou adicionado à lista) informações para controles associados. Portanto, as listas usadas para associação de dados devem implementar o <xref:System.ComponentModel.IBindingList>, que fornece os dois tipos de notificação de alteração. O <xref:System.ComponentModel.BindingList%601> é uma implementação de <xref:System.ComponentModel.IBindingList> e foi projetado para uso com associação de dados de formulários do Windows. Você pode criar um <xref:System.ComponentModel.BindingList%601> que contém um tipo de objeto de negócios que implementa <xref:System.ComponentModel.INotifyPropertyChanged> e a lista irá converter automaticamente o <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> eventos <xref:System.ComponentModel.IBindingList.ListChanged> eventos. Se a lista associada não é um <xref:System.ComponentModel.IBindingList>, você deve associar a lista de objetos para controles de Windows Forms usando o <xref:System.Windows.Forms.BindingSource> componente. O <xref:System.Windows.Forms.BindingSource> componente fornecerá a lista de propriedades de conversão semelhante do <xref:System.ComponentModel.BindingList%601>. Para obter mais informações, consulte [como: acionar notificações de alteração usando um BindingSource e a INotifyPropertyChanged Interface](../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md).  
  
## <a name="change-notification-for-custom-controls"></a>Notificação de alteração para controles personalizados  
 Por fim, do lado do controle você deve expor um *PropertyName*evento Changed para cada propriedade projetado para ser associado a dados. As alterações para a propriedade de controle, em seguida, são propagadas para a fonte de dados associada. Para obter mais informações, consulte [como: aplicar o padrão PropertyNameChanged](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.ComponentModel.INotifyPropertyChanged>  
 <xref:System.ComponentModel.BindingList%601>  
 [Vinculação de dados dos Windows Forms](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Fontes de dados com suporte nos Windows Forms](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)  
 [Vinculação de dados e os Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
