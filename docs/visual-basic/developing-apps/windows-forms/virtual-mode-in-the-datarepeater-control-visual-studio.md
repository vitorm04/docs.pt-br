---
title: Modo virtual no controle DataRepeater (Visual Studio) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- virtual data binding
- DataRepeater
- DataRepeater, virtual mode
ms.assetid: 5fb805dc-2d8b-4139-b1e3-86e4c2667221
caps.latest.revision: 13
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
ms.openlocfilehash: 85f7e250c57a507e891eb30756c0550098cce9e0
ms.lasthandoff: 03/13/2017

---
# <a name="virtual-mode-in-the-datarepeater-control-visual-studio"></a>Modo virtual no controle DataRepeater (Visual Studio)
Quando você deseja exibir grandes quantidades de dados tabulares em uma <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle, você pode melhorar o desempenho, definindo o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>propriedade `True` e gerenciar explicitamente a interação do controle com sua fonte de dados.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> O <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle fornece vários eventos que você pode manipular para interagir com a fonte de dados e exibir os dados conforme necessário no tempo de execução.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
## <a name="how-virtual-mode-works"></a>Como Virtual funciona de modo  
 O cenário mais comum para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle deve ligar os controles filho do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>para dados de origem em tempo de design e permitir que o <xref:System.Windows.Forms.BindingSource>para passar dados e volta conforme necessário.</xref:System.Windows.Forms.BindingSource> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Quando você usa o modo virtual, os controles não associados a uma fonte de dados e dados são passados e voltar para a fonte de dados em tempo de execução.  
  
 Quando o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>estiver definida como `True`, criar a interface do usuário adicionando controles a partir o **ferramentas** em vez de adicionar controles associados do **fontes de dados** janela.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>  
  
 Eventos são gerados em uma base por controle, e você deve adicionar o código para manipular a exibição de dados. Quando um novo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>é colocada na exibição de <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>é gerado uma vez para cada controle e você deve fornecer os valores para cada controle o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>manipulador de eventos.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>  
  
 Se um dos controles de dados for alterados pelo usuário, o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>é gerado e você deve validar os dados e salvá-lo em sua fonte de dados.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>  
  
 Se o usuário adiciona um novo item, o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded>é gerado.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded> Use o manipulador deste evento para criar um novo registro na fonte de dados. Para evitar alterações indesejadas, você também deve monitorar o <xref:System.Windows.Forms.Control.KeyDown>evento para cada controle e chamada <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A>se o usuário pressionar a tecla ESC.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A> </xref:System.Windows.Forms.Control.KeyDown>  
  
 Se as alterações de fonte de dados, você poderá atualizar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle chamando o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A>e <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A>métodos.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Ambos os métodos devem ser chamados na ordem.  
  
 Por fim, você deve implementar manipuladores de eventos para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved>evento que ocorre quando um item é excluído e, opcionalmente, para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletingItems>e <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletedItems>eventos que ocorrem sempre que um usuário exclui um item pressionando a tecla DELETE.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletedItems> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletingItems> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved>  
  
## <a name="implementing-virtual-mode"></a>Implementando o modo Virtual  
 A seguir estão as etapas necessárias para implementar o modo virtual.  
  
#### <a name="to-implement-virtual-mode"></a>Para implementar o modo virtual  
  
1.  Arraste um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>de controle do **Visual Basic PowerPacks** guia o **Toolbox** a um controle de formulário ou contêiner.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Definir o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>propriedade `True`.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>  
  
2.  Arraste os controles do **Toolbox** para a região de modelo de item (região superior) do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Você precisará de um controle para cada campo na fonte de dados que você deseja exibir.  
  
3.  Implemente um manipulador para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>evento para fornecer valores para cada controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> Esse evento é gerado quando um novo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>é colocada na exibição.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> O código será parecida com o exemplo a seguir, que é uma fonte de dados chamada `Employees`.  
  
     [!code-vb[&#1; VbPowerPacksDataRepeaterVirtualMode](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_1.vb) ] 
     [!code-cs [VbPowerPacksDataRepeaterVirtualMode n º&1;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_1.cs)]  
  
4.  Implemente um manipulador para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>evento para armazenar os dados.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> Esse evento é gerado quando o usuário confirma as alterações para um controle filho de <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> O código será parecida com o exemplo a seguir, que é uma fonte de dados chamada `Employees`.  
  
     [!code-vb[N º&2; VbPowerPacksDataRepeaterVirtualMode](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_2.vb) ] 
     [!code-cs [VbPowerPacksDataRepeaterVirtualMode n º&2;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_2.cs)]  
  
5.  Implemente um manipulador para cada controle filho <xref:System.Windows.Forms.Control.KeyDown>eventos e monitorar a tecla ESC.</xref:System.Windows.Forms.Control.KeyDown> Chamar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A>método para impedir que o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>evento seja gerado.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A> O código será parecida com o exemplo a seguir.  
  
     [!code-vb[N º&3; VbPowerPacksDataRepeaterVirtualMode](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_3.vb) ] 
     [!code-cs [VbPowerPacksDataRepeaterVirtualMode n º&3;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_3.cs)]  
  
6.  Implemente um manipulador para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded>evento.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded> Esse evento é gerado quando o usuário adiciona um novo item para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> O código será parecida com o exemplo a seguir, que é uma fonte de dados chamada `Employees`.  
  
     [!code-vb[N º&4; VbPowerPacksDataRepeaterVirtualMode](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_4.vb) ] 
     [!code-cs [VbPowerPacksDataRepeaterVirtualMode n º&4;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_4.cs)]  
  
7.  Implemente um manipulador para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved>evento.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved> Esse evento ocorre quando um usuário exclui um item existente. O código será parecida com o exemplo a seguir, que é uma fonte de dados chamada `Employees`.  
  
     [!code-vb[N º&5; VbPowerPacksDataRepeaterVirtualMode](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_5.vb) ] 
     [!code-cs [VbPowerPacksDataRepeaterVirtualMode n º&5;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_5.cs)]  
  
8.  Para validação de nível de controle, opcionalmente, implementar manipuladores para o <xref:System.Windows.Forms.Control.Validating>eventos dos controles filho.</xref:System.Windows.Forms.Control.Validating> O código será parecida com o exemplo a seguir.  
  
     [!code-vb[N º&6; VbPowerPacksDataRepeaterVirtualMode](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_6.vb) ] 
     [!code-cs [VbPowerPacksDataRepeaterVirtualMode n º&6;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_6.cs)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>   
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded>   
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>   
 [Introdução ao Controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
