---
title: "Como: criar um formulário mestre-detalhes usando dois controles DataRepeater (Visual Studio) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- DataRepeater, master/detail tables
ms.assetid: eec43ae3-05d8-45a1-8d41-3803c6359dbe
caps.latest.revision: 7
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
ms.openlocfilehash: 23789bb11cab17b50928651e1dc00d5d59640c0f
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-a-masterdetail-form-by-using-two-datarepeater-controls-visual-studio"></a>Como criar um formulário mestre/detalhado usando dois controles DataRepeater (Visual Studio)
Você pode exibir dados relacionados usando dois ou mais <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controles para criar um formulário mestre/detalhes.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Por exemplo, você talvez queira exibir uma lista de clientes em um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>e quando o usuário seleciona um cliente, exibir uma lista de pedidos do cliente em um segundo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
 Você pode exibir dados relacionados, arrastando os itens de detalhe que compartilham o mesmo nó da tabela principal do **fontes de dados** janela para um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Por exemplo, se você tiver uma fonte de dados que tenha uma tabela clientes e uma tabela relacionada Orders, você ver ambas as tabelas como nós superiores na exibição de árvore no **fontes de dados** janela. Expanda o nó Customers para que você possa ver as colunas. Observe que a última coluna da lista é um nó expansível que representa a tabela Orders. Este nó representa os pedidos relacionados para um cliente.  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-display-related-data-in-two-datarepeater-controls"></a>Para exibir dados relacionados em dois controles DataRepeater  
  
1.  Arraste dois <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controles do **Visual Basic PowerPacks** guia de **Toolbox** a um controle de formulário ou contêiner.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
2.  Arraste as alças de dimensionamento e a posição para dimensionar os controles e posicioná-los lado a lado.  
  
3.  Sobre o **dados** menu, clique em **Show Data Sources**.  
  
    > [!NOTE]
    >  Se o **fontes de dados** janela estiver vazia, adicionar uma fonte de dados a ele. Para obter mais informações, consulte [adicionar novas fontes de dados](https://docs.microsoft.com/visualstudio/data-tools/add-new-data-sources).  
  
4.  No **fontes de dados** janela, selecione o nó de nível superior para a tabela principal.  
  
5.  Altere o tipo subjacente da tabela mestra de detalhes clicando em **detalhes** na lista suspensa no nó da tabela.  
  
6.  Arraste o nó tabela mestre para a região de modelo de item do primeiro <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
7.  Expanda o nó de tabela mestre e selecione o nó de detalhes para a tabela relacionada.  
  
8.  Alterar o tipo subjacente da tabela de detalhes para obter detalhes, clicando em **detalhes** na lista suspensa no nó da tabela.  
  
9. Selecione este nó de tabela e arraste-o para a região de modelo de item da segunda <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 [Introdução ao controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [Como: exibir dados associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)   
 [Como: Exibir relacionados a dados em um Windows Forms Application](http://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd)   
 [Como: alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)   
 [Solução de problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
