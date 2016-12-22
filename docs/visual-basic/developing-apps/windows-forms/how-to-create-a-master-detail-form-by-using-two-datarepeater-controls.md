---
title: "Como criar um formul&#225;rio mestre/detalhado usando dois controles DataRepeater (Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "DataRepeater, tabelas de detalhes/mestre"
ms.assetid: eec43ae3-05d8-45a1-8d41-3803c6359dbe
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como criar um formul&#225;rio mestre/detalhado usando dois controles DataRepeater (Visual Studio)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Você pode exibir dados relacionados usando dois ou mais <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controles para criar um formulário mestre\/detalhes.  Por exemplo, você talvez queira exibir uma lista de clientes em um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>e quando o usuário seleciona um cliente, exibir uma lista dos pedidos do cliente em um segundo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
 Você pode exibir dados relacionados arrastando itens de detalhe que compartilham o mesmo nó de tabela mestre a partir do  **Fontes de dados** janela para um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  Por exemplo, se você tiver uma fonte de dados que tenha uma tabela clientes e uma tabela relacionada Orders, você ver ambas as tabelas como nós superiores na exibição em árvore no  **Fontes de dados** janela.  Expanda o nó Customers para que você possa ver as colunas.  Observe que a última coluna na lista é um nó expansível que representa a tabela Pedidos.  Este nó representa os pedidos relacionados de um cliente.  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### Para exibir dados relacionados em dois controles DataRepeater  
  
1.  Arraste dois <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controla a partir o  **Visual Basic PowerPacks** guia o  **caixa de ferramentas** a um controle de formulário ou recipiente.  
  
2.  Arraste as alças de dimensionamento e a posição para dimensionar os controles e posicioná\-los lado a lado.  
  
3.  No menu **Data**, clique em **Show Data Sources**.  
  
    > [!NOTE]
    >  Se a janela **Data Sources** estiver vazia, adicionar uma fonte de dados a ela.  Para obter mais informações, consulte [Adicionar novas fontes de dados](/visual-studio/data-tools/add-new-data-sources).  
  
4.  No  **Fontes de dados** janela, selecione o nó de nível superior para a tabela mestre.  
  
5.  Alterar o tipo subjacente da tabela mestre detalhes clicando em  **detalhes** na lista drop\-down no nó da tabela.  
  
6.  Arraste o nó de tabela mestre para a região de modelo de item do primeiro <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
7.  Expanda o nó de tabela mestre e selecione o nó de detalhe para a tabela relacionada.  
  
8.  Alterar o tipo subjacente da tabela de detalhe detalhes clicando em  **detalhes** na lista drop\-down no nó da tabela.  
  
9. Selecione este nó de tabela e arraste\-o para a região de modelo de item da segunda <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 [Introdução ao controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [Como exibir dados associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)   
 [Como exibir dados relacionados em um Aplicativo do Windows Forms](../Topic/How%20to:%20Display%20Related%20Data%20in%20a%20Windows%20Forms%20Application.md)   
 [Como alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)   
 [Solucionando problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)