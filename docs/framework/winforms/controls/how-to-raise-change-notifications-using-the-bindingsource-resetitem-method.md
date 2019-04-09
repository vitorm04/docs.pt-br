---
title: 'Como: Acionar notificações de alteração usando o método BindingSource ResetItem'
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
ms.openlocfilehash: 68073f245e1a2eb18a277d7011ca0183dabb3724
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085058"
---
# <a name="how-to-raise-change-notifications-using-the-bindingsource-resetitem-method"></a>Como: Acionar notificações de alteração usando o método BindingSource ResetItem
Algumas fontes de dados para seus controles não acionam notificações de alteração quando itens são alterados, adicionados ou excluídos. Com o <xref:System.Windows.Forms.BindingSource> componente, você pode associar a essas fontes de dados e gerar uma notificação de alteração do seu código.  
  
## <a name="example"></a>Exemplo  
 Este formulário demonstra o uso de um <xref:System.Windows.Forms.BindingSource> componente para associar uma lista para um <xref:System.Windows.Forms.DataGridView> controle. A lista não gera notificações de alteração, portanto, o <xref:System.Windows.Forms.BindingSource.ResetItem%2A> método no <xref:System.Windows.Forms.BindingSource> é chamado quando um item na lista é alterado. .  
  
 [!code-cpp[System.Windows.Forms.DataConnector.ResetItem#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.ResetItem#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.ResetItem#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.  
  
 Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Componente BindingSource](bindingsource-component.md)
- [Como: Associar um controle do Windows Forms a um tipo](how-to-bind-a-windows-forms-control-to-a-type.md)
