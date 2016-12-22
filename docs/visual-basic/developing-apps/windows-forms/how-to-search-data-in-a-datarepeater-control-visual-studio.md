---
title: "Como pesquisar dados em um controle DataRepeater (Visual Studio) | Microsoft Docs"
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
  - "DataRepeater, implementando pesquisa"
  - "DataRepeater, pesquisando dados"
ms.assetid: a8ab5d17-b94f-43c4-8dd7-d0450226d73f
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como pesquisar dados em um controle DataRepeater (Visual Studio)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Quando você estiver usando um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle que contém muitos registros, você pode querer permitir que os usuários de pesquisa para um registro específico.  Em vez de pesquisar os dados no próprio controle, você pode implementar uma pesquisa por meio de consulta base <xref:System.Windows.Forms.BindingSource>.  Se o item for encontrado, você pode usar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndex%2A> propriedade para selecionar o item e rolá\-lo no modo de exibição.  
  
### Para implementar a pesquisa  
  
1.  Arrastar um <xref:System.Windows.Forms.TextBox> controlar a partir de  **Toolbox** para o formulário que contém o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
2.  Na janela Properties, altere o  **nome** propriedade para SearchTextBox.  
  
3.  Arrastar um <xref:System.Windows.Forms.Button> controlar a partir de  **Toolbox** para o formulário que contém o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
4.  Na janela Properties, altere o  **nome** propriedade para SearchButton.  Alterar o  **texto** propriedade para pesquisa.  
  
5.  Clique duas vezes o <xref:System.Windows.Forms.Button> o controle para abrir o Editor de código e, em seguida, adicione o seguinte código para o `SearchButton_Click` manipulador de eventos.  
  
     [!code-vb[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-search-data-in-a-datarepeater-control-visual-studio_1.vb)]
     [!code-cs[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-search-data-in-a-datarepeater-control-visual-studio_1.cs)]  
  
     Substitua  *ProductsBindingSource* com o nome da <xref:System.Windows.Forms.BindingSource> para seu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>e substituir  *ProductID* com o nome do campo que você deseja pesquisar.  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 [Introdução ao controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [Solucionando problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)   
 [Como alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)