---
title: Visão geral da propriedade AutoSize
ms.date: 03/30/2017
helpviewer_keywords:
- sizing [Windows Forms], automatic
- layout [Windows Forms], AutoSize
- automatic sizing
- AutoSizeMode property
ms.assetid: 62fd82a2-9565-4f65-925b-9d1e66dc4e7d
ms.openlocfilehash: d7502d11c6cad526c5b19ea2d98e39756d518b98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="autosize-property-overview"></a>Visão geral da propriedade AutoSize
O <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade permite que um controle alterar seu tamanho, se necessário, para obter o valor especificado pelo <xref:System.Windows.Forms.Control.PreferredSize%2A> propriedade. Você ajusta o comportamento de dimensionamento para controles específicos configurando a propriedade `AutoSizeMode`.  
  
## <a name="autosize-behavior"></a>Comportamento de AutoSize  
 Suportam a apenas alguns controles de <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade. Além disso, alguns controles que oferecem suporte a <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade também dão suporte a `AutoSizeMode` propriedade.  
  
 O <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade produz um comportamento um pouco diferente, dependendo do tipo de controle específico e o valor da `AutoSizeMode` propriedade, se a propriedade existe. A tabela a seguir descreve os comportamentos que sempre são verdadeiros e fornece uma breve descrição de cada um:  
  
|Comportamento sempre verdadeiro|Descrição|  
|--------------------------|-----------------|  
|O dimensionamento automático é um recurso de tempo de execução.|Isso significa que ele nunca aumenta ou diminui um controle e, em seguida, não tem mais efeito.|  
|Se um controle de alterações de tamanho, o valor de seu <xref:System.Windows.Forms.Control.Location%2A> propriedade sempre permanece constante.|Quando o conteúdo de um controle faz com que ele cresça, o controle aumenta para a direita e para baixo. Controles não crescem para a esquerda.|  
|O <xref:System.Windows.Forms.Control.Dock%2A> e <xref:System.Windows.Forms.Control.Anchor%2A> propriedades são consideradas quando <xref:System.Windows.Forms.Control.AutoSize%2A> é `true`.|O valor do controle do <xref:System.Windows.Forms.Control.Location%2A> propriedade é ajustada para o valor correto.<br /><br /> **Observação** o <xref:System.Windows.Forms.Label> controle é a exceção a essa regra. Quando você define o valor de um encaixada <xref:System.Windows.Forms.Label> do controle <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade `true`, o <xref:System.Windows.Forms.Label> controle não será ampliado.|  
|Um controle <xref:System.Windows.Forms.Control.MaximumSize%2A> e <xref:System.Windows.Forms.Control.MinimumSize%2A> propriedades sempre são cumpridas, independentemente do valor de seu <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade.|O <xref:System.Windows.Forms.Control.MaximumSize%2A> e <xref:System.Windows.Forms.Control.MinimumSize%2A> propriedades não são afetadas pelo <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade.|  
|Não há um tamanho mínimo definido por padrão.|Isso significa que, se um controle é definido para redução em <xref:System.Windows.Forms.Control.AutoSize%2A> e não tiver conteúdo, o valor de seu <xref:System.Windows.Forms.Control.Size%2A> propriedade é 0,0. Nesse caso, o controle será reduzido a um ponto e não ficará visível imediatamente.|  
|Se um controle não implementa o <xref:System.Windows.Forms.Control.GetPreferredSize%2A> método, o <xref:System.Windows.Forms.Control.GetPreferredSize%2A> método retorna o último valor atribuído para o <xref:System.Windows.Forms.Control.Size%2A> propriedade.|Isso significa que essa configuração <xref:System.Windows.Forms.Control.AutoSize%2A> para `true` não terá efeito.|  
|Um controle em um <xref:System.Windows.Forms.TableLayoutPanel> célula sempre é reduzido para caber na célula até que seu <xref:System.Windows.Forms.Control.MinimumSize%2A> for atingido.|Esse tamanho é imposto como um tamanho máximo. Isso não é o caso quando a célula é parte de um <xref:System.Windows.Forms.SizeType.AutoSize> linha ou coluna.|  
  
## <a name="autosizemode-property"></a>Propriedade AutoSizeMode  
 O `AutoSizeMode` propriedade fornece controle mais refinado sobre o padrão <xref:System.Windows.Forms.Control.AutoSize%2A> comportamento. A propriedade `AutoSizeMode` especifica como um controle dimensiona a si mesmo de acordo com seu conteúdo. O conteúdo, por exemplo, poderia ser o texto de um <xref:System.Windows.Forms.Button> de controles filho para um contêiner.  
  
 A tabela a seguir mostra o <xref:System.Windows.Forms.AutoSizeMode> configurações e uma descrição do comportamento elicits cada configuração.  
  
|Configuração de AutoSizeMode|Comportamento|  
|--------------------------|--------------|  
|GrowAndShrink|O controle aumenta ou diminui para conter o conteúdo.<br /><br /> O <xref:System.Windows.Forms.Control.MinimumSize%2A> e <xref:System.Windows.Forms.Control.MaximumSize%2A> valores são cumpridos, mas o valor atual do <xref:System.Windows.Forms.Control.Size%2A> propriedade será ignorada.<br /><br /> Este é o mesmo comportamento de controles com o <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade e não `AutoSizeMode` propriedade.|  
|GrowOnly|O controle aumenta conforme o necessário para abranger o seu conteúdo, mas não irá reduzir seja menor do que o valor especificado pelo seu <xref:System.Windows.Forms.Control.Size%2A> propriedade.<br /><br /> Esse é o valor padrão de `AutoSizeMode`.|  
  
