---
title: Como exibir cabeçalhos de item em um controle DataRepeater (Visual Studio)
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, item headers
- DataRepeater, selection indicators
ms.assetid: 37321447-0ffa-43e1-bdc9-0480e392b90f
ms.openlocfilehash: 07f6a7e06c5b1e91597ab6b6d816407a2c172278
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592126"
---
# <a name="how-to-display-item-headers-in-a-datarepeater-control-visual-studio"></a>Como exibir cabeçalhos de item em um controle DataRepeater (Visual Studio)
Cabeçalho do item em uma <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle fornece um indicador visual quando um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> é selecionado. Quando o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> está definida como <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical> (o padrão), o cabeçalho do item é exibido à esquerda de cada item. Quando o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> está definida como <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>, o cabeçalho do item é exibido na parte superior de cada item.  
  
 Quando o primeiro estiver selecionada, o cabeçalho do item é exibido na cor que é especificada pelo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> propriedade e um ícone de seta branca é exibida.  
  
> [!NOTE]
>  Se você definir o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> para <xref:System.Drawing.Color.White%2A>, o símbolo de seleção não fica visível quando o item é selecionado pela primeira vez.  
  
 Quando um campo o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> tem o foco, a cor da cabeçalho de alterações de item para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> as alterações do ícone de seta para preto e de cor do plano de fundo. Se dados forem alterados, um símbolo de lápis é exibido no cabeçalho de item.  
  
 A largura padrão (ou altura quando o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> está definida como <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>) do item de cabeçalho é 15 pixels. Você pode alterar a largura, definindo o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> propriedade.  
  
> [!NOTE]
>  Se o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> propriedade é definida como um valor que é menor que 11, os símbolos de indicador no cabeçalho do item não serão exibidos.  
  
 Você pode ocultar os cabeçalhos de item definindo a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> propriedade **False**. Quando <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> é definido como **False**, a única indicação de que um item é selecionado é uma linha pontilhada ao redor do perímetro da <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.  
  
> [!NOTE]
>  Você também pode fornecer seu próprio indicador de seleção, monitorando o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A> propriedade do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> no <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> eventos do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle. Para obter mais informações, consulte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>.  
  
### <a name="to-change-the-appearance-of-item-headers"></a>Para alterar a aparência de cabeçalhos de item  
  
1.  No Designer de formulários do Windows, selecione a região inferior do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
    > [!NOTE]
    >  Você deve selecionar a região inferior do controle. Se você selecionar a seção do item de modelo, um conjunto diferente de propriedades aparecerão na janela Propriedades.  
  
2.  Na janela Propriedades, use o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> propriedade para alterar a cor dos cabeçalhos de item.  
  
    > [!NOTE]
    >  Se você definir o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> para <xref:System.Drawing.Color.White%2A>, o símbolo de seleção não fica visível quando o item é selecionado pela primeira vez.  
  
3.  Use o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> propriedade para alterar a largura (ou altura) dos cabeçalhos de item.  
  
    > [!NOTE]
    >  Se o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> propriedade é definida como um valor que é menor que 11, os símbolos de indicador no cabeçalho do item não serão exibidos.  
  
### <a name="to-hide-item-headers"></a>Para ocultar cabeçalhos de item  
  
1.  No Designer de formulários do Windows, selecione a região inferior do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
    > [!NOTE]
    >  Você deve selecionar a região inferior do controle. Se você selecionar a seção do item de modelo, um conjunto diferente de propriedades aparecerão na janela Propriedades.  
  
2.  Na janela Propriedades, defina o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> propriedade **False**.  
  
     Quando um item no <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> é selecionada, a única indicação será uma linha pontilhada ao redor do perímetro da <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [Introdução ao Controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Como alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [Como alterar o layout de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)  
 [Solução de problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
