---
title: 'Como: exibir dados associados em um controle DataRepeater (Visual Studio) | Documentos do Microsoft'
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- DataRepeater, data-binding
- DataRepeater, displaying bound controls
ms.assetid: 56a15326-1334-4275-af4e-075cad79e6f7
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
ms.openlocfilehash: 9bf8f2f5fcc4dfa2b29e368a4e26bf112e08149e
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-display-bound-data-in-a-datarepeater-control-visual-studio"></a>Como exibir dados associados em um controle DataRepeater (Visual Studio)
O uso mais comum de <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle é exibir dados associados de um banco de dados ou outra fonte de dados.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
 Além de controles associados, você talvez queira adicionar outros controles, como um rótulo estático ou uma imagem que é repetida em cada item a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Para obter mais informações, consulte [como: exibir controles não associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md).  
  
 Você também pode vincular a uma fonte de dados em tempo de execução, definindo o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>propriedade `True` e atribuindo a uma fonte de dados para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DataSource%2A>propriedade.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DataSource%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> Nesse caso, você precisará gerenciar toda a interação com a fonte de dados. Para obter mais informações, consulte [modo Virtual no controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md).  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-create-a-data-bound-datarepeater"></a>Para criar um DataRepeater ligados a dados  
  
1.  Arraste um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>de controle do **Visual Basic PowerPacks** guia o **Toolbox** a um controle de formulário ou contêiner.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
2.  Arraste as alças de dimensionamento e a posição para tamanho e posição do controle.  
  
     Observe que o controle tem duas regiões retangulares. Região superior é o *modelo de item*; controles adicionados ao modelo serão repetidos em cada item a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle em tempo de execução.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> A região inferior é o *visor*, onde os itens serão exibidos.  
  
     Você também pode redimensionar e posicionar o controle ou o modelo de item, alterando o **tamanho** e **posição** propriedades na janela Propriedades.  
  
3.  Sobre o **dados** menu, clique em **Show Data Sources**.  
  
    > [!NOTE]
    >  Se o **fontes de dados** janela estiver vazia, adicionar uma fonte de dados a ele. Para obter mais informações, consulte [adicionar novas fontes de dados](https://docs.microsoft.com/visualstudio/data-tools/add-new-data-sources).  
  
4.  No **fontes de dados** janela, selecione o nó de nível superior para a tabela que contém os dados que você deseja associar.  
  
5.  Altere o tipo subjacente da tabela para `Details` clicando `Details` na lista suspensa no nó da tabela.  
  
6.  Selecione o nó de tabela e arraste-o para a região de modelo de item do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
     Você pode especificar quais tipos de controles são exibidos para cada campo. Para obter mais informações, consulte [definir o controle a ser criado quando arrastado da janela fontes de dados](https://docs.microsoft.com/visualstudio/data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 [Introdução ao controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [Como: exibir controles não associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)   
 [Como: criar um formulário mestre/detalhes usando dois controles DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)   
 [Como: alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)   
 [Solução de problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
