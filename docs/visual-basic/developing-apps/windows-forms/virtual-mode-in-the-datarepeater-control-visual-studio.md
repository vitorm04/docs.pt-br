---
title: "Modo virtual no controle DataRepeater (Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "DataRepeater, modo virtual"
  - "associação de dados virtuais"
ms.assetid: 5fb805dc-2d8b-4139-b1e3-86e4c2667221
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Modo virtual no controle DataRepeater (Visual Studio)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Quando você deseja exibir grandes quantidades de dados tabulares em um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle, você pode melhorar o desempenho, definindo a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> propriedade para `True` e gerenciar explicitamente a interação do controle com sua fonte de dados.  O <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle fornece vários eventos que você pode manipular para interagir com sua fonte de dados e exibir os dados conforme necessário em tempo de execução.  
  
## Como as Virtual funciona de modo  
 A situação mais comum para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle está a ligar os controles filho do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> em um de dados em tempo de design de fonte e permitir que o <xref:System.Windows.Forms.BindingSource> para passar dados e para trás conforme necessário.  Quando você usa o modo virtual, os controles não estão ligados a uma fonte de dados e dados está indo e voltando à fonte de dados subjacente, em tempo de execução.  
  
 Quando o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> propriedade estiver definida como `True`, você criar a interface do usuário adicionando controles a partir do  **Toolbox** em vez de adicionar controles de limite da  **Fontes de dados** janela.  
  
 Eventos são gerados em uma base de controle, o controle, e você deve adicionar código para manipular a exibição de dados.  Quando um novo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> é colocada na exibição, o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> evento é gerado uma vez para cada controle e você deve fornecer os valores para cada controle no <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> manipulador de eventos.  
  
 Se os dados em um dos controles são alterados pelo usuário, o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> evento é gerado e você deve validar os dados e salvá\-lo em sua fonte de dados.  
  
 Se o usuário adiciona um novo item, o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded> evento é gerado.  Use o manipulador deste evento para criar um novo registro na fonte de dados.  Para evitar alterações indesejadas, você também deve monitorar o <xref:System.Windows.Forms.Control.KeyDown> evento para cada controle e a chamada <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A> se o usuário pressionar a tecla ESC.  
  
 Se as alterações de fonte de dados, você poderá atualizar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle chamando o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetTemplateItem%2A> e <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetTemplateItem%2A> métodos.  Ambos os métodos devem ser chamados na ordem.  
  
 Finalmente, você deve implementar manipuladores de eventos para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved> evento, que ocorre quando um item é excluído e, opcionalmente, para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletingItems> e <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletedItems> eventos, que ocorrem sempre que um usuário exclui um item pressionando a tecla DELETE.  
  
## Implementando o modo Virtual  
 A seguir estão as etapas necessárias para implementar o modo virtual.  
  
#### Para implementar o modo virtual  
  
1.  Arrastar um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controlar da  **Visual Basic PowerPacks** guia o  **caixa de ferramentas** a um controle de formulário ou recipiente.  Defina a propriedade <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> como `True`.  
  
2.  Arraste os controles a partir o  **caixa de ferramentas** até a região de modelo de item \(a região superior\) do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  Você precisará de um controle para cada campo na fonte de dados que você deseja exibir.  
  
3.  Implementar um manipulador para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> evento para fornecer valores para cada controle.  Este evento é gerado quando um novo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> é colocada na exibição.  O código parecerá com o exemplo a seguir, que é para uma fonte de dados denominada `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_1.vb)]
     [!code-cs[VbPowerPacksDataRepeaterVirtualMode#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_1.cs)]  
  
4.  Implementar um manipulador para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> evento para armazenar os dados.  Este evento é gerado quando o usuário confirma as alterações para um controle filho de <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.  O código parecerá com o exemplo a seguir, que é para uma fonte de dados denominada `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_2.vb)]
     [!code-cs[VbPowerPacksDataRepeaterVirtualMode#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_2.cs)]  
  
5.  Implementar um manipulador para do cada controle filho <xref:System.Windows.Forms.Control.KeyDown> de eventos e monitor a tecla ESC.  Chamar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A> método para impedir que o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> o evento de disparo.  O código parecerá com o exemplo a seguir.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_3.vb)]
     [!code-cs[VbPowerPacksDataRepeaterVirtualMode#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_3.cs)]  
  
6.  Implementar um manipulador para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded> evento.  Este evento é gerado quando o usuário adiciona um novo item para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  O código parecerá com o exemplo a seguir, que é para uma fonte de dados denominada `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_4.vb)]
     [!code-cs[VbPowerPacksDataRepeaterVirtualMode#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_4.cs)]  
  
7.  Implementar um manipulador para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved> evento.  Esse evento ocorre quando um usuário exclui um item existente.  O código parecerá com o exemplo a seguir, que é para uma fonte de dados denominada `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_5.vb)]
     [!code-cs[VbPowerPacksDataRepeaterVirtualMode#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_5.cs)]  
  
8.  Para validação de nível de controle, opcionalmente implemente manipuladores para o <xref:System.Windows.Forms.Control.Validating> eventos dos controles filho.  O código parecerá com o exemplo a seguir.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#6](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_6.vb)]
     [!code-cs[VbPowerPacksDataRepeaterVirtualMode#6](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_6.cs)]  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>   
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded>   
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>   
 [Introdução ao controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)