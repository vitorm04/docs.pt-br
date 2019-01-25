---
title: 'Como: Exibir controles não associados em um controle DataRepeater (Visual Studio)'
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, adding unbound controls
- DataRepeater
- displaying unbound data
ms.assetid: f234fa40-5a13-4209-930e-7c5f81e86e66
ms.openlocfilehash: a20e1ba83d1963bc3d4c135817767ee02fcbdeda
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730783"
---
# <a name="how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio"></a>Como: Exibir controles não associados em um controle DataRepeater (Visual Studio)
Além de controles associados, você talvez queira adicionar outros controles para um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, como um rótulo estático ou uma imagem que é repetida em cada item no <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
> [!NOTE]
>  Você também deve ter pelo menos um controle associado no <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ou nada será exibido em tempo de execução.  
  
### <a name="to-add-unbound-controls-to-a-datarepeater"></a>Para adicionar controles não associados a um DataRepeater  
  
1.  Arraste uma <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controlar do **Visual Basic PowerPacks** guia o **caixa de ferramentas** a um controle de formulário ou contêiner.  
  
2.  Arraste as alças de dimensionamento e a posição para o tamanho e posicionar o controle.  
  
     Você também pode dimensionar e posicionar o controle, alterando a **tamanho** e **posição** propriedades na janela Propriedades.  
  
3.  Adicione pelo menos um controle associado a dados para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle. Para obter mais informações, confira [Como: Exibir dados associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).  
  
4.  Arraste um controle dos **caixa de ferramentas** para a área de modelo de item do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
     Observe que o controle tem duas regiões retangulares. A região interna é o *modelo de item*; controles adicionados ao modelo serão repetidos em cada item o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle em tempo de execução. A região externa é a *visor*, onde os itens serão exibidos; controles que são adicionados a essa região não serão exibidos no tempo de execução.  
  
## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- [Introdução ao Controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [Solução de problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
- [Como: Exibir dados associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)
- [Como: Criar um formulário mestre/detalhes usando dois controles DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)
- [Como: Alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
