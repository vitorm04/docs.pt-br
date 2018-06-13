---
title: Como exibir dados associados em um controle DataRepeater (Visual Studio)
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, data-binding
- DataRepeater, displaying bound controls
ms.assetid: 56a15326-1334-4275-af4e-075cad79e6f7
ms.openlocfilehash: b96fb33a0dcf80a86d1fcb6e219e5f35b1f7351c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589861"
---
# <a name="how-to-display-bound-data-in-a-datarepeater-control-visual-studio"></a>Como exibir dados associados em um controle DataRepeater (Visual Studio)
O uso mais comum dos <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle é exibir dados associados de um banco de dados ou outra fonte de dados.  
  
 Além de controles associados, você talvez queira adicionar outros controles, como um rótulo estático ou uma imagem que é repetida em cada item a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle. Para obter mais informações, consulte [como: exibição de controles não associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md).  
  
 Você também pode associar a uma fonte de dados em tempo de execução, definindo o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> propriedade `True` e a atribuição de uma fonte de dados para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DataSource%2A> propriedade. Nesse caso, você precisará gerenciar toda a interação com a fonte de dados. Para obter mais informações, consulte [modo Virtual no controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-data-bound-datarepeater"></a>Para criar um associação de dados DataRepeater  
  
1.  Arraste um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controlar do **Visual Basic PowerPacks** guia o **caixa de ferramentas** a um controle de formulário ou contêiner.  
  
2.  Arraste as alças de dimensionamento e a posição para o tamanho e posição do controle.  
  
     Observe que o controle tem duas regiões retangulares. A região superior é o *modelo de item*; controles adicionados para o modelo serão repetidos em cada item a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle em tempo de execução. A região inferior é o *visor*, onde os itens serão exibidos.  
  
     Você também pode dimensionar e posicionar o controle ou o modelo de item, alterando o **tamanho** e **posição** propriedades na janela Propriedades.  
  
3.  Sobre o **dados** menu, clique em **Mostrar fontes de dados**.  
  
    > [!NOTE]
    >  Se o **fontes de dados** janela estiver vazia, adicionar uma fonte de dados a ele. Para obter mais informações, consulte [Adicionar novas fontes de dados](/visualstudio/data-tools/add-new-data-sources).  
  
4.  No **fontes de dados** janela, selecione o nó de nível superior para a tabela que contém os dados que você deseja vincular.  
  
5.  Altere o tipo subjacente da tabela para `Details` clicando `Details` na lista suspensa no nó da tabela.  
  
6.  Selecione o nó de tabela e arraste-o para a região de modelo de item do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
     Você pode especificar quais tipos de controles são exibidos para cada campo. Para obter mais informações, consulte [definir o controle a ser criado quando arrastado da janela fontes de dados](/visualstudio/data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [Introdução ao Controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Como exibir controles não associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [Como: criar um formulário mestre/detalhado usando dois controles DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)  
 [Como alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [Solução de problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
