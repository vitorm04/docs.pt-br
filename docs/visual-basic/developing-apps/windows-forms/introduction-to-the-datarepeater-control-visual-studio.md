---
title: "Introdu&#231;&#227;o ao controle DataRepeater (Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "DataRepeater"
  - "DataRepeater, visão geral"
  - "repetindo dados"
ms.assetid: 78a52a1d-65f0-4ecb-97ff-53bc114300c5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Introdu&#231;&#227;o ao controle DataRepeater (Visual Studio)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Os pacotes de energia de Visual Basic <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle é um contêiner rolável repetido de controles que exibem dados, por exemplo, linhas em uma tabela de banco de dados.  Ele pode ser usado como uma alternativa para o <xref:System.Windows.Forms.DataGridView> controlar quando você precisar de mais controle sobre o layout dos dados.  O <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> "repete" de um grupo de controles relacionados, criando várias instâncias em um modo de exibição de rolagem.  Isso permite aos usuários exibir vários registros ao mesmo tempo.  
  
## Visão Geral  
 Em tempo de design, o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> o controle consiste em duas seções.  A seção externa é o  *visor*, onde os dados de rolagem serão exibidos em tempo de execução.  A seção interna de \(superior\), conhecida como o  *modelo de item*, é onde posicionar os controles que serão repetidos em tempo de execução, normalmente um controle para cada campo na fonte de dados.  As propriedades e os controles no modelo de item são encapsuladas na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> propriedade.  
  
 Em tempo de execução, o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> é copiado para uma virtual <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> objeto que é usado para exibir os dados quando cada registro é colocado na exibição.  Você pode personalizar a exibição de registros individuais na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> evento, por exemplo, realce um campo com base no valor que ele contém.  Para obter mais informações, consulte [Como alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md).  
  
 O uso mais comum para um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> é de controle exibir dados de uma tabela de banco de dados ou outra fonte de dados ligada.  Além [!INCLUDE[vstecado](../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)] objetos de dados, o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle pode vincular qualquer classe que implementa o <xref:System.Collections.IList> interface \(inclusive arrays\), qualquer classe que implementa o <xref:System.ComponentModel.IListSource> interface, qualquer classe que implementa o <xref:System.ComponentModel.IBindingList> interface ou qualquer classe que implementa o <xref:System.ComponentModel.IBindingListView> interface.  
  
### Ligação de Dados  
 Em geral, realizar a ligação de dados arrastando campos da  **Fontes de dados** janela para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  Para obter mais informações, consulte [Como exibir dados associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).  
  
 Ao trabalhar com grandes quantidades de dados, você pode definir a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> propriedade para `True` para exibir um subconjunto dos dados disponíveis.  Modo virtual requer a implementação de um cache de dados a partir do qual o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> estiver preenchido, e você deve controlar todas as interações com o cache de dados em tempo de execução.  Para obter mais informações, consulte [Modo virtual no controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md).  
  
 Você também pode exibir controles não acoplados em um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  Por exemplo, você pode exibir uma imagem que é repetida em cada item.  Para obter mais informações, consulte [Como exibir controles não associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md).  
  
### Eventos  
 Os eventos mais importantes para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle são o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> evento, que é disparado quando novos itens são colocados na exibição, e o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged> o evento, que é disparado quando um item é selecionado.  Você pode usar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> evento para alterar a aparência do item.  Por exemplo, você pode realçar os valores negativos.  Use o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged> evento para acessar os valores dos controles quando um item é selecionado.  
  
 O <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle expõe todos os eventos de controle padrão no Editor de código.  No entanto, alguns eventos não devem ser usado.  Teclado e eventos de mouse, como `KeyDown`, `Click`, e `MouseDown` não serão gerados em tempo de execução porque a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> nunca, o próprio controle tem foco.  
  
 O <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> não expõe eventos em tempo de design porque ele é criado somente em tempo de execução.  Se você deseja manipular eventos de teclado e mouse, você pode adicionar um <xref:System.Windows.Forms.Panel> o controle para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> em tempo de design e, em seguida, manipular os eventos para o <xref:System.Windows.Forms.Panel>.  Para obter mais informações, consulte [Solucionando problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md).  
  
### Personalizações  
 Há várias maneiras para personalizar a aparência e comportamento da <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controlar, tanto em tempo de execução em tempo de design.  Propriedades podem ser definidas para alterar as cores, ocultar ou modificar os cabeçalhos de item, alterar a orientação de vertical para horizontal e muito mais.  Para obter mais informações, consulte [Como alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md),  [Como exibir cabeçalhos de item em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md) e [Como alterar o layout de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md).  
  
 Observe que algumas propriedades se aplicam para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle próprio, enquanto outros se apliquem somente ao <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>.  Certifique\-se de que você tenha a seção correta do controle selecionado antes de definir propriedades.  Para obter mais informações, consulte [Como alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md).  
  
 Outras personalizações incluem controlar a capacidade de adicionar ou excluir registros, adicionando recursos de pesquisa e exibir dados relacionados em um formato de mestre e detalhadas.  Para obter mais informações, consulte [Como desabilitar a adição e a exclusão de itens DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md),  [Como pesquisar dados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md) e [Como criar um formulário mestre\/detalhado usando dois controles DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md).  
  
## Consulte também  
 [Controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/datarepeater-control-visual-studio.md)   
 [Instruções passo a passo: exibindo dados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio.md)   
 [Solucionando problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)