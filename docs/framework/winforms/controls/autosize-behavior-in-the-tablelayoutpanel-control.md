---
title: Comportamento de AutoSize no controle TableLayoutPanel
ms.date: 03/30/2017
helpviewer_keywords:
- AutoSize property [Windows Forms], tableLayoutPanel control
- controls [Windows Forms], sizing
- localizing forms
- layout [Windows Forms], AutoSize
- sizing [Windows Forms], automatic
- TableLayoutPanel control [Windows Forms], AutoSize behavior
- automatic sizing
- AutoSizeMode property
ms.assetid: 9233e0c3-2fa6-405e-8701-959479b1250e
ms.openlocfilehash: 46061108226feb83e821edb21dfce2a57bdd3ac7
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708061"
---
# <a name="autosize-behavior-in-the-tablelayoutpanel-control"></a>Comportamento de AutoSize no controle TableLayoutPanel
## <a name="distinct-autosize-behaviors"></a>Comportamentos distintos de AutoSize  
 O <xref:System.Windows.Forms.TableLayoutPanel> controle dá suporte ao comportamento de dimensionamento automático das seguintes maneiras:  
  
-   Por meio de <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade;  
  
-   Por meio de <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> propriedade no <xref:System.Windows.Forms.TableLayoutPanel> estilos de coluna e linha do controle.  
  
### <a name="the-autosize-property-with-row-and-column-styles"></a>A propriedade AutoSize com estilos de coluna e linha  
 A tabela a seguir descreve a interação entre o <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade e o <xref:System.Windows.Forms.TableLayoutPanel> estilos de coluna e linha do controle.  
  
|Configuração de AutoSize|Interação de estilo|  
|----------------------|-----------------------|  
|`false`|O <xref:System.Windows.Forms.TableLayoutPanel> controle prossegue da esquerda para a direita e aloca espaço para a coluna ou linha ou na seguinte ordem.<br /><br /> 1.  Se o <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> estiver definida como <xref:System.Windows.Forms.SizeType.Absolute>, o número de pixels especificado por <xref:System.Windows.Forms.ColumnStyle.Width%2A> ou <xref:System.Windows.Forms.RowStyle.Height%2A> é alocado.<br />2.  Se o <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> estiver definida como <xref:System.Windows.Forms.SizeType.AutoSize>, o número de pixels retornados pelo controle do filho <xref:System.Windows.Forms.Control.GetPreferredSize%2A> método é alocado.<br />3.  Após o espaço para todos os <xref:System.Windows.Forms.SizeType.Absolute> e <xref:System.Windows.Forms.SizeType.AutoSize> linhas ou colunas é alocado, todas as colunas ou linhas com <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> definido como <xref:System.Windows.Forms.SizeType.Percent> são usadas para alocar proporcionalmente o espaço livre restante|  
|`true`|Semelhante à interação anterior, com a exceção que <xref:System.Windows.Forms.SizeType.Percent> colunas ou linhas adquirem um aspecto de dimensionamento automático.<br /><br /> O <xref:System.Windows.Forms.TableLayoutPanel> controle se expande a coluna ou linha para criar o espaço livre adequado, para que nenhuma coluna ou linha com <xref:System.Windows.Forms.SizeType.Percent> estilo corte seu conteúdo. O <xref:System.Windows.Forms.TableLayoutPanel> controle aloca novo espaço proporcionalmente acordo com ao <xref:System.Windows.Forms.ColumnStyle.Width%2A> ou <xref:System.Windows.Forms.RowStyle.Height%2A> propriedade.|  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.TableLayoutPanel>
- [Visão geral do controle TableLayoutPanel](tablelayoutpanel-control-overview.md)
