---
title: Personalizar a adição de itens com o componente BindingSource
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
ms.openlocfilehash: 7d74fe6b4bbb1ddb94b359f5ba3ae32ed398d1dd
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738322"
---
# <a name="how-to-customize-item-addition-with-the-windows-forms-bindingsource"></a>Como personalizar a adição de item com o BindingSource dos Windows Forms
Ao usar um componente de <xref:System.Windows.Forms.BindingSource> para associar um controle de Windows Forms a uma fonte de dados, talvez você ache necessário personalizar a criação de novos itens. O componente <xref:System.Windows.Forms.BindingSource> torna isso simples fornecendo o evento <xref:System.Windows.Forms.BindingSource.AddingNew>, que normalmente é gerado quando o controle ligado precisa criar um novo item. O manipulador de eventos pode fornecer qualquer comportamento personalizado necessário (por exemplo, chamar um método em um serviço Web ou obter um novo objeto de uma fábrica de classes).  
  
> [!NOTE]
> Quando um item é adicionado manipulando o evento <xref:System.Windows.Forms.BindingSource.AddingNew>, a adição não pode ser cancelada.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como associar um controle de <xref:System.Windows.Forms.DataGridView> a uma fábrica de classes usando um componente <xref:System.Windows.Forms.BindingSource>. Quando o usuário clica na nova linha do controle de <xref:System.Windows.Forms.DataGridView>, o evento <xref:System.Windows.Forms.BindingSource.AddingNew> é gerado. O manipulador de eventos cria um novo objeto `DemoCustomer`, que é atribuído à propriedade <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType>. Isso faz com que o novo objeto `DemoCustomer` seja adicionado à lista do componente de <xref:System.Windows.Forms.BindingSource> e seja exibido na nova linha do controle de <xref:System.Windows.Forms.DataGridView>.  
  
 [!code-cpp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 Este exemplo requer:  
  
- Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Componente BindingSource](bindingsource-component.md)
- [Como associar um controle do Windows Forms a um tipo](how-to-bind-a-windows-forms-control-to-a-type.md)
