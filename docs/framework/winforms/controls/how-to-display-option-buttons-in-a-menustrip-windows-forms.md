---
title: 'Como: Exibir botões de opção em um MenuStrip (Windows Forms)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip [Windows Forms], displaying option buttons
- displaying option buttons [Windows Forms], MenuStrip [Windows Forms]
- option buttons [Windows Forms], displaying in MenuStrip
ms.assetid: 8b596af2-9ff8-4f7b-93d7-cba830e167f4
ms.openlocfilehash: 94d683369edd6583ad8b01c2ce3f393567a5ed75
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971934"
---
# <a name="how-to-display-option-buttons-in-a-menustrip-windows-forms"></a>Como: Exibir botões de opção em um MenuStrip (Windows Forms)

Botões de opção são semelhantes a caixas de seleção, exceto que os usuários podem selecionar apenas um por vez. Embora, por padrão <xref:System.Windows.Forms.ToolStripMenuItem> , a classe não forneça comportamento de botão de opção, a classe fornece o comportamento de caixa de seleção que você pode personalizar para implementar o comportamento de botão de opção <xref:System.Windows.Forms.MenuStrip> para itens de menu em um controle.

Quando a <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> propriedade de um item de menu `true`é, os usuários podem clicar no item para alternar a exibição de uma marca de seleção. A <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> propriedade indica o estado atual do item. Para implementar o comportamento básico do botão de opção, você deve garantir que, quando um item for selecionado, <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> defina a propriedade do item selecionado anteriormente `false`como.

Os procedimentos a seguir descrevem como implementar isso e funcionalidade adicional em uma classe que herda a <xref:System.Windows.Forms.ToolStripMenuItem> classe. A `ToolStripRadioButtonMenuItem` classe substitui membros <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> como e <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> para fornecer o comportamento de seleção e a aparência dos botões de opção. Além disso, essa classe substitui <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> a propriedade para que as opções em um submenu sejam desabilitadas, a menos que o item pai esteja selecionado.

## <a name="to-implement-option-button-selection-behavior"></a>Implementar o comportamento de seleção do botão de opção

1. Inicialize a <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> propriedade para `true` habilitar a seleção de itens.

     [!code-csharp[ToolStripRadioButtonMenuItem#110](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]

2. Substitua o <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> método para limpar a seleção do item selecionado anteriormente quando um novo item for selecionado.

     [!code-csharp[ToolStripRadioButtonMenuItem#120](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]

3. Substitua o <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> método para garantir que clicar em um item que já tenha sido selecionado não desmarcará a seleção.

     [!code-csharp[ToolStripRadioButtonMenuItem#130](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]

## <a name="to-modify-the-appearance-of-the-option-button-items"></a>Modificar a aparência dos itens do botão de opção

1. Substitua o <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> método para substituir a marca de seleção padrão por um botão de opção usando a <xref:System.Windows.Forms.RadioButtonRenderer> classe.

     [!code-csharp[ToolStripRadioButtonMenuItem#140](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]

2. Substitua os <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>métodos <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> e <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> para acompanhar o estado do mouse e certifique-se de que o método pinta o estado de botão de opção correto.

     [!code-csharp[ToolStripRadioButtonMenuItem#150](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]

## <a name="to-disable-options-on-a-submenu-when-the-parent-item-is-not-selected"></a>Desabilitar as opções em um submenu quando o item pai não está selecionado

1. Substitua a <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> propriedade para que o item seja desabilitado quando ele tiver um item pai com um <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> valor de `true` e um <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> valor de `false`.

     [!code-csharp[ToolStripRadioButtonMenuItem#160](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]

2. Substitua o <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> método para assinar o <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> evento do item pai.

     [!code-csharp[ToolStripRadioButtonMenuItem#170](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]

3. No manipulador do evento pai-item <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> , invalida o item para atualizar a exibição com o novo estado habilitado.

     [!code-csharp[ToolStripRadioButtonMenuItem#180](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]

## <a name="example"></a>Exemplo

O exemplo de código a seguir fornece `ToolStripRadioButtonMenuItem` a classe completa, <xref:System.Windows.Forms.Form> e uma `Program` classe e classe para demonstrar o comportamento de botão de opção.

[!code-csharp[ToolStripRadioButtonMenuItem#000](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#000)]
[!code-vb[ToolStripRadioButtonMenuItem#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#000)]

## <a name="compiling-the-code"></a>Compilando o código

Este exemplo requer:

- Referências aos assemblies System, System.Drawing e System.Windows.Forms.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RadioButtonRenderer>
- [Controle MenuStrip](menustrip-control-windows-forms.md)
- [Como: Implementar um ToolStripRenderer personalizado](how-to-implement-a-custom-toolstriprenderer.md)
