---
title: Desabilitar botões em uma coluna de botão no controle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], disabling buttons
- buttons [Windows Forms], disabling in button columns
- DataGridView control [Windows Forms], disabling button cells
ms.assetid: 5c344d01-013a-4a6b-8f8d-62ec9321d81e
ms.openlocfilehash: 691781a43005d66e13029ab8110eb7f9daacc35f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745955"
---
# <a name="how-to-disable-buttons-in-a-button-column-in-the-windows-forms-datagridview-control"></a>Como desabilitar botões em uma coluna de botão no controle DataGridView dos Windows Forms
O controle <xref:System.Windows.Forms.DataGridView> inclui a classe <xref:System.Windows.Forms.DataGridViewButtonCell> para exibir células com uma interface do usuário (IU) como um botão. No entanto, <xref:System.Windows.Forms.DataGridViewButtonCell> não fornece uma maneira de desabilitar a aparência do botão exibido pela célula.  
  
 O exemplo de código a seguir demonstra como personalizar a classe <xref:System.Windows.Forms.DataGridViewButtonCell> para exibir botões que podem aparecer desabilitados. O exemplo define um novo tipo de célula, `DataGridViewDisableButtonCell`, que deriva de <xref:System.Windows.Forms.DataGridViewButtonCell>. Esse tipo de célula fornece uma nova propriedade `Enabled` que pode ser definida como `false` para desenhar um botão desabilitado na célula. O exemplo também define um novo tipo de coluna, `DataGridViewDisableButtonColumn`, que exibe objetos `DataGridViewDisableButtonCell`. Para demonstrar essa nova célula e tipo de coluna, o valor atual de cada <xref:System.Windows.Forms.DataGridViewCheckBoxCell> no <xref:System.Windows.Forms.DataGridView> pai determina se a propriedade `Enabled` do `DataGridViewDisableButtonCell` na mesma linha é `true` ou `false`.  
  
> [!NOTE]
> Quando você deriva de <xref:System.Windows.Forms.DataGridViewCell> ou <xref:System.Windows.Forms.DataGridViewColumn> e adiciona novas propriedades à classe derivada, certifique-se de substituir o método `Clone` para copiar as novas propriedades durante as operações de clonagem. Você também deve chamar o método `Clone` da classe base para que as propriedades da classe base sejam copiadas para a nova célula ou coluna.  
  
## <a name="example"></a>{1&gt;Exemplo&lt;1}  
 [!code-csharp[System.Windows.Forms.DataGridView.DisabledButtons#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.DisabledButtons#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 Este exemplo requer:  
  
- Referências aos assemblies System, System.Drawing, System.Windows.Forms e System.Windows.Forms.VisualStyles.  
  
## <a name="see-also"></a>Consulte também

- [Personalizando o controle DataGridView do Windows Forms](customizing-the-windows-forms-datagridview-control.md)
- [Arquitetura de controle DataGridView](datagridview-control-architecture-windows-forms.md)
- [Tipos de coluna no controle DataGridView do Windows Forms](column-types-in-the-windows-forms-datagridview-control.md)
