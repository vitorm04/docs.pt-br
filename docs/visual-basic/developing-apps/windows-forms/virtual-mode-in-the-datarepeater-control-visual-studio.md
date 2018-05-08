---
title: Modo virtual no controle DataRepeater (Visual Studio)
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- virtual data binding [Visual Basic]
- DataRepeater
- DataRepeater, virtual mode
ms.assetid: 5fb805dc-2d8b-4139-b1e3-86e4c2667221
ms.openlocfilehash: 7aa462f670c95f2d5996cf04b676bf09e9ec62b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="virtual-mode-in-the-datarepeater-control-visual-studio"></a>Modo virtual no controle DataRepeater (Visual Studio)
Quando você deseja exibir grandes quantidades de dados tabulares em uma <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle, você pode melhorar o desempenho, definindo o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> propriedade para `True` e gerenciar explicitamente a interação do controle com sua fonte de dados. O <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle fornece vários eventos que você pode manipular para interagir com sua fonte de dados e exibir os dados necessários em tempo de execução.  
  
## <a name="how-virtual-mode-works"></a>Como Virtual funciona de modo  
 O cenário mais comum para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle é associar os controles filho do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> para dados de um fonte em tempo de design e permitir que o <xref:System.Windows.Forms.BindingSource> para passar dados e para trás conforme necessário. Quando você usa o modo virtual, os controles não associados a uma fonte de dados e dados são passados e voltar para a fonte de dados subjacente em tempo de execução.  
  
 Quando o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> está definida como `True`, criar a interface do usuário, adicionando controles a partir o **caixa de ferramentas** em vez de adicionar controles associados do **fontes de dados** janela.  
  
 Os eventos são gerados em uma base por um controle, e você deve adicionar código para lidar com a exibição de dados. Quando um novo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> é colocada na exibição de <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> é gerado uma vez para cada controle e você deve fornecer os valores para cada controle no <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> manipulador de eventos.  
  
 Se os dados em um dos controles são alterados pelo usuário, o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> é gerado e você deve validar os dados e salvá-lo em sua fonte de dados.  
  
 Se o usuário adiciona um novo item, o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded> é gerado. Use esse manipulador para criar um novo registro na fonte de dados. Para evitar alterações não intencionais, você também deve monitorar o <xref:System.Windows.Forms.Control.KeyDown> eventos para cada controle e chamada <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A> se o usuário pressionar a tecla ESC.  
  
 Se as alterações de fonte de dados, você poderá atualizar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle chamando o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> e <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> métodos. Ambos os métodos devem ser chamados em ordem.  
  
 Por fim, você deve implementar manipuladores de eventos para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved> evento que ocorre quando um item é excluído e, opcionalmente, para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletingItems> e <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletedItems> eventos que ocorrem quando um usuário exclui um item, pressionando a tecla DELETE.  
  
## <a name="implementing-virtual-mode"></a>Implementando o modo Virtual  
 A seguir estão as etapas necessárias para implementar o modo virtual.  
  
#### <a name="to-implement-virtual-mode"></a>Para implementar o modo virtual  
  
1.  Arraste um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controlar do **Visual Basic PowerPacks** guia o **caixa de ferramentas** a um controle de formulário ou contêiner. Defina a propriedade <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> como `True`.  
  
2.  Arraste os controles do **caixa de ferramentas** para a região de modelo de item (região superior) do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle. Você precisará de um controle para cada campo na fonte de dados que você deseja exibir.  
  
3.  Implementar um manipulador para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> evento para fornecer valores para cada controle. Esse evento é gerado quando um novo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> rolado para a exibição. O código será parecida com o exemplo a seguir, que é para uma fonte de dados denominada `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_1.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_1.cs)]  
  
4.  Implementar um manipulador para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> evento para armazenar os dados. Esse evento é gerado quando o usuário confirma as alterações para um controle filho de <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>. O código será parecida com o exemplo a seguir, que é para uma fonte de dados denominada `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_2.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_2.cs)]  
  
5.  Implementar um manipulador para cada controle filho <xref:System.Windows.Forms.Control.KeyDown> eventos e monitorar a tecla ESC. Chamar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A> método para impedir que o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> evento seja gerado. O código será parecida com o exemplo a seguir.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_3.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_3.cs)]  
  
6.  Implementar um manipulador para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded> evento. Esse evento é gerado quando o usuário adiciona um novo item para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle. O código será parecida com o exemplo a seguir, que é para uma fonte de dados denominada `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_4.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_4.cs)]  
  
7.  Implementar um manipulador para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved> evento. Esse evento ocorre quando um usuário exclui um item existente. O código será parecida com o exemplo a seguir, que é para uma fonte de dados denominada `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_5.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_5.cs)]  
  
8.  Para validação de nível de controle, a opção de implementar manipuladores para o <xref:System.Windows.Forms.Control.Validating> eventos dos controles filho. O código será parecida com o exemplo a seguir.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#6](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_6.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#6](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_6.cs)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>  
 [Introdução ao Controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
