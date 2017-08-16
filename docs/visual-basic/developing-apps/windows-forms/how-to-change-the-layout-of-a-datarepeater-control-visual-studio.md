---
title: 'Como: alterar o Layout de um controle DataRepeater (Visual Studio) | Documentos do Microsoft'
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- DataRepeater, changing layout style
- DataRepeater, changing orientation
ms.assetid: 33aa8fd5-ac63-4bd0-ba13-8c2ab17e7824
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 2adcb80eec08e25553f25dfcb7d2642022c25020
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-change-the-layout-of-a-datarepeater-control-visual-studio"></a>Como alterar o layout de um controle DataRepeater (Visual Studio)
O <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle pode ser exibido em um horizontal (itens de rolagem horizontal) ou vertical (itens de rolagem vertical) orientação.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Você pode alterar a orientação em tempo de design ou em tempo de execução alterando o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>propriedade.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> Se você alterar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>propriedade em tempo de execução, você talvez queira redimensionar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>e reposicionar os controles filho.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>  
  
> [!NOTE]
>  Se você reposicionar controles no <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>em tempo de execução, você precisará chamar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A>e <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A>métodos no início e no final do bloco de código que reposiciona os controles.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>  
  
### <a name="to-change-the-layout-at-design-time"></a>Para alterar o layout em tempo de design  
  
1.  No Windows Forms Designer, selecione o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
    > [!NOTE]
    >  Você deve selecionar a borda externa do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle clicando na área inferior do controle, não na parte superior <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>região.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
2.  Na janela Propriedades, defina a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>propriedade para um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles>ou <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles>.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>  
  
### <a name="to-change-the-layout-at-run-time"></a>Para alterar o layout em tempo de execução  
  
1.  Adicione o seguinte código para um botão ou menu `Click` manipulador de eventos:  
  
     [!code-cs[&#1; VbPowerPacksDataRepeaterLayout](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterLayout n º&1;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.vb)]  
  
2.  Na maioria dos casos, você desejará adicionar código semelhante ao mostrado na seção de exemplo para redimensionar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>e reordenar os controles para se ajustar à nova orientação.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como responder a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyleChanged>evento em um manipulador de eventos.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyleChanged> Este exemplo requer que você tenha um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle chamado `DataRepeater1` em um formulário e que sua <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>contêm dois <xref:System.Windows.Forms.TextBox>controles denominados `TextBox1` e `TextBox2`.</xref:System.Windows.Forms.TextBox> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
 [!code-cs[N º&2; VbPowerPacksDataRepeaterLayout](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.cs) ] 
 [!code-vb [VbPowerPacksDataRepeaterLayout n º&2;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>   
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A>   
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A>   
 [Introdução ao controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [Solucionando problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)   
 [Como alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
