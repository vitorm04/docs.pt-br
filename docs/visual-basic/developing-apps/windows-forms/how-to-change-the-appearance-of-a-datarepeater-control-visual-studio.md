---
title: 'Como: Alterar a aparência de um controle DataRepeater (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, customizing
- DataRepeater, changing run time appearance
ms.assetid: 2af6dfce-760b-489e-b863-8da967f315c3
ms.openlocfilehash: e5508329ba716b53eff0c9e1bfe13e190fa1fd85
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716629"
---
# <a name="how-to-change-the-appearance-of-a-datarepeater-control-visual-studio"></a>Como: Alterar a aparência de um controle DataRepeater (Visual Studio)
Você pode alterar a aparência de um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle em tempo de design, definindo as propriedades ou no tempo de execução manipulando o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> eventos.  
  
 Propriedades que podem ser definidas em tempo de design quando a seção de modelo de item do controle é selecionada serão repetidas para cada <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> em tempo de execução. Propriedades relacionadas à aparência do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> próprio controle ficará visível no tempo de execução somente se uma parte do contêiner é deixada revelado (por exemplo, se o <xref:System.Windows.Forms.Control.Padding%2A> estiver definida como um valor grande).  
  
 Em tempo de execução relacionadas à aparência propriedades podem ser definidas com base nas condições. Por exemplo, em um aplicativo de agendamento, você pode alterar a cor do plano de fundo de um item para avisar os usuários quando um item está atrasado. No <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> manipulador de eventos, se você definir uma propriedade em uma instrução condicional, como `If…Then`, você também deve usar um `Else` cláusula para especificar a aparência de quando a condição não for atendida.  
  
### <a name="to-change-the-appearance-at-design-time"></a>Para alterar a aparência em tempo de design  
  
1.  No Designer de formulários do Windows, selecione a região de modelo (superior) do item do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
2.  Na janela Propriedades, selecione uma propriedade e altere o valor. Incluem propriedades comuns que afetam a aparência <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Panel.BorderStyle%2A>, e <xref:System.Windows.Forms.Control.ForeColor%2A>.  
  
### <a name="to-change-the-appearance-at-run-time"></a>Para alterar a aparência em tempo de execução  
  
1.  No Editor de código, lista suspensa de eventos, clique em **DrawItem**.  
  
2.  No <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> manipulador de eventos, adicione código para definir as propriedades:  
  
     [!code-csharp[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.vb)]  
  
## <a name="example"></a>Exemplo  
 Algumas personalizações comuns para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle incluem a exibição de linhas em cores alternadas e alterando a cor de um campo com base em uma condição. O exemplo a seguir mostra como executar essas personalizações. Este exemplo pressupõe que você tenha um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle que está associado à tabela Produtos no banco de dados Northwind.  
  
 [!code-vb[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.vb)]
 [!code-csharp[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.cs)]  
  
 Observe que, para ambas essas personalizações, você deve fornecer o código para definir as propriedades de ambos os lados da condição. Se você não especificar o `Else` condição, você verá resultados inesperados em tempo de execução.  
  
## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>
- [Introdução ao Controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [Solução de problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
- [Como: Exibir dados associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)
- [Como: Exibir controles não associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)
- [Como: Exibir cabeçalhos de Item em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)
