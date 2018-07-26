---
title: 'Como: criar um formulário mestre / detalhes usando dois controles DataRepeater (Visual Studio)'
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, master/detail tables
ms.assetid: eec43ae3-05d8-45a1-8d41-3803c6359dbe
ms.openlocfilehash: 84639a5d49a3fa4a8c6845793c39fc8a67c31e02
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245513"
---
# <a name="how-to-create-a-masterdetail-form-by-using-two-datarepeater-controls-visual-studio"></a>Como criar um formulário mestre/detalhado usando dois controles DataRepeater (Visual Studio)
Você pode exibir dados relacionados usando dois ou mais <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controles para criar um formulário mestre/detalhes. Por exemplo, você talvez queira exibir uma lista de clientes em um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>e quando o usuário seleciona um cliente, exibir uma lista de pedidos do cliente em um segundo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
 Você pode exibir dados relacionados, arrastando os itens de detalhe que compartilham o mesmo nó da tabela mestre do **fontes de dados** window para um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle. Por exemplo, se você tiver uma fonte de dados que tem uma tabela de clientes e uma tabela Pedidos relacionada, você ver ambas as tabelas como nós de nível superior na exibição de árvore na **fontes de dados** janela. Expanda o nó de clientes para que você possa ver as colunas. Observe que a última coluna na lista é um nó expansível que representa a tabela de pedidos. Este nó representa os pedidos relacionados para um cliente.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-display-related-data-in-two-datarepeater-controls"></a>Para exibir dados relacionados em dois controles DataRepeater  
  
1.  Arraste duas <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controles do **Visual Basic PowerPacks** guia o **caixa de ferramentas** a um controle de formulário ou contêiner.  
  
2.  Arraste as alças de dimensionamento e a posição para dimensionar os controles e posicioná-los lado a lado.  
  
3.  Sobre o **dados** menu, clique em **Show Data Sources**.  
  
    > [!NOTE]
    >  Se o **fontes de dados** janela estiver vazia, adicione uma fonte de dados a ele. Para obter mais informações, consulte [Adicionar novas fontes de dados](/visualstudio/data-tools/add-new-data-sources).  
  
4.  No **fontes de dados** janela, selecione o nó de nível superior para a tabela mestre.  
  
5.  Alterar o tipo subjacente da tabela mestra de detalhes clicando **detalhes** na lista suspensa no nó da tabela.  
  
6.  Arraste o nó de tabela mestre para a região de modelo de item do primeiro <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
7.  Expanda o nó mestre de tabela e selecione o nó de detalhe para a tabela relacionada.  
  
8.  Alterar o tipo subjacente da tabela de detalhes para obter detalhes clicando **detalhes** na lista suspensa no nó da tabela.  
  
9. Selecione este nó de tabela e arraste-o para a região de modelo de item do segundo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [Introdução ao Controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Como exibir dados associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [Como exibir dados relacionados em um Aplicativo do Windows Forms](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio)  
 [Como alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [Solução de problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
