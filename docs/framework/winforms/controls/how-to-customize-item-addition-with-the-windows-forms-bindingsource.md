---
title: Como personalizar a adição de item com o BindingSource dos Windows Forms
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
- cpp
helpviewer_keywords:
- controls [Windows Forms], creating new items
- BindingSource component [Windows Forms], customizing item addition with
- examples [Windows Forms], BindingSource component
- BindingSource component [Windows Forms], examples
ms.assetid: 1aae11fc-6fb2-4cb9-b3d0-e0638fe77ef0
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 39ee45e7bfc0d9ca7fbdadb44514feb67b767dce
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-customize-item-addition-with-the-windows-forms-bindingsource"></a>Como personalizar a adição de item com o BindingSource dos Windows Forms
Quando você usa um <xref:System.Windows.Forms.BindingSource> componente para associar um controle de formulários do Windows a uma fonte de dados, talvez seja necessário personalizar a criação de novos itens. O <xref:System.Windows.Forms.BindingSource> componente facilita isso fornecendo o <xref:System.Windows.Forms.BindingSource.AddingNew> evento, que normalmente é gerado quando o controle associado precisa criar um novo item. O manipulador de eventos pode fornecer qualquer comportamento personalizado necessário (por exemplo, chamar um método em um serviço Web ou obter um novo objeto de uma fábrica de classes).  
  
> [!NOTE]
>  Quando um item é adicionado ao manipular o <xref:System.Windows.Forms.BindingSource.AddingNew> evento, a adição não pode ser cancelada.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como vincular um <xref:System.Windows.Forms.DataGridView> controle a uma fábrica de classe usando um <xref:System.Windows.Forms.BindingSource> componente. Quando o usuário clica o <xref:System.Windows.Forms.DataGridView> linha nova do controle de <xref:System.Windows.Forms.BindingSource.AddingNew> é gerado. O manipulador de eventos cria um novo `DemoCustomer` objeto, que é atribuído para o <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> propriedade. Isso faz com que o novo `DemoCustomer` o objeto a ser adicionado para o <xref:System.Windows.Forms.BindingSource> lista do componente e a serem exibidos na nova linha do <xref:System.Windows.Forms.DataGridView> controle.  
  
 [!code-cpp[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.  
  
 Para obter informações sobre como criar este exemplo da linha de comando para o visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Também é possível compilar este exemplo em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] colando o código em um novo projeto.  Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [Componente BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Como associar um controle do Windows Forms a um tipo](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
