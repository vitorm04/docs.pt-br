---
title: "Como: alterar a aparência de um controle DataRepeater (Visual Studio) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- DataRepeater, customizing
- DataRepeater, changing run time appearance
ms.assetid: 2af6dfce-760b-489e-b863-8da967f315c3
caps.latest.revision: 12
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
ms.openlocfilehash: 8380bfca247efaa8556473e92d73726a11eb262a
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-change-the-appearance-of-a-datarepeater-control-visual-studio"></a>Como alterar a aparência de um controle DataRepeater (Visual Studio)
Você pode alterar a aparência de um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle em tempo de design, definindo propriedades ou em tempo de execução manipulando o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>evento.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
 Propriedades que podem ser definidas em tempo de design, quando é selecionada a seção de modelo de item do controle serão repetidas para cada <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>em tempo de execução.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> Propriedades relacionadas à aparência do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>próprio controle ficará visível em tempo de execução somente se uma parte do contêiner é deixado descoberto (por exemplo, se o <xref:System.Windows.Forms.Control.Padding%2A>propriedade é definida como um valor grande).</xref:System.Windows.Forms.Control.Padding%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
 Em tempo de execução propriedades relacionadas à aparência podem ser definidas com base em condições. Por exemplo, em um aplicativo de planejamento, você pode alterar a cor de plano de fundo de um item para avisar os usuários quando um item está vencido. No <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>manipulador de eventos, se você definir uma propriedade em uma instrução condicional, como `If…Then`, você também deve usar um `Else` cláusula para especificar a aparência de quando a condição não for atendidos.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>  
  
### <a name="to-change-the-appearance-at-design-time"></a>Para alterar a aparência em tempo de design  
  
1.  No Windows Forms Designer, selecione a região de modelo (superior) do item do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
2.  Na janela Propriedades, selecione uma propriedade e altere o valor. Propriedades comuns que afetam a aparência incluem <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Panel.BorderStyle%2A>e <xref:System.Windows.Forms.Control.ForeColor%2A>.</xref:System.Windows.Forms.Control.ForeColor%2A> </xref:System.Windows.Forms.Panel.BorderStyle%2A> </xref:System.Windows.Forms.Control.BackgroundImage%2A> </xref:System.Windows.Forms.Control.BackColor%2A>  
  
### <a name="to-change-the-appearance-at-run-time"></a>Para alterar a aparência em tempo de execução  
  
1.  No Editor de código, lista suspensa de eventos, clique em **DrawItem**.  
  
2.  No <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>manipulador de eventos, adicione código para definir as propriedades:</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>  
  
     [!code-cs[&#1; VbPowerPacksDataRepeaterAppearance](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterAppearance n º&1;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.vb)]  
  
## <a name="example"></a>Exemplo  
 Algumas personalizações comuns para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle incluem exibindo as linhas em cores alternadas e alterando a cor de um campo com base em uma condição.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> O exemplo a seguir mostra como realizar essas personalizações. Este exemplo pressupõe que você tenha um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle ligado à tabela Produtos no banco de dados Northwind.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
 [!code-vb[&#1; VbPowerPacksDataRepeaterAlternateBackColor](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.vb) ] 
 [!code-cs [VbPowerPacksDataRepeaterAlternateBackColor n º&1;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.cs)]  
  
 Observe que, para ambas essas personalizações, você deve fornecer o código para definir as propriedades de ambos os lados da condição. Se você não especificar o `Else` condição, você verá resultados inesperados em tempo de execução.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>   
 [Introdução ao controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [Solucionando problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)   
 [Como: exibir dados associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)   
 [Como: exibir controles não associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)   
 [Como exibir cabeçalhos de item em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)
