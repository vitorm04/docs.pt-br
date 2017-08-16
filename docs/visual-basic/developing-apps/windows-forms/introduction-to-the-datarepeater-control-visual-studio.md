---
title: "Introdução ao controle DataRepeater (Visual Studio) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- repeating data
- DataRepeater, overview
- DataRepeater
ms.assetid: 78a52a1d-65f0-4ecb-97ff-53bc114300c5
caps.latest.revision: 8
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
ms.openlocfilehash: 86078426494caabefc6bbfb036037007e830e1cb
ms.lasthandoff: 03/13/2017

---
# <a name="introduction-to-the-datarepeater-control-visual-studio"></a>Introdução ao controle DataRepeater (Visual Studio)
O Visual Basic Power Packs <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle é um contêiner rolável para repetido de controles que exibem dados, por exemplo, as linhas em uma tabela de banco de dados.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Ele pode ser usado como uma alternativa para o <xref:System.Windows.Forms.DataGridView>controlar quando você precisar de mais controle sobre o layout dos dados.</xref:System.Windows.Forms.DataGridView> O <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>"repete" de um grupo de controles relacionados Criando várias instâncias em um modo de rolagem.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Isso permite aos usuários exibir vários registros ao mesmo tempo.  
  
## <a name="overview"></a>Visão geral  
 Em tempo de design, o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle consiste em duas seções.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> A seção externa é o *visor*, onde os dados de rolagem serão exibidos em tempo de execução. A seção (superior) interna, conhecida como o *modelo de item*, é onde posicionar os controles que serão repetidos em tempo de execução, normalmente um controle para cada campo na fonte de dados. As propriedades e os controles no modelo de item são encapsulados no <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>propriedade.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>  
  
 Em tempo de execução, o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>é copiado para uma máquina virtual <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>objeto que é usado para exibir os dados quando cada registro é colocado na exibição.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> Você pode personalizar a exibição de registros individuais a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>evento, por exemplo, realce um campo com base no valor que ele contém.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> Para obter mais informações, consulte [como: alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md).  
  
 O uso mais comum para um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle é exibir dados de uma tabela de banco de dados ou outra fonte de dados ligada.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Além [!INCLUDE[vstecado](../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)] objetos de dados, o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle pode vincular a qualquer classe que implementa o <xref:System.Collections.IList>interface (incluindo matrizes), qualquer classe que implementa o <xref:System.ComponentModel.IListSource>interface, qualquer classe que implementa o <xref:System.ComponentModel.IBindingList>interface ou qualquer classe que implementa o <xref:System.ComponentModel.IBindingListView>interface.</xref:System.ComponentModel.IBindingListView> </xref:System.ComponentModel.IBindingList> </xref:System.ComponentModel.IListSource> </xref:System.Collections.IList> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
### <a name="data-binding"></a>Associação de dados  
 Normalmente, executar associação de dados arrastando campos do **fontes de dados** janela para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Para obter mais informações, consulte [como: exibir dados associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).  
  
 Ao trabalhar com grandes quantidades de dados, você pode definir o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>propriedade `True` para exibir um subconjunto dos dados disponíveis.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> Modo virtual requer a implementação de um cache de dados do qual o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>é preenchida, e você deve controlar todas as interações com o cache de dados em tempo de execução.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Para obter mais informações, consulte [modo Virtual no controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md).  
  
 Você também pode exibir controles não associados em um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Por exemplo, você pode exibir uma imagem que é repetida em cada item. Para obter mais informações, consulte [como: exibir controles não associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md).  
  
### <a name="events"></a>Eventos  
 Os eventos mais importantes para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle são o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>evento, que é disparado quando novos itens são colocados na exibição, e o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged>evento, que é disparado quando um item é selecionado.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Você pode usar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>evento para alterar a aparência do item.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> Por exemplo, você pode realçar valores negativos. Use o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged>evento para acessar os valores dos controles quando um item é selecionado.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged>  
  
 O <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle expõe todos os eventos de controle padrão no Editor de códigos.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> No entanto, alguns dos eventos não devem ser usado. Teclado e mouse eventos como `KeyDown`, `Click`, e `MouseDown` não serão gerados em tempo de execução porque o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle em si nunca tem foco.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
 O <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>não expõe eventos em tempo de design porque ele é criado apenas em tempo de execução.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> Se você quiser manipular eventos de teclado e mouse, você pode adicionar uma <xref:System.Windows.Forms.Panel>o controle para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>em tempo de design e, em seguida, manipular os eventos para <xref:System.Windows.Forms.Panel>.</xref:System.Windows.Forms.Panel> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> </xref:System.Windows.Forms.Panel> Para obter mais informações, consulte [Solucionando problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md).  
  
### <a name="customizations"></a>Personalizações  
 Há muitas maneiras de personalizar a aparência e comportamento do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controlar, tanto em tempo de execução e em tempo de design.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Propriedades podem ser definidas para alterar cores, ocultar ou alterar os cabeçalhos de item, alterar a orientação de vertical para horizontal e muito mais. Para obter mais informações, consulte [como: alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md), [como: exibir cabeçalhos de Item em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md), e [como: alterar o Layout de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md).  
  
 Observe que algumas propriedades se aplicam para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>próprio controle enquanto outros se aplicam somente a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Certifique-se de que você tem a seção correta do controle selecionado antes de definir propriedades. Para obter mais informações, consulte [como: alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md).  
  
 Outras personalizações incluem controlar a capacidade de adicionar ou excluir registros, adicionando recursos de pesquisa e exibir dados relacionados em um formato mestre e de detalhes. Para obter mais informações, consulte [como: desabilitar a adição e exclusão de itens DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md), [como: dados de pesquisa em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md), e [como: criar um formulário mestre/detalhes usando dois controles de DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md).  
  
## <a name="see-also"></a>Consulte também  
 [Controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/datarepeater-control-visual-studio.md)   
 [Passo a passo: Exibindo dados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio.md)   
 [Solução de problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
