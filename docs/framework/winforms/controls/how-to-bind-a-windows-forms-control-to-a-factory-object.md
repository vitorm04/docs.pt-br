---
title: Associar o controle a um objeto de fábrica
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], binding
- factory objects [Windows Forms], binding to
- BindingSource component [Windows Forms], binding to a factory object
- BindingSource component [Windows Forms], examples
ms.assetid: 7d59af89-ff82-41d8-a48a-f1fbae788b0d
ms.openlocfilehash: 2b4d9aca3345a0cb1e7e995f66a8982dee983ca8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745088"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-factory-object"></a>Como associar um controle dos Windows Forms a um objeto de alocador
Quando você estiver criando controles que interagem com os dados, às vezes, será necessário associar um controle a um objeto ou método que gere outros objetos. Esse objeto ou método é chamado de alocador. A fonte de dados pode ser, por exemplo, o valor retornado de uma chamada de método, em vez de um objeto na memória ou um tipo. Você pode associar um controle a esse tipo de fonte de dados desde que a fonte retorne uma coleção.  
  
 Você pode associar facilmente um controle a um objeto de fábrica usando o controle de <xref:System.Windows.Forms.BindingSource>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como associar um controle de <xref:System.Windows.Forms.DataGridView> a um método de fábrica usando um controle de <xref:System.Windows.Forms.BindingSource>. O método de fábrica chama-se `GetOrdersByCustomerId` e retorna todos os pedidos para determinado cliente no banco de dados Northwind.  
  
 [!code-cpp[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 Este exemplo requer:  
  
- Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Componente BindingSource](bindingsource-component.md)
- [Como associar um controle do Windows Forms a um tipo](how-to-bind-a-windows-forms-control-to-a-type.md)
