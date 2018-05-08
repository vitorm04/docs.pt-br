---
title: Como desabilitar a adição e a exclusão de itens DataRepeater (Visual Studio)
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, disabling delete
- DataRepeater, disabling add
ms.assetid: 298d8f60-ddfe-4361-ab66-cf76d0df5220
ms.openlocfilehash: e3d0d2a8d422054e269ee92df1fdfcb5acb96eac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-disable-adding-and-deleting-datarepeater-items-visual-studio"></a>Como desabilitar a adição e a exclusão de itens DataRepeater (Visual Studio)
Por padrão, os usuários podem adicionar e excluir itens em um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle. Os usuários podem adicionar um novo item, pressionando CTRL + N quando um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> tem foco ou clicando o **AddNewItem** botão o <xref:System.Windows.Forms.BindingNavigator> controle. Os usuários podem excluir um item pressionando excluir quando um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> tem foco ou clicando o **DeleteItem** botão o <xref:System.Windows.Forms.BindingNavigator> controle.  
  
 Você pode desabilitar a adição de e/ou exclusão em tempo de design ou em tempo de execução.  
  
### <a name="to-disable-adding-and-deleting-at-design-time"></a>Para desabilitar a adição e exclusão no tempo de design  
  
1.  No Designer de Formulários do Windows, selecione o controle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
    > [!NOTE]
    >  Você deve selecionar a seção inferior do controle. Se você selecionar a seção do item de modelo, será exibido um conjunto diferente de propriedades.  
  
2.  Na janela Propriedades, defina o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToAddItems%2A> propriedade **False**.  
  
3.  Definir o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToDeleteItems%2A> propriedade **False**.  
  
4.  No Designer de formulários do Windows, selecione o <xref:System.Windows.Forms.BindingNavigator> de controle e, em seguida, clique no **AddNewItem** botão (o botão com um sinal de adição nele).  
  
5.  Na janela Propriedades, defina o <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> propriedade **False**.  
  
6.  No Designer de formulários do Windows, selecione o <xref:System.Windows.Forms.BindingNavigator> de controle e, em seguida, clique no **DeleteItem** botão (o botão com um X vermelho).  
  
7.  Na janela Propriedades, defina o <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> propriedade **False**.  
  
8.  Na bandeja do componente, selecione o <xref:System.Windows.Forms.BindingSource> ao qual o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> está associado.  
  
9. Na janela Propriedades, defina o <xref:System.Windows.Forms.BindingSource.AllowNew%2A> propriedade **False**.  
  
10. No Designer de formulários do Windows, clique duas vezes o **DeleteItem** botão para abrir o Editor de código.  
  
11. Na lista suspensa de eventos, selecione o `BindingNavigatorDeleteItem_EnabledChanged` evento.  
  
12. Adicione o seguinte código ao manipulador de eventos do `BindingNavigatorDeleteItem_EnabledChanged`:  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  Essa etapa é necessária porque o <xref:System.Windows.Forms.BindingSource> habilitará o **DeleteItem** botão toda vez que o registro atual é alterado.  
  
### <a name="to-disable-adding-and-deleting-at-run-time"></a>Para desabilitar a adição e exclusão em tempo de execução  
  
1.  No Designer de formulários do Windows, clique duas vezes no formulário para abrir o Editor de códigos.  
  
2.  Adicione o seguinte código para o `Form_Load` evento:  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.vb)]  
  
3.  Adicione o seguinte código ao manipulador de eventos do `BindingNavigatorDeleteItem_EnabledChanged`:  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  Essa etapa é necessária porque o <xref:System.Windows.Forms.BindingSource> habilitará o **DeleteItem** botão toda vez que o registro atual é alterado.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [Introdução ao Controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Solução de problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
