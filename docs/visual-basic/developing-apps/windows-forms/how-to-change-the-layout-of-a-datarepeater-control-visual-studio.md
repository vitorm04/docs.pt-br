---
title: "Como alterar o layout de um controle DataRepeater (Visual Studio) | Microsoft Docs"
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
  - "DataRepeater, alterando estilo de layout"
  - "DataRepeater, alterando orientação"
ms.assetid: 33aa8fd5-ac63-4bd0-ba13-8c2ab17e7824
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como alterar o layout de um controle DataRepeater (Visual Studio)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle pode ser exibido em um horizontal \(itens de rolagem horizontal\) ou vertical \(itens de rolagem vertical\) orientação.  Você pode alterar a orientação em tempo de design ou em tempo de execução alterando a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> propriedade.  Se você alterar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> propriedade em tempo de execução, você talvez também queira redimensionar a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> e reposicionar os controles filho.  
  
> [!NOTE]
>  Caso seja reposicionado controles sobre o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> em tempo de execução, você precisará chamar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> e <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> métodos no início e no final do bloco de código que reposiciona os controles.  
  
### Para alterar o layout em tempo de design  
  
1.  No Windows Forms Designer, selecione o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
    > [!NOTE]
    >  Você deve selecionar a borda externa da <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> o controle clicando na região inferior do controle, não na parte superior <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> região.  
  
2.  Na janela Properties, defina a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> propriedade para um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles> ou <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles>.  
  
### Para alterar o layout em tempo de execução  
  
1.  Adicione o seguinte código para um botão ou menu `Click` manipulador de eventos:  
  
     [!code-cs[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.vb)]  
  
2.  Na maioria dos casos, você desejará adicionar código semelhante ao mostrado na seção exemplo para redimensionar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> e reorganizar os controles para se ajustar à nova orientação.  
  
## Exemplo  
 O exemplo a seguir mostra como responder para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyleChanged> evento em um manipulador de eventos.  Este exemplo requer que você tenha um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle denominado `DataRepeater1` em um formulário e que seu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> conter dois <xref:System.Windows.Forms.TextBox> controles denominados `TextBox1` e `TextBox2`.  
  
 [!code-cs[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.cs)]
 [!code-vb[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.vb)]  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>   
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A>   
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A>   
 [Introdução ao controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [Solucionando problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)   
 [Como alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)