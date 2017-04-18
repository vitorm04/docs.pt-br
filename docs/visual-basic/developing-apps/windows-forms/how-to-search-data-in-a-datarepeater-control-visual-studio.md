---
title: 'Como: pesquisar dados em um controle DataRepeater (Visual Studio) | Documentos do Microsoft'
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- DataRepeater, implementing search
- DataRepeater, searching data
ms.assetid: a8ab5d17-b94f-43c4-8dd7-d0450226d73f
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7dfa7eb057d3bea87df878a802159c721be8b569
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-search-data-in-a-datarepeater-control-visual-studio"></a>Como pesquisar dados em um controle DataRepeater (Visual Studio)
Quando você estiver usando um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle que contém muitos registros, talvez você queira permitir que os usuários procurar um registro específico.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Em vez de pesquisar os dados no próprio controle, você pode implementar uma pesquisa por meio de consulta subjacente <xref:System.Windows.Forms.BindingSource>.</xref:System.Windows.Forms.BindingSource> Se o item for encontrado, você pode usar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndex%2A>propriedade para selecionar o item e rolá-lo no modo de exibição.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndex%2A>  
  
### <a name="to-implement-search"></a>Para implementar a pesquisa  
  
1.  Arraste um <xref:System.Windows.Forms.TextBox>de controle do **Toolbox** para o formulário que contém o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> </xref:System.Windows.Forms.TextBox>  
  
2.  Na janela Propriedades, altere o **nome** propriedade **SearchTextBox**.  
  
3.  Arraste um <xref:System.Windows.Forms.Button>de controle do **Toolbox** para o formulário que contém o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> </xref:System.Windows.Forms.Button>  
  
4.  Na janela Propriedades, altere o **nome** propriedade **SearchButton**. Alterar o **texto** propriedade **pesquisa**.  
  
5.  Clique duas vezes o <xref:System.Windows.Forms.Button>de controle para abrir o Editor de códigos e adicione o seguinte código para o `SearchButton_Click` manipulador de eventos.</xref:System.Windows.Forms.Button>  
  
     [!code-vb[&#1; VbPowerPacksDataRepeaterSearch](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-search-data-in-a-datarepeater-control-visual-studio_1.vb) ] 
     [!code-cs [VbPowerPacksDataRepeaterSearch n º&1;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-search-data-in-a-datarepeater-control-visual-studio_1.cs)]  
  
     Substitua *ProductsBindingSource* com o nome do <xref:System.Windows.Forms.BindingSource>para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>e substitua *ProductID* com o nome do campo que você deseja pesquisar.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> </xref:System.Windows.Forms.BindingSource>  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 [Introdução ao controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [Solucionando problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)   
 [Como alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
