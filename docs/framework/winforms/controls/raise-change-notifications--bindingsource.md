---
title: Como acionar notificações de alteração usando um BindingSource e a interface INotifyPropertyChanged
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4ff6cf75a18f9a19cc6649f551d5630d4d69dde8
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a>Como acionar notificações de alteração usando um BindingSource e a interface INotifyPropertyChanged
O <xref:System.Windows.Forms.BindingSource> componente detectará automaticamente as alterações em uma fonte de dados quando o tipo contido de fonte de dados implementa a <xref:System.ComponentModel.INotifyPropertyChanged> interface e gera <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> eventos quando um valor de propriedade é alterado. Isso é útil porque os controles associados para o <xref:System.Windows.Forms.BindingSource> , em seguida, será atualizado automaticamente como a alteração de valores de fonte de dados.  
  
> [!NOTE]
>  Se sua fonte de dados implementa <xref:System.ComponentModel.INotifyPropertyChanged> e você estiver executando operações assíncronas, você não deve fazer alterações à fonte de dados em um thread em segundo plano. Em vez disso, você deve ler os dados em um thread em segundo plano e mesclar os dados em uma lista no thread da interface do usuário.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra uma implementação simples do <xref:System.ComponentModel.INotifyPropertyChanged> interface. Ele também mostra como o <xref:System.Windows.Forms.BindingSource> passa automaticamente uma alteração de fonte de dados para uma associação de controle quando o <xref:System.Windows.Forms.BindingSource> está associado a uma lista da <xref:System.ComponentModel.INotifyPropertyChanged> tipo.  
  
 Se você usar o atributo `CallerMemberName`, chamadas para o método `NotifyPropertyChanged` não precisarão especificar o nome da propriedade como um argumento de cadeia de caracteres. Para obter mais informações, consulte [Informações do chamador](http://msdn.microsoft.com/library/9cb2b8c0-c4f6-44b8-9c90-38948455b373).  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.  
  
 Para obter informações sobre como criar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Também é possível compilar este exemplo em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] colando o código em um novo projeto.  Consulte também [HYPERLINK "http://msdn.microsoft.com/library/Bb129228(v=vs.110)" como: compilar e executar uma completa Windows Forms código de exemplo com o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ComponentModel.INotifyPropertyChanged>  
 [Componente BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Como acionar notificações de alteração usando o método BindingSource ResetItem](../../../../docs/framework/winforms/controls/how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)
