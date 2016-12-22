---
title: "Como exibir cabe&#231;alhos de item em um controle DataRepeater (Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "DataRepeater, cabeçalhos de item"
  - "DataRepeater, indicadores de seleção"
ms.assetid: 37321447-0ffa-43e1-bdc9-0480e392b90f
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como exibir cabe&#231;alhos de item em um controle DataRepeater (Visual Studio)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O cabeçalho de item em um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle fornece um indicador visual quando um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> está selecionada.  Quando o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> propriedade estiver definida como <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles> \(padrão\), o cabeçalho de item é exibido à esquerda de cada item.  Quando o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> propriedade estiver definida como <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles>, o cabeçalho de item é exibido na parte superior de cada item.  
  
 Quando ele é selecionado pela primeira vez, o cabeçalho de item é exibido na cor especificada pelo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> propriedade e um ícone de seta branca é exibida.  
  
> [!NOTE]
>  Se você definir a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> para <xref:System.Drawing.Color.White%2A>, o símbolo de seleção não ficará visível quando o item é selecionado pela primeira vez.  
  
 Quando um campo na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> tem o foco, a cor das alterações de cabeçalho de item para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> as alterações do ícone de seta para preto e de cor de plano de fundo.  Se os dados são alterados, um símbolo de lápis é exibido no cabeçalho de item.  
  
 A largura padrão \(ou altura quando o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> propriedade estiver definida como <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles>\) do item de cabeçalho é de 15 pixels.  Você pode alterar a largura, definindo a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> propriedade.  
  
> [!NOTE]
>  Se a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> propriedade estiver definida como um valor que seja menor do que 11, os símbolos do indicador no cabeçalho de item não serão exibidos.  
  
 Você pode ocultar os cabeçalhos de item definindo a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> propriedade para  **False**.  Quando <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> for definido como  **False**, a única indicação de que um item é selecionado é uma linha pontilhada ao redor do perímetro da <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.  
  
> [!NOTE]
>  Você também pode fornecer seu próprio indicador de seleção, monitorando o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A> propriedade da <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> evento da <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  Para obter mais informações, consulte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>.  
  
### Para alterar a aparência dos cabeçalhos de item  
  
1.  No Windows Forms Designer, selecione a região inferior da <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
    > [!NOTE]
    >  Você deve selecionar a região inferior do controle.  Se você selecionar a seção de modelo de item, um conjunto diferente de propriedades será exibida na janela Propriedades.  
  
2.  Na janela Propriedades, use o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> propriedade para alterar a cor dos cabeçalhos de item.  
  
    > [!NOTE]
    >  Se você definir a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> para <xref:System.Drawing.Color.White%2A>, o símbolo de seleção não ficará visível quando o item é selecionado pela primeira vez.  
  
3.  Use o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> propriedade para alterar a largura \(ou altura\) dos cabeçalhos de item.  
  
    > [!NOTE]
    >  Se a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> propriedade estiver definida como um valor que seja menor do que 11, os símbolos do indicador no cabeçalho de item não serão exibidos.  
  
### Para ocultar os cabeçalhos de item  
  
1.  No Windows Forms Designer, selecione a região inferior da <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
    > [!NOTE]
    >  Você deve selecionar a região inferior do controle.  Se você selecionar a seção de modelo de item, um conjunto diferente de propriedades será exibida na janela Propriedades.  
  
2.  Na janela Properties, defina a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> propriedade para  **False**.  
  
     Quando um item a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> é selecionada, a única indicação será uma linha pontilhada ao redor do perímetro da <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 [Introdução ao controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [Como alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)   
 [Como alterar o layout de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)   
 [Solucionando problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)