## <a name="controls-that-support-the-autosize-property"></a>Controles que dão suporte à propriedade AutoSize  
 A tabela a seguir lista os controles que oferecem suporte a <xref:System.Windows.Forms.Control.AutoSize%2A> e `AutoSizeMode` propriedades.  
  
|Suporte para AutoSize|Tipo de controle|  
|----------------------|------------------|  
|Suporte para a propriedade -   <xref:System.Windows.Forms.Control.AutoSize%2A>.<br />- Não tem a propriedade `AutoSizeMode`.|<xref:System.Windows.Forms.CheckBox><br /><br /> <xref:System.Windows.Forms.DomainUpDown><br /><br /> <xref:System.Windows.Forms.Label><br /><br /> <xref:System.Windows.Forms.LinkLabel><br /><br /> <xref:System.Windows.Forms.MaskedTextBox> (<xref:System.Windows.Forms.TextBox> base)<br /><br /> <xref:System.Windows.Forms.NumericUpDown><br /><br /> <xref:System.Windows.Forms.RadioButton><br /><br /> <xref:System.Windows.Forms.TextBox><br /><br /> <xref:System.Windows.Forms.TrackBar>|  
|Suporte para a propriedade -   <xref:System.Windows.Forms.Control.AutoSize%2A>.<br />Suporte para a propriedade -   `AutoSizeMode`.|<xref:System.Windows.Forms.Button><br /><br /> <xref:System.Windows.Forms.CheckedListBox><br /><br /> <xref:System.Windows.Forms.FlowLayoutPanel><br /><br /> <xref:System.Windows.Forms.Form><br /><br /> <xref:System.Windows.Forms.GroupBox><br /><br /> <xref:System.Windows.Forms.Panel><br /><br /> <xref:System.Windows.Forms.TableLayoutPanel>|  
|- Não tem a propriedade <xref:System.Windows.Forms.Control.AutoSize%2A>.|<xref:System.Windows.Forms.CheckedListBox><br /><br /> <xref:System.Windows.Forms.ComboBox><br /><br /> <xref:System.Windows.Forms.DataGridView><br /><br /> <xref:System.Windows.Forms.DateTimePicker><br /><br /> <xref:System.Windows.Forms.ListBox><br /><br /> <xref:System.Windows.Forms.ListView><br /><br /> <xref:System.Windows.Forms.MaskedTextBox><br /><br /> <xref:System.Windows.Forms.MonthCalendar><br /><br /> <xref:System.Windows.Forms.ProgressBar><br /><br /> <xref:System.Windows.Forms.PropertyGrid><br /><br /> <xref:System.Windows.Forms.RichTextBox><br /><br /> <xref:System.Windows.Forms.SplitContainer><br /><br /> <xref:System.Windows.Forms.TabControl><br /><br /> <xref:System.Windows.Forms.TabPage><br /><br /> <xref:System.Windows.Forms.TreeView><br /><br /> <xref:System.Windows.Forms.WebBrowser><br /><br /> <xref:System.Windows.Forms.ScrollBar>|  
  
## <a name="autosize-in-the-design-environment"></a>AutoSize no ambiente de design  
 A tabela a seguir descreve o comportamento de dimensionamento de um controle em tempo de design, com base no valor de seu <xref:System.Windows.Forms.Control.AutoSize%2A> e `AutoSizeMode` propriedades.  
  
 Substituir o <xref:System.Windows.Forms.Design.ControlDesigner.SelectionRules%2A> propriedade para determinar se um determinado controle está em um estado de usuário redimensionável. Na tabela a seguir, "não é possível" significa <xref:System.Windows.Forms.Design.SelectionRules.Moveable> somente, "pode" significa <xref:System.Windows.Forms.Design.SelectionRules.AllSizeable> e <xref:System.Windows.Forms.Design.SelectionRules.Moveable>.  
  
|Configurações de AutoSize|Gesto de dimensionamento em tempo de design|  
|-----------------------|---------------------------------|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `true`<br />- Não tem a propriedade `AutoSizeMode`.|O usuário não pode redimensionar o controle em tempo de design, exceto para os seguintes controles:<br /><br /> -   <xref:System.Windows.Forms.TextBox><br />-   <xref:System.Windows.Forms.MaskedTextBox><br />-   <xref:System.Windows.Forms.RichTextBox><br />-   <xref:System.Windows.Forms.TrackBar>|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `true`<br />-   `AutoSizeMode` = <xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>|O usuário não pode redimensionar o controle em tempo de design.|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `true`<br />-   `AutoSizeMode` = <xref:System.Windows.Forms.AutoSizeMode.GrowOnly>|O usuário pode redimensionar o controle em tempo de design. Quando o <xref:System.Windows.Forms.Control.Size%2A> estiver definida, o usuário só pode aumentar o tamanho do controle.|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `false`, ou <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade está oculto.|O usuário pode redimensionar o controle em tempo de design.|  
  
> [!NOTE]
>  Para maximizar a produtividade, as sombras de Windows Forms Designer o <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade para o <xref:System.Windows.Forms.Form> classe. Em tempo de design, o formulário se comporta como se o <xref:System.Windows.Forms.Control.AutoSize%2A> está definida como `false`, independentemente de sua configuração atual. Em tempo de execução, nenhuma acomodação especial é feita e o <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade é aplicada conforme especificado pela configuração da propriedade.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.Control.AutoSize%2A>  
 <xref:System.Windows.Forms.Control.PreferredSize%2A>  
 <xref:System.Windows.Forms.Control.GetPreferredSize%2A>
