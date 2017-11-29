---
title: Como alterar o layout de um controle DataRepeater (Visual Studio)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, changing layout style
- DataRepeater, changing orientation
ms.assetid: 33aa8fd5-ac63-4bd0-ba13-8c2ab17e7824
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 94c5f8f5e83578ca0a82b479ef5ef359738df5f1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-layout-of-a-datarepeater-control-visual-studio"></a>Como alterar o layout de um controle DataRepeater (Visual Studio)
O <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle pode ser exibido em um (itens de rolagem vertical) do vertical ou horizontal (itens de rolagem horizontal) orientação. Você pode alterar a orientação em tempo de design ou em tempo de execução alterando o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> propriedade. Se você alterar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> propriedade em tempo de execução, você talvez queira redimensionar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> e reposicionar os controles filho.  
  
> [!NOTE]
>  Se você reposicionar controles no <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> em tempo de execução, você precisará chamar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> e <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> métodos no início e no final do bloco de código que reposiciona os controles.  
  
### <a name="to-change-the-layout-at-design-time"></a>Para alterar o layout em tempo de design  
  
1.  No Designer de Formulários do Windows, selecione o controle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
    > [!NOTE]
    >  Você deve selecionar a borda externa do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle clicando na região inferior do controle, não na parte superior <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> região.  
  
2.  Na janela Propriedades, defina o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> propriedade como <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical> ou <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>.  
  
### <a name="to-change-the-layout-at-run-time"></a>Para alterar o layout em tempo de execução  
  
1.  Adicione o seguinte código para um menu ou botão `Click` manipulador de eventos:  
  
     [!code-csharp[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.vb)]  
  
2.  Na maioria dos casos, você desejará adicionar código semelhante ao mostrado na seção de exemplo para redimensionar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> e reorganizar os controles para se ajustar à nova orientação.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como responder a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyleChanged> evento em um manipulador de eventos. Este exemplo requer que você tenha um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle chamado `DataRepeater1` em um formulário e que seu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> contêm dois <xref:System.Windows.Forms.TextBox> controles denominados `TextBox1` e `TextBox2`.  
  
 [!code-csharp[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.cs)]
 [!code-vb[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A>  
 [Introdução ao Controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Solução de problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [Como alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
