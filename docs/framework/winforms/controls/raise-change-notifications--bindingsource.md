---
title: 'Como: Gerar notificações de alteração usando um BindingSource e a interface INotifyPropertyChanged'
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
ms.openlocfilehash: 7dc640f272226da650a63b1a3434822d21053b48
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968291"
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a>Como: Gerar notificações de alteração usando um BindingSource e a interface INotifyPropertyChanged
O <xref:System.Windows.Forms.BindingSource> componente detectará automaticamente as alterações em uma fonte de dados quando o tipo contido na fonte de dados <xref:System.ComponentModel.INotifyPropertyChanged> implementar a interface <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> e gerar eventos quando um valor de propriedade for alterado. Isso é útil porque os controles vinculados <xref:System.Windows.Forms.BindingSource> ao serão atualizados automaticamente conforme os valores da fonte de dados forem alterados.  
  
> [!NOTE]
> Se a fonte de dados <xref:System.ComponentModel.INotifyPropertyChanged> for implementada e você estiver executando operações assíncronas, você não deverá fazer alterações na fonte de dados em um thread em segundo plano. Em vez disso, você deve ler os dados em um thread em segundo plano e mesclar os dados em uma lista no thread da interface do usuário.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra uma implementação simples <xref:System.ComponentModel.INotifyPropertyChanged> da interface. Ele também mostra como o <xref:System.Windows.Forms.BindingSource> passa automaticamente uma alteração de fonte de dados para um controle ligado <xref:System.Windows.Forms.BindingSource> quando o está associado <xref:System.ComponentModel.INotifyPropertyChanged> a uma lista do tipo.  
  
 Se você usar o atributo `CallerMemberName`, chamadas para o método `NotifyPropertyChanged` não precisarão especificar o nome da propriedade como um argumento de cadeia de caracteres. Para obter mais informações, consulte informações [doC#chamador ()](../../../csharp/programming-guide/concepts/caller-information.md) ou [informações do chamador (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md).  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
- Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ComponentModel.INotifyPropertyChanged>
- [Componente BindingSource](bindingsource-component.md)
- [Como: Gerar notificações de alteração usando o método BindingSource ResetItem](how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)
