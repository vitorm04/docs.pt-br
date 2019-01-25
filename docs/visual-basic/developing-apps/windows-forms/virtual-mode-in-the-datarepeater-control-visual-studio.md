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
ms.openlocfilehash: 3988c16746606de9f20f9a66b87539b6cea04758
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700800"
---
# <a name="virtual-mode-in-the-datarepeater-control-visual-studio"></a>Modo virtual no controle DataRepeater (Visual Studio)
Quando quiser exibir grandes quantidades de dados tabulares em um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle, você pode melhorar o desempenho, definindo o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> propriedade `True` e gerenciar explicitamente a interação do controle com sua fonte de dados. O <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle fornece vários eventos que você pode manipular para interagir com sua fonte de dados e exibir os dados conforme necessário no tempo de execução.  
  
## <a name="how-virtual-mode-works"></a>Como Virtual funciona de modo  
 O cenário mais comum para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> é associar os controles filho do controle a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> aos dados de um fonte em tempo de design e permitir que o <xref:System.Windows.Forms.BindingSource> para passar dados e para trás, conforme necessário. Quando você usa o modo virtual, os controles não associados a uma fonte de dados e dados são passados e voltar para a fonte de dados subjacente em tempo de execução.  
  
 Quando o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> estiver definida como `True`, você cria a interface do usuário adicionando controles da **caixa de ferramentas** em vez de adicionar controles associados da **fontes de dados** janela.  
  
 Eventos são gerados em uma base de controle por controle, e você deve adicionar código para lidar com a exibição de dados. Quando um novo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> for colocado na exibição, o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> é gerado uma vez para cada controle e você deve fornecer os valores para cada controle no <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> manipulador de eventos.  
  
 Se os dados em um dos controles são alterados pelo usuário, o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> é gerado e você deve validar os dados e salvá-lo em sua fonte de dados.  
  
 Se o usuário adiciona um novo item, o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded> é gerado. Use o manipulador deste evento para criar um novo registro na fonte de dados. Para evitar alterações indesejadas, você também deve monitorar o <xref:System.Windows.Forms.Control.KeyDown> evento para cada controle e a chamada <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A> se o usuário pressiona a tecla ESC.  
  
 Se as alterações de fonte de dados, você poderá atualizar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle chamando o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> e <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> métodos. Ambos os métodos devem ser chamados na ordem.  
  
 Por fim, você deve implementar manipuladores de eventos para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved> evento que ocorre quando um item é excluído e, opcionalmente, para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletingItems> e <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletedItems> eventos que ocorrem sempre que um usuário exclui um item, pressionando a tecla DELETE.  
  
## <a name="implementing-virtual-mode"></a>Implementando o modo Virtual  
 A seguir estão as etapas necessárias para implementar o modo virtual.  
  
#### <a name="to-implement-virtual-mode"></a>Para implementar o modo virtual  
  
1.  Arraste uma <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controlar do **Visual Basic PowerPacks** guia o **caixa de ferramentas** a um controle de formulário ou contêiner. Defina a propriedade <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> como `True`.  
  
2.  Arraste os controles do **caixa de ferramentas** para a região de modelo de item (região superior) do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle. Você precisará de um controle para cada campo na fonte de dados que você deseja exibir.  
  
3.  Implemente um manipulador para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> eventos para fornecer valores para cada controle. Esse evento é gerado quando um novo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> for colocado na exibição. O código será parecida com o exemplo a seguir, que é uma fonte de dados denominada `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_1.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_1.cs)]  
  
4.  Implemente um manipulador para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> evento para armazenar os dados. Esse evento é gerado quando o usuário confirma alterações em um controle filho a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>. O código será parecida com o exemplo a seguir, que é uma fonte de dados denominada `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_2.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_2.cs)]  
  
5.  Implemente um manipulador para cada controle de filho <xref:System.Windows.Forms.Control.KeyDown> eventos e monitorar a tecla ESC. Chame o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A> método para impedir que o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> evento seja gerado. O código será semelhante ao exemplo a seguir.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_3.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_3.cs)]  
  
6.  Implemente um manipulador para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded> eventos. Esse evento é gerado quando o usuário adiciona um novo item para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle. O código será parecida com o exemplo a seguir, que é uma fonte de dados denominada `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_4.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_4.cs)]  
  
7.  Implemente um manipulador para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved> eventos. Esse evento ocorre quando um usuário exclui um item existente. O código será parecida com o exemplo a seguir, que é uma fonte de dados denominada `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_5.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_5.cs)]  
  
8.  Para validação de nível de controle, opcionalmente, implementar manipuladores para o <xref:System.Windows.Forms.Control.Validating> eventos dos controles filho. O código será semelhante ao exemplo a seguir.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#6](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_6.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#6](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_6.cs)]  
  
## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>
- [Introdução ao Controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
