---
title: Como acionar notificações de alteração usando o método BindingSource ResetItem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- change notifications [Windows Forms], raising
- data binding [Windows Forms], change notifications
- BindingSource component [Windows Forms], raising change notifications with
- data sources [Windows Forms], detecting changes
- change notifications
ms.assetid: ab8b4096-37ff-4e30-aabc-de79a2f2e972
ms.openlocfilehash: 5894e7036126cb5271cea65e6025e9880b0cbe3d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534593"
---
# <a name="how-to-raise-change-notifications-using-the-bindingsource-resetitem-method"></a>Como acionar notificações de alteração usando o método BindingSource ResetItem
Algumas fontes de dados para os controles não acionar notificações de alteração quando itens são alterados, adicionados ou excluídos. Com o <xref:System.Windows.Forms.BindingSource> componente, você pode associar a essas fontes de dados e gerar uma notificação de alteração de seu código.  
  
## <a name="example"></a>Exemplo  
 Este formulário demonstra como usar um <xref:System.Windows.Forms.BindingSource> componente para associar uma lista para um <xref:System.Windows.Forms.DataGridView> controle. A lista não gera notificações de alteração, portanto, o <xref:System.Windows.Forms.BindingSource.ResetItem%2A> método no <xref:System.Windows.Forms.BindingSource> é chamado quando um item na lista é alterado. .  
  
 [!code-cpp[System.Windows.Forms.DataConnector.ResetItem#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.ResetItem#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.ResetItem#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.  
  
 Para obter informações sobre como criar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [Componente BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Como associar um controle do Windows Forms a um tipo](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
