---
title: Como personalizar a adição de item com o BindingSource dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], creating new items
- BindingSource component [Windows Forms], customizing item addition with
- examples [Windows Forms], BindingSource component
- BindingSource component [Windows Forms], examples
ms.assetid: 1aae11fc-6fb2-4cb9-b3d0-e0638fe77ef0
ms.openlocfilehash: f8956ceb8da2aa14aea8b7e62b9d60ab656a3891
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43529422"
---
# <a name="how-to-customize-item-addition-with-the-windows-forms-bindingsource"></a>Como personalizar a adição de item com o BindingSource dos Windows Forms
Quando você usa um <xref:System.Windows.Forms.BindingSource> componente para associar um controle dos Windows Forms a uma fonte de dados, talvez seja necessário personalizar a criação de novos itens. O <xref:System.Windows.Forms.BindingSource> componente simplifica isso oferecendo o <xref:System.Windows.Forms.BindingSource.AddingNew> evento, que geralmente ocorre quando o controle associado precisar criar um novo item. O manipulador de eventos pode fornecer qualquer comportamento personalizado necessário (por exemplo, chamar um método em um serviço Web ou obter um novo objeto de uma fábrica de classes).  
  
> [!NOTE]
>  Quando um item é adicionado ao manipular o <xref:System.Windows.Forms.BindingSource.AddingNew> evento, a adição não pode ser cancelada.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como associar um <xref:System.Windows.Forms.DataGridView> controle para uma fábrica de classes usando um <xref:System.Windows.Forms.BindingSource> componente. Quando o usuário clica o <xref:System.Windows.Forms.DataGridView> nova linha do controle, o <xref:System.Windows.Forms.BindingSource.AddingNew> é gerado. O manipulador de eventos cria um novo `DemoCustomer` objeto, que é atribuído para o <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> propriedade. Isso faz com que o novo `DemoCustomer` objeto a ser adicionado para o <xref:System.Windows.Forms.BindingSource> lista do componente e a serem exibidos na nova linha do <xref:System.Windows.Forms.DataGridView> controle.  
  
 [!code-cpp[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.  
  
 Para obter informações sobre como compilar este exemplo de linha de comando do visual Basic ou Visual c#, consulte [compilando da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [Componente BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Como associar um controle do Windows Forms a um tipo](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
