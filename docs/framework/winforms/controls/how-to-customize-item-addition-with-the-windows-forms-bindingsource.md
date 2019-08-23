---
title: 'Como: Como personalizar a adição de item com o BindingSource do Windows Forms'
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
ms.openlocfilehash: 59522791408eb9c8cabf97a62be2049aeb17f864
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935358"
---
# <a name="how-to-customize-item-addition-with-the-windows-forms-bindingsource"></a>Como: Como personalizar a adição de item com o BindingSource do Windows Forms
Quando você usa um <xref:System.Windows.Forms.BindingSource> componente para associar um controle de Windows Forms a uma fonte de dados, pode ser necessário personalizar a criação de novos itens. O <xref:System.Windows.Forms.BindingSource> componente torna isso simples fornecendo o <xref:System.Windows.Forms.BindingSource.AddingNew> evento, que normalmente é gerado quando o controle ligado precisa criar um novo item. O manipulador de eventos pode fornecer qualquer comportamento personalizado necessário (por exemplo, chamar um método em um serviço Web ou obter um novo objeto de uma fábrica de classes).  
  
> [!NOTE]
> Quando um item é adicionado manipulando o <xref:System.Windows.Forms.BindingSource.AddingNew> evento, a adição não pode ser cancelada.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como associar um <xref:System.Windows.Forms.DataGridView> controle a uma fábrica de classes usando um <xref:System.Windows.Forms.BindingSource> componente. Quando o usuário clica na <xref:System.Windows.Forms.DataGridView> nova linha do controle, o <xref:System.Windows.Forms.BindingSource.AddingNew> evento é gerado. O manipulador de eventos cria um `DemoCustomer` novo objeto, que é atribuído <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> à propriedade. Isso faz com que `DemoCustomer` o novo objeto seja adicionado <xref:System.Windows.Forms.BindingSource> à lista do componente e seja exibido na nova linha do <xref:System.Windows.Forms.DataGridView> controle.  
  
 [!code-cpp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
- Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Componente BindingSource](bindingsource-component.md)
- [Como: Associar um controle de Windows Forms a um tipo](how-to-bind-a-windows-forms-control-to-a-type.md)
