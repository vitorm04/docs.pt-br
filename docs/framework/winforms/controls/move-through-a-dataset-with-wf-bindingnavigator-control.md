---
title: Percorrer um conjunto de um DataSet com o controle BindingNavigator
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- datasets [Windows Forms], moving through
- BindingNavigator control [Windows Forms], moving through datasets
- examples [Windows Forms], BindingNavigator control
ms.assetid: 146d97be-3d97-400e-accb-860bbf47729d
ms.openlocfilehash: 73a102da74a3a2a00b5042331cffcaf3d858ea5b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742157"
---
# <a name="how-to-move-through-a-dataset-with-the-windows-forms-bindingnavigator-control"></a>Como avançar em um DataSet com o controle BindingNavigator dos Windows Forms
Ao criar aplicativos controlados por dados, muitas vezes você precisará exibir coleções de dados aos usuários. O controle de <xref:System.Windows.Forms.BindingNavigator>, em conjunto com o componente <xref:System.Windows.Forms.BindingSource>, fornece uma solução conveniente e extensível para a movimentação de uma coleção e a exibição de itens em sequência.  
  
## <a name="example"></a>{1&gt;Exemplo&lt;1}  
 O exemplo de código a seguir demonstra como usar um controle de <xref:System.Windows.Forms.BindingNavigator> para percorrer os dados. O conjunto está contido em um <xref:System.Data.DataView>, que está associado a um controle de <xref:System.Windows.Forms.TextBox> com um componente <xref:System.Windows.Forms.BindingSource>.  
  
> [!NOTE]
> O armazenamento das informações confidenciais, como uma senha, dentro da cadeia de conexão pode afetar a segurança do aplicativo. O uso da Autenticação do Windows (também conhecida como segurança integrada) é uma maneira mais segura de controlar o acesso a um banco de dados. Para obter mais informações, consulte [Protegendo informações de conexão](../../data/adonet/protecting-connection-information.md).  
  
 [!code-csharp[System.Windows.Forms.DataNavigator#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataNavigator#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 Este exemplo requer:  
  
- Referência aos conjuntos System, System.Data, System.Drawing, System.Windows.Forms e System.Xml.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Controle BindingNavigator](bindingnavigator-control-windows-forms.md)
- [Componente BindingSource](bindingsource-component.md)
- [Como associar um controle dos Windows Forms a um tipo](how-to-bind-a-windows-forms-control-to-a-type.md)
