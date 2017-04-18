---
title: "Como: desabilitar a adição e exclusão de itens DataRepeater (Visual Studio) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- DataRepeater, disabling delete
- DataRepeater, disabling add
ms.assetid: 298d8f60-ddfe-4361-ab66-cf76d0df5220
caps.latest.revision: 9
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
ms.openlocfilehash: 404e4dcc2f7d5cf7c92f8183f7437338312501f8
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-disable-adding-and-deleting-datarepeater-items-visual-studio"></a>Como desabilitar a adição e a exclusão de itens DataRepeater (Visual Studio)
Por padrão, os usuários podem adicionar e excluir itens em uma <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Os usuários podem adicionar um novo item, pressionando CTRL + N quando um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A>tem o foco ou clicando o **AddNewItem** botão o <xref:System.Windows.Forms.BindingNavigator>controle.</xref:System.Windows.Forms.BindingNavigator> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> Os usuários podem excluir um item pressionando DELETE quando uma <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A>tem o foco ou clicando o **DeleteItem** botão o <xref:System.Windows.Forms.BindingNavigator>controle.</xref:System.Windows.Forms.BindingNavigator> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A>  
  
 Você pode desabilitar a adição de e/ou exclusão em tempo de design ou em tempo de execução.  
  
### <a name="to-disable-adding-and-deleting-at-design-time"></a>Para desabilitar a adição e exclusão no tempo de design  
  
1.  No Windows Forms Designer, selecione o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
    > [!NOTE]
    >  Você deve selecionar a seção inferior do controle. Se você selecionar a seção de modelos de item, um conjunto diferente de propriedades será exibido.  
  
2.  Na janela Propriedades, defina o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToAddItems%2A>propriedade **False**.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToAddItems%2A>  
  
3.  Definir o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToDeleteItems%2A>propriedade **False**.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToDeleteItems%2A>  
  
4.  No Windows Forms Designer, selecione o <xref:System.Windows.Forms.BindingNavigator>de controle e, em seguida, clique no **AddNewItem** botão (o botão com um sinal de adição nele).</xref:System.Windows.Forms.BindingNavigator>  
  
5.  Na janela Propriedades, defina o <xref:System.Windows.Forms.ToolBarButton.Enabled%2A>propriedade **False**.</xref:System.Windows.Forms.ToolBarButton.Enabled%2A>  
  
6.  No Windows Forms Designer, selecione o <xref:System.Windows.Forms.BindingNavigator>de controle e, em seguida, clique no **DeleteItem** botão (o botão com um X vermelho).</xref:System.Windows.Forms.BindingNavigator>  
  
7.  Na janela Propriedades, defina o <xref:System.Windows.Forms.ToolBarButton.Enabled%2A>propriedade **False**.</xref:System.Windows.Forms.ToolBarButton.Enabled%2A>  
  
8.  Na bandeja do componente, selecione o <xref:System.Windows.Forms.BindingSource>ao qual o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>associado.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> </xref:System.Windows.Forms.BindingSource>  
  
9. Na janela Propriedades, defina o <xref:System.Windows.Forms.BindingSource.AllowNew%2A>propriedade **False**.</xref:System.Windows.Forms.BindingSource.AllowNew%2A>  
  
10. No Windows Forms Designer, clique duas vezes o **DeleteItem** botão para abrir o Editor de código.  
  
11. Na lista suspensa de eventos, selecione o `BindingNavigatorDeleteItem_EnabledChanged` evento.  
  
12. Adicione o seguinte código ao manipulador de eventos do `BindingNavigatorDeleteItem_EnabledChanged`:  
  
     [!code-cs[&#1; VbPowerPacksDataRepeaterDisableAddDelete](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterDisableAddDelete n º&1;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  Essa etapa é necessária porque o <xref:System.Windows.Forms.BindingSource>permitirá que o **DeleteItem** botão toda vez que o registro atual é alterado.</xref:System.Windows.Forms.BindingSource>  
  
### <a name="to-disable-adding-and-deleting-at-run-time"></a>Para desabilitar a adição e exclusão de tempo de execução  
  
1.  No Windows Forms Designer, clique duas vezes no formulário para abrir o Editor de códigos.  
  
2.  Adicione o seguinte código para o `Form_Load` evento:  
  
     [!code-cs[N º&2; VbPowerPacksDataRepeaterDisableAddDelete](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterDisableAddDelete n º&2;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.vb)]  
  
3.  Adicione o seguinte código ao manipulador de eventos do `BindingNavigatorDeleteItem_EnabledChanged`:  
  
     [!code-cs[&#1; VbPowerPacksDataRepeaterDisableAddDelete](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterDisableAddDelete n º&1;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  Essa etapa é necessária porque o <xref:System.Windows.Forms.BindingSource>permitirá que o **DeleteItem** botão toda vez que o registro atual é alterado.</xref:System.Windows.Forms.BindingSource>  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 [Introdução ao controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [Solução de problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
