---
title: Introdução ao controle DataRepeater (Visual Studio)
ms.date: 07/20/2015
helpviewer_keywords:
- repeating data
- DataRepeater, overview
- DataRepeater
ms.assetid: 78a52a1d-65f0-4ecb-97ff-53bc114300c5
ms.openlocfilehash: fc0cf9c358faf3e738eb3b24ec61577b88dbce4a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="introduction-to-the-datarepeater-control-visual-studio"></a>Introdução ao controle DataRepeater (Visual Studio)
O Visual Basic Power Packs <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle é um contêiner rolável para repetido de controles que exibem dados, por exemplo, as linhas em uma tabela de banco de dados. Ele pode ser usado como uma alternativa para o <xref:System.Windows.Forms.DataGridView> controlar quando precisar de mais controle sobre o layout dos dados. O <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> "repete" de um grupo de controles relacionados com a criação de várias instâncias em uma exibição da rolagem. Isso permite aos usuários exibir vários registros ao mesmo tempo.  
  
## <a name="overview"></a>Visão geral  
 Em tempo de design, o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle consiste em duas seções. A seção externa é o *visor*, onde os dados de rolagem serão exibidos em tempo de execução. A seção (superior) interna, conhecida como o *modelo de item*, é onde você posicionar controles que serão repetidos em tempo de execução, normalmente um controle para cada campo na fonte de dados. As propriedades e os controles no modelo de item são encapsulados no <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> propriedade.  
  
 Em tempo de execução, o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> é copiado para uma máquina virtual <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> objeto que é usado para exibir os dados quando cada registro é colocado na exibição. Você pode personalizar a exibição de registros individuais de <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> evento, por exemplo, realce um campo com base no valor que ele contém. Para obter mais informações, consulte [como: alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md).  
  
 O uso mais comum para um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> é de controle exibir dados de uma tabela de banco de dados ou outra fonte de dados associada. Além [!INCLUDE[vstecado](~/includes/vstecado-md.md)] objetos de dados, o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle pode se associar a qualquer classe que implementa o <xref:System.Collections.IList> interface (incluindo matrizes), qualquer classe que implementa o <xref:System.ComponentModel.IListSource> interface, qualquer classe que implementa o <xref:System.ComponentModel.IBindingList> interface ou qualquer classe que implementa o <xref:System.ComponentModel.IBindingListView> interface.  
  
### <a name="data-binding"></a>Associação de dados  
 Normalmente, você realizar a associação de dados arrastando campos do **fontes de dados** janela para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle. Para obter mais informações, consulte [como: exibir dados associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).  
  
 Ao trabalhar com grandes quantidades de dados, você pode definir o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> propriedade `True` para exibir um subconjunto dos dados disponíveis. Modo virtual requer a implementação de um cache de dados do qual o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> for preenchida, e você deve controlar todas as interações com o cache de dados em tempo de execução. Para obter mais informações, consulte [modo Virtual no controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md).  
  
 Você também pode exibir controles não associados em um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle. Por exemplo, você pode exibir uma imagem que é repetida em cada item. Para obter mais informações, consulte [como: exibição de controles não associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md).  
  
### <a name="events"></a>Eventos  
 Os eventos mais importantes para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle são o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> evento, que é disparado quando novos itens são rolados para a exibição, e o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged> evento, que é gerado quando um item é selecionado. Você pode usar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> evento para alterar a aparência do item. Por exemplo, você pode realçar valores negativos. Use o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged> evento para acessar os valores de controles quando um item é selecionado.  
  
 O <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle expõe todos os eventos de controle padrão no Editor de códigos. No entanto, alguns eventos não devem ser usado. Teclado e mouse eventos como `KeyDown`, `Click`, e `MouseDown` não serão gerados em tempo de execução porque o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> nunca o próprio controle tem foco.  
  
 O <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> não expõe eventos em tempo de design porque ele é criado apenas em tempo de execução. Se você desejar tratar eventos de teclado e mouse, você pode adicionar uma <xref:System.Windows.Forms.Panel> o controle para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> em tempo de design e, em seguida, manipular os eventos para o <xref:System.Windows.Forms.Panel>. Para obter mais informações, consulte [Solucionando problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md).  
  
### <a name="customizations"></a>Personalizações  
 Há várias maneiras de personalizar a aparência e comportamento do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controlar em tempo de execução e em tempo de design. Propriedades podem ser definidas para alterar cores, ocultar ou modificar os cabeçalhos de item, alterar a orientação de vertical para horizontal e muito mais. Para obter mais informações, consulte [como: alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md), [como: exibir cabeçalhos de Item em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md), e [como: alterar o Layout de um Controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md).  
  
 Observe que algumas propriedades se aplicam para a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> próprio controle enquanto outras se aplicam somente ao <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>. Certifique-se de que você tem a seção correta do controle selecionado para que você definir propriedades. Para obter mais informações, consulte [como: alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md).  
  
 Outras personalizações incluem controlando a capacidade de adicionar ou excluir registros, adicionando recursos de pesquisa e exibir dados relacionados em um formato mestre e de detalhes. Para obter mais informações, consulte [como: desabilitar adicionando e excluindo itens de DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md), [como: dados de pesquisa em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md), e [como: criar um formulário mestre/detalhado usando dois Controles DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md).  
  
## <a name="see-also"></a>Consulte também  
 [Controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/datarepeater-control-visual-studio.md)  
 [Instruções passo a passo: exibindo dados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio.md)  
 [Solução de problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
