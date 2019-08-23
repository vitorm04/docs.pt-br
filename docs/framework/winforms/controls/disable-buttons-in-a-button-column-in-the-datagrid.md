---
title: 'Como: Desabilitar botões em uma coluna de botão no controle DataGridView do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], disabling buttons
- buttons [Windows Forms], disabling in button columns
- DataGridView control [Windows Forms], disabling button cells
ms.assetid: 5c344d01-013a-4a6b-8f8d-62ec9321d81e
ms.openlocfilehash: b8bb503186e41c682b0685e4c9c4bf0bb3adcbe8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967391"
---
# <a name="how-to-disable-buttons-in-a-button-column-in-the-windows-forms-datagridview-control"></a>Como: Desabilitar botões em uma coluna de botão no controle DataGridView do Windows Forms
O <xref:System.Windows.Forms.DataGridView> controle inclui a <xref:System.Windows.Forms.DataGridViewButtonCell> classe para exibir células com uma interface do usuário (IU) como um botão. No entanto, <xref:System.Windows.Forms.DataGridViewButtonCell> o não fornece uma maneira de desabilitar a aparência do botão exibido pela célula.  
  
 O exemplo de código a seguir demonstra como personalizar <xref:System.Windows.Forms.DataGridViewButtonCell> a classe para exibir botões que podem aparecer desabilitados. O exemplo define um novo tipo de célula `DataGridViewDisableButtonCell`,, que deriva de <xref:System.Windows.Forms.DataGridViewButtonCell>. Esse tipo de célula fornece uma nova propriedade `Enabled` que pode ser definida como `false` para desenhar um botão desabilitado na célula. O exemplo também define um novo tipo de coluna, `DataGridViewDisableButtonColumn`, que exibe objetos `DataGridViewDisableButtonCell`. Para demonstrar essa nova célula e tipo de coluna, o valor atual de <xref:System.Windows.Forms.DataGridViewCheckBoxCell> cada no pai <xref:System.Windows.Forms.DataGridView> determina `DataGridViewDisableButtonCell` se a `Enabled` Propriedade do na mesma linha é `true` ou `false`.  
  
> [!NOTE]
> Quando você deriva de <xref:System.Windows.Forms.DataGridViewCell> ou <xref:System.Windows.Forms.DataGridViewColumn> e adiciona novas propriedades à classe derivada, certifique-se de substituir o `Clone` método para copiar as novas propriedades durante as operações de clonagem. Você também deve chamar o método `Clone` da classe base para que as propriedades da classe base sejam copiadas para a nova célula ou coluna.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.Windows.Forms.DataGridView.DisabledButtons#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.DisabledButtons#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
- Referências aos assemblies System, System.Drawing, System.Windows.Forms e System.Windows.Forms.VisualStyles.  
  
## <a name="see-also"></a>Consulte também

- [Personalizando o controle DataGridView dos Windows Forms](customizing-the-windows-forms-datagridview-control.md)
- [Arquitetura de controle DataGridView](datagridview-control-architecture-windows-forms.md)
- [Tipos de coluna no controle DataGridView dos Windows Forms](column-types-in-the-windows-forms-datagridview-control.md)
