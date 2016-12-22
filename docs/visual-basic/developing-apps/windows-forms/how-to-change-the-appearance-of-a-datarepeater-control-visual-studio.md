---
title: "Como alterar a apar&#234;ncia de um controle DataRepeater (Visual Studio) | Microsoft Docs"
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
  - "DataRepeater, alterando a aparência de tempo de execução"
  - "DataRepeater, personalizando"
ms.assetid: 2af6dfce-760b-489e-b863-8da967f315c3
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como alterar a apar&#234;ncia de um controle DataRepeater (Visual Studio)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Você pode alterar a aparência de um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle em tempo de design, definindo propriedades ou em tempo de execução pelo tratamento a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> evento.  
  
 Propriedades que podem ser definidas em tempo de design quando a seção de modelo de item do controle é selecionada serão repetidas para cada <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> em tempo de execução.  Propriedades relacionadas a aparência da <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle propriamente dito ficará visível em tempo de execução somente se uma parte do contêiner é deixado revelado \(por exemplo, se a <xref:System.Windows.Forms.Control.Padding%2A> propriedade estiver definida como um valor grande\).  
  
 Em tempo de execução, propriedades relacionadas à aparência podem ser definidas com base nas condições.  Por exemplo, em um aplicativo de agendamento, você pode alterar a cor de plano de fundo de um item para avisar os usuários quando um item está vencido.  No <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> manipulador de eventos, se você definir uma propriedade em uma instrução condicional, tais como `If…Then`, você também deve usar um `Else` cláusula para especificar a aparência quando a condição não for atendida.  
  
### Para alterar a aparência em tempo de design  
  
1.  No Windows Forms Designer, selecione a região de modelo \(superior\) do item da <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
2.  Na janela Properties, selecione uma propriedade e alterar o valor.  Propriedades comuns que afetam a aparência incluem <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Panel.BorderStyle%2A>, e <xref:System.Windows.Forms.Control.ForeColor%2A>.  
  
### Para alterar a aparência em tempo de execução  
  
1.  No Editor de código, além de eventos na lista suspensa, clique em  **DrawItem**.  
  
2.  No <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> o manipulador de eventos, adicione código para definir as propriedades:  
  
     [!code-cs[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.vb)]  
  
## Exemplo  
 Algumas personalizações comuns para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle incluem exibir as linhas em cores alternadas e alterando a cor de um campo com base em uma condição.  O exemplo a seguir mostra como realizar essas personalizações.  Este exemplo presume que você tenha um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle está acoplado à tabela Produtos no banco de dados Northwind.  
  
 [!code-vb[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.vb)]
 [!code-cs[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.cs)]  
  
 Observe que, para ambas essas personalizações, você deve fornecer o código para definir as propriedades de ambos os lados da condição.  Se você não especificar o `Else` condição, você verá resultados inesperados em tempo de execução.  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>   
 [Introdução ao controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [Solucionando problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)   
 [Como exibir dados associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)   
 [Como exibir controles não associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)   
 [Como exibir cabeçalhos de item em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)