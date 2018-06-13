---
title: Como pesquisar dados em um controle DataRepeater (Visual Studio)
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, implementing search
- DataRepeater, searching data
ms.assetid: a8ab5d17-b94f-43c4-8dd7-d0450226d73f
ms.openlocfilehash: 689990ee125c85c3151a4e965b619fde068d220e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588048"
---
# <a name="how-to-search-data-in-a-datarepeater-control-visual-studio"></a>Como pesquisar dados em um controle DataRepeater (Visual Studio)
Quando você estiver usando um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle que contém muitos registros, talvez você queira permitir que os usuários de pesquisa para um registro específico. Em vez de pesquisar os dados no controle em si, você pode implementar uma pesquisa por meio de consulta subjacente <xref:System.Windows.Forms.BindingSource>. Se o item for encontrado, você pode usar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndex%2A> propriedade para selecionar o item e rolá-lo no modo de exibição.  
  
### <a name="to-implement-search"></a>Para implementar a pesquisa  
  
1.  Arraste um <xref:System.Windows.Forms.TextBox> controlar do **caixa de ferramentas** para o formulário que contém o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
2.  Na janela Propriedades, altere o **nome** propriedade **SearchTextBox**.  
  
3.  Arraste um <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** para o formulário que contém o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
4.  Na janela Propriedades, altere o **nome** propriedade **SearchButton**. Alterar o **texto** propriedade **pesquisa**.  
  
5.  Clique duas vezes o <xref:System.Windows.Forms.Button> de controle para abrir o Editor de código e adicione o seguinte código para o `SearchButton_Click` manipulador de eventos.  
  
     [!code-vb[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-search-data-in-a-datarepeater-control-visual-studio_1.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-search-data-in-a-datarepeater-control-visual-studio_1.cs)]  
  
     Substituir *ProductsBindingSource* com o nome do <xref:System.Windows.Forms.BindingSource> para sua <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>e substitua *ProductID* com o nome do campo que você deseja pesquisar.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [Introdução ao Controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Solução de problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [Como alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
