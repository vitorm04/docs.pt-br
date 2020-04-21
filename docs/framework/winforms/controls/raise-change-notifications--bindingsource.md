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
ms.openlocfilehash: 2fe4458aa43144a9c29ed67fd7bee99a37fe1434
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739688"
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a>Como acionar notificações de alteração usando um BindingSource e a interface INotifyPropertyChanged
O <xref:System.Windows.Forms.BindingSource> componente detecta automaticamente alterações em uma fonte de dados <xref:System.ComponentModel.INotifyPropertyChanged> quando <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> o tipo contido na fonte de dados implementa e levanta eventos quando um valor de propriedade é alterado. Essa detecção de alteração é <xref:System.Windows.Forms.BindingSource> útil porque os controles vinculados à atualização automática à medida que os valores de origem de dados mudam.  
  
> [!NOTE]
> Se a sua <xref:System.ComponentModel.INotifyPropertyChanged> fonte de dados for implementada e você estiver realizando operações assíncronas, você não deve fazer alterações na fonte de dados em um segmento de fundo. Em vez disso, você deve ler os dados em um thread em segundo plano e mesclar os dados em uma lista no thread da interface do usuário.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a <xref:System.ComponentModel.INotifyPropertyChanged> seguir demonstra uma implementação simples da interface. Ele também mostra <xref:System.Windows.Forms.BindingSource> como a mudança de origem de <xref:System.Windows.Forms.BindingSource> dados passa automaticamente para <xref:System.ComponentModel.INotifyPropertyChanged> um controle vinculado quando está vinculado a uma lista do tipo.  
  
 Se você usar o atributo `CallerMemberName`, chamadas para o método `NotifyPropertyChanged` não precisarão especificar o nome da propriedade como um argumento de cadeia de caracteres. Para obter mais informações, consulte [Informações do chamador (C#)](../../../csharp/language-reference/attributes/caller-information.md) ou [Informações do Chamador (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md).  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
- Referências aos conjuntos System,Data, System.Drawing e System.Windows.Forms.  
  
## <a name="see-also"></a>Confira também

- <xref:System.ComponentModel.INotifyPropertyChanged>
- [Componente de origem de vinculação](bindingsource-component.md)
- [Como gerar notificações de alteração usando o método BindingSource ResetItem](how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)
