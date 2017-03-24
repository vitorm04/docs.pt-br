---
title: "Como: exibir cabeçalhos de Item em um controle DataRepeater (Visual Studio) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- DataRepeater, item headers
- DataRepeater, selection indicators
ms.assetid: 37321447-0ffa-43e1-bdc9-0480e392b90f
caps.latest.revision: 7
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6158f171fd497fa0ab4dd994e2bfe45cc74cc488
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-display-item-headers-in-a-datarepeater-control-visual-studio"></a>Como exibir cabeçalhos de item em um controle DataRepeater (Visual Studio)
Cabeçalho do item em uma <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle fornece um indicador visual quando um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>é selecionado.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Quando o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>estiver definida como <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles>(o padrão), o cabeçalho do item é exibido à esquerda de cada item.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> Quando o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>estiver definida como <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles>, o cabeçalho do item é exibido na parte superior de cada item.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>  
  
 Quando o primeiro é selecionada, o cabeçalho do item é exibido na cor que é especificada pelo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>propriedade e um ícone de seta branca é exibida.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>  
  
> [!NOTE]
>  Se você definir o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>para <xref:System.Drawing.Color.White%2A>, o símbolo de seleção não ficará visível quando o item for selecionado pela primeira vez.</xref:System.Drawing.Color.White%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>  
  
 Quando um campo o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>tem o foco, a cor da cabeçalho de alterações de item para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>plano de fundo de cor e as alterações do ícone de seta para preto.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> Se os dados são alterados, um símbolo de lápis é exibido no cabeçalho de item.  
  
 A largura padrão (ou altura quando o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>estiver definida como <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles>) do item de cabeçalho é 15 pixels.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> Você pode alterar a largura, definindo o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A>propriedade.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A>  
  
> [!NOTE]
>  Se o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A>propriedade é definida como um valor que seja menor do que 11, os símbolos de indicador no cabeçalho do item não serão exibidos.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A>  
  
 Você pode ocultar os cabeçalhos de item, definindo a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A>propriedade **False**.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> Quando <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A>é definido como **False**, a única indicação de que um item é selecionado é uma linha pontilhada em torno do perímetro de <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A>  
  
> [!NOTE]
>  Você também pode fornecer seu próprio indicador de seleção monitorando o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>propriedade do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>no <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>eventos do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A> Para obter mais informações, consulte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>  
  
### <a name="to-change-the-appearance-of-item-headers"></a>Para alterar a aparência de cabeçalhos de item  
  
1.  No Windows Forms Designer, selecione a região inferior do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
    > [!NOTE]
    >  Você deve selecionar a região inferior do controle. Se você selecionar a seção de modelos de item, um conjunto diferente de propriedades será exibida na janela Propriedades.  
  
2.  Na janela Propriedades, use o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>propriedade para alterar a cor dos cabeçalhos de item.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>  
  
    > [!NOTE]
    >  Se você definir o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>para <xref:System.Drawing.Color.White%2A>, o símbolo de seleção não ficará visível quando o item for selecionado pela primeira vez.</xref:System.Drawing.Color.White%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>  
  
3.  Use o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A>propriedade para alterar a largura (ou altura) dos cabeçalhos de item.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A>  
  
    > [!NOTE]
    >  Se o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A>propriedade é definida como um valor que seja menor do que 11, os símbolos de indicador no cabeçalho do item não serão exibidos.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A>  
  
### <a name="to-hide-item-headers"></a>Para ocultar cabeçalhos de item  
  
1.  No Windows Forms Designer, selecione a região inferior do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
    > [!NOTE]
    >  Você deve selecionar a região inferior do controle. Se você selecionar a seção de modelos de item, um conjunto diferente de propriedades será exibida na janela Propriedades.  
  
2.  Na janela Propriedades, defina o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A>propriedade **False**.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A>  
  
     Quando um item de <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>é selecionada, a única indicação será uma linha pontilhada em torno do perímetro de <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 [Introdução ao controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [Como: alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)   
 [Como: alterar o Layout de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)   
 [Solução de problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
