---
title: Associar controle a um tipo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 94faeebb-d2bc-45d6-86d7-96a42661b43d
ms.openlocfilehash: 0bc1f92ee8922990bd0e461655168f5618ba39a6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744991"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type"></a>Como associar um controle dos Windows Forms a um tipo
Quando estiver criando controles que interagem com os dados, às vezes, achará necessário associar um controle a um tipo, em vez de um objeto. Essa situação ocorre especialmente em tempo de design, quando os dados podem não estar disponíveis, mas seus controles ligados a dados ainda precisam exibir informações da interface pública de um tipo. Por exemplo, você pode associar um controle de <xref:System.Windows.Forms.DataGridView> a um objeto exposto por um serviço Web e deseja que o controle de <xref:System.Windows.Forms.DataGridView> etiquete suas colunas em tempo de design com os nomes de membro de um tipo personalizado.  
  
 Você pode associar facilmente um controle a um tipo com o componente <xref:System.Windows.Forms.BindingSource>.  
  
## <a name="example"></a>{1&gt;Exemplo&lt;1}  
 O exemplo de código a seguir demonstra como associar um controle de <xref:System.Windows.Forms.DataGridView> a um tipo personalizado usando um componente <xref:System.Windows.Forms.BindingSource>. Ao executar o exemplo, você observará que o <xref:System.Windows.Forms.DataGridView> tem colunas rotuladas que refletem as propriedades de um objeto `Customer`, antes que o controle seja preenchido com dados. O exemplo tem um botão Adicionar cliente para adicionar dados ao controle de <xref:System.Windows.Forms.DataGridView>. Quando você clica no botão, um novo objeto `Customer` é adicionado à <xref:System.Windows.Forms.BindingSource>. Em um cenário do mundo real, os dados podem ser obtidos por uma chamada para um serviço Web ou outra fonte de dados.  
  
 [!code-csharp[System.Windows.Forms.DataConnector.BindingToType#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindingToType#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 Este exemplo requer:  
  
- Referências aos assemblies Sistema e System.Windows.Forms.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Componente BindingSource](bindingsource-component.md)
