---
title: "Como exibir dados associados em um controle DataRepeater (Visual Studio) | Microsoft Docs"
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
  - "DataRepeater, associação de dados"
  - "DataRepeater, exibindo controles associados"
ms.assetid: 56a15326-1334-4275-af4e-075cad79e6f7
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como exibir dados associados em um controle DataRepeater (Visual Studio)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O uso mais comum de <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> é de controle exibir dados acoplados de um banco de dados ou outra fonte de dados.  
  
 Com controles acoplados, você talvez queira adicionar outros controles, como, por exemplo, um rótulo estático ou uma imagem que é repetida em cada item da <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  Para obter mais informações, consulte [Como exibir controles não associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md).  
  
 Você também pode vincular a uma fonte de dados em tempo de execução, definindo a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> propriedade para `True` e a atribuição de uma fonte de dados para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DataSource%2A> propriedade.  Nesse caso, você precisará gerenciar toda a interação com a fonte de dados.  Para obter mais informações, consulte [Modo virtual no controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md).  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### Para criar um DataRepeater ligados a dados  
  
1.  Arrastar um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controlar da  **Visual Basic PowerPacks** guia o  **caixa de ferramentas** a um controle de formulário ou recipiente.  
  
2.  Arraste as alças de dimensionamento e a posição, tamanho e posicione o controle.  
  
     Observe que o controle tem duas regiões retangulares.  Região superior é o  *modelo de item*; os controles adicionados ao modelo serão repetidos em cada item da <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> o controle em tempo de execução.  A região inferior é o  *visor*, onde os itens serão exibidos.  
  
     Você também pode dimensionar e posicionar o controle ou o modelo de item, alterando a  **tamanho** e  **posição** propriedades na janela Propriedades.  
  
3.  No menu **Data**, clique em **Show Data Sources**.  
  
    > [!NOTE]
    >  Se a janela **Data Sources** estiver vazia, adicionar uma fonte de dados a ela.  Para obter mais informações, consulte [Adicionar novas fontes de dados](/visual-studio/data-tools/add-new-data-sources).  
  
4.  No  **Fontes de dados** janela, selecione o nó de nível superior para a tabela que contém os dados que você deseja vincular.  
  
5.  Altere o tipo subjacente da tabela para `Details` , clicando em `Details` na lista drop\-down no nó da tabela.  
  
6.  Selecione o nó de tabela e arraste\-o para a região de modelo de item a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
     Você pode especificar quais tipos de controles que são exibidos para cada campo.  Para obter mais informações, consulte [Como definir o controle a ser criado quando arrastado da janela Fontes de Dados](/visual-studio/data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window).  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 [Introdução ao controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [Como exibir controles não associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)   
 [Como criar um formulário mestre\/detalhado usando dois controles DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)   
 [Como alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)   
 [Solucionando problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)