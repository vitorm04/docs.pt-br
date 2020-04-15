---
title: Como acionar notificações de alteração usando um BindingSource e a interface INotifyPropertyChanged
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- change notifications [Windows Forms], raising
- BindingSource component [Windows Forms], and IPropertyChange
- data sources [Windows Forms], detecting changes
- examples [Windows Forms], BindingSource component
- change notifications
- INotifyPropertyChanged interface [Windows Forms], using with BindingSource
- BindingSource component [Windows Forms], examples
ms.assetid: 7fa2cf51-c09f-4375-adf0-e36c5617f099
ms.openlocfilehash: 07248ec0b8ac4f2356d9c9915b6a904dfad30cb2
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388975"
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a>Como acionar notificações de alteração usando um BindingSource e a interface INotifyPropertyChanged
O <xref:System.Windows.Forms.BindingSource> componente detectará automaticamente alterações em uma fonte de dados <xref:System.ComponentModel.INotifyPropertyChanged> quando o <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> tipo contido na fonte de dados implementar a interface e levantar eventos quando um valor de propriedade é alterado. Isso é útil porque os <xref:System.Windows.Forms.BindingSource> controles vinculados ao testamento serão atualizados automaticamente à medida que os valores de origem de dados mudam.  
  
> [!NOTE]
> Se a sua <xref:System.ComponentModel.INotifyPropertyChanged> fonte de dados for implementada e você estiver realizando operações assíncronas, você não deve fazer alterações na fonte de dados em um segmento de fundo. Em vez disso, você deve ler os dados em um thread em segundo plano e mesclar os dados em uma lista no thread da interface do usuário.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a <xref:System.ComponentModel.INotifyPropertyChanged> seguir demonstra uma implementação simples da interface. Ele também mostra <xref:System.Windows.Forms.BindingSource> como a mudança de origem de <xref:System.Windows.Forms.BindingSource> dados passa automaticamente para <xref:System.ComponentModel.INotifyPropertyChanged> um controle vinculado quando está vinculado a uma lista do tipo.  
  
 Se você usar o atributo `CallerMemberName`, chamadas para o método `NotifyPropertyChanged` não precisarão especificar o nome da propriedade como um argumento de cadeia de caracteres. Para obter mais informações, consulte [Informações do chamador (C#)](../../../csharp/language-reference/attributes/caller-information.md) ou [Informações do Chamador (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md).  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
- Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.  
  
## <a name="see-also"></a>Confira também

- <xref:System.ComponentModel.INotifyPropertyChanged>
- [Componente de origem de vinculação](bindingsource-component.md)
- [Como gerar notificações de alteração usando o método BindingSource ResetItem](how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)
