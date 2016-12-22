---
title: "Como exibir controles n&#227;o associados em um controle DataRepeater (Visual Studio) | Microsoft Docs"
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
  - "DataRepeater"
  - "DataRepeater, adicionando controles não associados"
  - "exibindo dados não associados"
ms.assetid: f234fa40-5a13-4209-930e-7c5f81e86e66
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como exibir controles n&#227;o associados em um controle DataRepeater (Visual Studio)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Com controles acoplados, você talvez queira adicionar outros controles a uma <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, como um rótulo estático ou uma imagem que é repetida em cada item na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
> [!NOTE]
>  Você também deve ter pelo menos um controle acoplado na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ou nada será exibido em tempo de execução.  
  
### Para adicionar controles não acoplados a um DataRepeater  
  
1.  Arrastar um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controlar da  **Visual Basic PowerPacks** guia o  **caixa de ferramentas** a um controle de formulário ou recipiente.  
  
2.  Arraste as alças de dimensionamento e a posição, tamanho e posicione o controle.  
  
     Você também pode dimensionar e posicionar o controle, alterando a  **tamanho** e  **posição** propriedades na janela Propriedades.  
  
3.  Adicionar pelo menos um controle ligado a dados para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  Para obter mais informações, consulte [Como exibir dados associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).  
  
4.  Arraste um controle da  **caixa de ferramentas** para a área de modelo de item da <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
     Observe que o controle tem duas regiões retangulares.  A região interna é o  *modelo de item*; os controles adicionados ao modelo serão repetidos em cada item da <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> o controle em tempo de execução.  A região externa é o  *visor*, onde os itens serão exibidos; controles que são adicionados a essa região não serão exibidos em tempo de execução.  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 [Introdução ao controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [Solucionando problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)   
 [Como exibir dados associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)   
 [Como criar um formulário mestre\/detalhado usando dois controles DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)   
 [Como alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)