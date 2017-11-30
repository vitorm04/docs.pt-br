---
title: "Como exibir controles não associados em um controle DataRepeater (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- DataRepeater, adding unbound controls
- DataRepeater
- displaying unbound data
ms.assetid: f234fa40-5a13-4209-930e-7c5f81e86e66
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3e96219f0ea8b8198967e9fa3c6e5afb824352db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio"></a>Como exibir controles não associados em um controle DataRepeater (Visual Studio)
Além de controles associados, você talvez queira adicionar outros controles para um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, como um rótulo estático ou uma imagem que é repetida em cada item a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
> [!NOTE]
>  Você também deve ter pelo menos um controle associado no <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ou nada será exibido em tempo de execução.  
  
### <a name="to-add-unbound-controls-to-a-datarepeater"></a>Para adicionar controles não associados a um DataRepeater  
  
1.  Arraste um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controlar do **Visual Basic PowerPacks** guia o **caixa de ferramentas** a um controle de formulário ou contêiner.  
  
2.  Arraste as alças de dimensionamento e a posição para o tamanho e posição do controle.  
  
     Você também pode dimensionar e posicionar o controle alterando o **tamanho** e **posição** propriedades na janela Propriedades.  
  
3.  Adicione pelo menos um controle associado a dados para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle. Para obter mais informações, consulte [como: exibir dados associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).  
  
4.  Arraste um controle do **caixa de ferramentas** para a área de modelo de item do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
     Observe que o controle tem duas regiões retangulares. A região interna é o *modelo de item*; controles adicionados para o modelo serão repetidos em cada item a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle em tempo de execução. A região externa é o *visor*, onde os itens serão exibidos; controles que são adicionados a esta região não serão exibidos em tempo de execução.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [Introdução ao Controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Solução de problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [Como exibir dados associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [Como: criar um formulário mestre/detalhado usando dois controles DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)  
 [Como alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
