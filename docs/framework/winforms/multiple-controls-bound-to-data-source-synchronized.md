---
title: 'Como: assegurar que vários controles associados à mesma fonte de dados permaneçam sincronizados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], binding multiple
- controls [Windows Forms], synchronizing with data source
ms.assetid: c2f0ecc6-11e6-4c2c-a1ca-0759630c451e
ms.openlocfilehash: 8f7e59720420a845fa195b8c0fb078a8699a9bc3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61800757"
---
# <a name="how-to-ensure-multiple-controls-bound-to-the-same-data-source-remain-synchronized"></a>Como: assegurar que vários controles associados à mesma fonte de dados permaneçam sincronizados
Muitas vezes, ao trabalhar com vinculação de dados nos Windows Forms, vários controles são associados à mesma fonte de dados. Em alguns casos, pode ser necessário executar etapas adicionais para garantir que as propriedades associadas dos controles permaneçam sincronizadas entre si e à fonte de dados. Essas etapas são necessárias em duas situações:  
  
- Se a fonte de dados não implementa <xref:System.ComponentModel.IBindingList>e, portanto, gerar <xref:System.ComponentModel.IBindingList.ListChanged> eventos do tipo <xref:System.ComponentModel.ListChangedType.ItemChanged>.  
  
- Se a fonte de dados implementa <xref:System.ComponentModel.IEditableObject>.  
  
 No primeiro caso, você pode usar um <xref:System.Windows.Forms.BindingSource> para associar a fonte de dados aos controles. No último caso, você deve usar um <xref:System.Windows.Forms.BindingSource> e lidar com o <xref:System.Windows.Forms.BindingSource.BindingComplete> eventos e chame <xref:System.Windows.Forms.BindingManagerBase.EndCurrentEdit%2A> em associado <xref:System.Windows.Forms.BindingManagerBase>.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como associar três controles — dois controles de caixa de texto e um <xref:System.Windows.Forms.DataGridView> controle — para a mesma coluna em uma <xref:System.Data.DataSet> usando um <xref:System.Windows.Forms.BindingSource> componente. Este exemplo demonstra como lidar com o <xref:System.Windows.Forms.BindingSource.BindingComplete> evento e certifique-se de que quando o valor de texto de uma caixa de texto é alterado, a caixa de texto adicionais e o <xref:System.Windows.Forms.DataGridView> controle são atualizados com o valor correto.  
  
 O exemplo usa um <xref:System.Windows.Forms.BindingSource> para associar a fonte de dados e os controles. Como alternativa, você pode associar os controles diretamente à fonte de dados e recuperar o <xref:System.Windows.Forms.BindingManagerBase> para a associação a partir do formulário <xref:System.Windows.Forms.Control.BindingContext%2A> e, em seguida, lidar com as <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> evento para o <xref:System.Windows.Forms.BindingManagerBase>. Para obter um exemplo de como fazer isso, consulte a página de ajuda o <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> eventos de <xref:System.Windows.Forms.BindingManagerBase>.  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleControls#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleControls#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
- Este exemplo de código requer  
  
- Referências para o <xref:System>, <xref:System.Windows.Forms>, e <xref:System.Drawing> assemblies.  
  
- Um formulário com o <xref:System.Windows.Forms.Form.Load> evento como manipulado e uma chamada para o `InitializeControlsAndDataSource` método no exemplo a partir do formulário <xref:System.Windows.Forms.Form.Load> manipulador de eventos.  
  
## <a name="see-also"></a>Consulte também

- [Como: Compartilhar dados associados entre formulários usando o componente BindingSource](./controls/how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)
- [Notificação de alteração na vinculação de dados dos Windows Forms](change-notification-in-windows-forms-data-binding.md)
- [Interfaces relacionadas à vinculação de dados](interfaces-related-to-data-binding.md)
- [Associação de dados do Windows Forms](windows-forms-data-binding.md)
