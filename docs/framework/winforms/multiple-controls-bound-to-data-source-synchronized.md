---
title: "Como assegurar que vários controles associados à mesma fonte de dados permaneçam sincronizados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], binding multiple
- controls [Windows Forms], synchronizing with data source
ms.assetid: c2f0ecc6-11e6-4c2c-a1ca-0759630c451e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2573f342530e59fa05e7f24342f251990b2ce47d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-ensure-multiple-controls-bound-to-the-same-data-source-remain-synchronized"></a>Como assegurar que vários controles associados à mesma fonte de dados permaneçam sincronizados
Muitas vezes, ao trabalhar com vinculação de dados nos Windows Forms, vários controles são associados à mesma fonte de dados. Em alguns casos, pode ser necessário executar etapas adicionais para garantir que as propriedades associadas dos controles permaneçam sincronizadas entre si e à fonte de dados. Essas etapas são necessárias em duas situações:  
  
-   Se a fonte de dados não implementa <xref:System.ComponentModel.IBindingList>e, portanto, gerar <xref:System.ComponentModel.IBindingList.ListChanged> eventos do tipo <xref:System.ComponentModel.ListChangedType.ItemChanged>.  
  
-   Se a fonte de dados implementa <xref:System.ComponentModel.IEditableObject>.  
  
 No primeiro caso, você pode usar um <xref:System.Windows.Forms.BindingSource> para associar a fonte de dados para os controles. No último caso, você deve usar um <xref:System.Windows.Forms.BindingSource> e tratar o <xref:System.Windows.Forms.BindingSource.BindingComplete> eventos e chamadas <xref:System.Windows.Forms.BindingManagerBase.EndCurrentEdit%2A> em associado <xref:System.Windows.Forms.BindingManagerBase>.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como associar controles dos três — dois controles de caixa de texto e um <xref:System.Windows.Forms.DataGridView> controle — para a mesma coluna em uma <xref:System.Data.DataSet> usando um <xref:System.Windows.Forms.BindingSource> componente. Este exemplo demonstra como tratar o <xref:System.Windows.Forms.BindingSource.BindingComplete> eventos e certifique-se de que quando o valor de texto de uma caixa de texto é alterado, a caixa de texto adicionais e o <xref:System.Windows.Forms.DataGridView> controle são atualizados com o valor correto.  
  
 O exemplo usa um <xref:System.Windows.Forms.BindingSource> para associar a fonte de dados e os controles. Como alternativa, você pode vincular os controles diretamente à fonte de dados e recuperar o <xref:System.Windows.Forms.BindingManagerBase> para a associação do formulário de <xref:System.Windows.Forms.Control.BindingContext%2A> e, em seguida, manipular o <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> eventos para o <xref:System.Windows.Forms.BindingManagerBase>. Para obter um exemplo de como fazer isso, consulte a página de ajuda o <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> evento <xref:System.Windows.Forms.BindingManagerBase>.  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleControls#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleControls#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
-   Este exemplo de código requer  
  
-   Referências a <xref:System>, <xref:System.Windows.Forms>, e <xref:System.Drawing> assemblies.  
  
-   Um formulário com o <xref:System.Windows.Forms.Form.Load> eventos manipulados e uma chamada para o `InitializeControlsAndDataSource` método no exemplo do formulário de <xref:System.Windows.Forms.Form.Load> manipulador de eventos.  
  
## <a name="see-also"></a>Consulte também  
 [Como compartilhar dados associados entre formulários usando o componente BindingSource](../../../docs/framework/winforms/controls/how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)  
 [Notificação de alteração na vinculação de dados dos Windows Forms](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [Interfaces relacionadas à vinculação de dados](../../../docs/framework/winforms/interfaces-related-to-data-binding.md)  
 [Vinculação de dados dos Windows Forms](../../../docs/framework/winforms/windows-forms-data-binding.md)
