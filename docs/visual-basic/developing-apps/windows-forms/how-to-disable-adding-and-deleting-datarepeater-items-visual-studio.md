---
title: "Como desabilitar a adi&#231;&#227;o e a exclus&#227;o de itens DataRepeater (Visual Studio) | Microsoft Docs"
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
  - "DataRepeater, desabilitando adição"
  - "DataRepeater, desabilitando exclusão"
ms.assetid: 298d8f60-ddfe-4361-ab66-cf76d0df5220
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como desabilitar a adi&#231;&#227;o e a exclus&#227;o de itens DataRepeater (Visual Studio)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Por padrão, os usuários podem adicionar e excluir itens em um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  Os usuários podem adicionar um novo item pressionando CTRL \+ N quando um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> tem foco ou clicando o  **AddNewItem** na barra de <xref:System.Windows.Forms.BindingNavigator> controle.  Os usuários podem excluir um item pressionando excluir quando um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> tem foco ou clicando o  **DeleteItem** na barra do <xref:System.Windows.Forms.BindingNavigator> controle.  
  
 Você pode desativar a adicionar e\/ou excluindo em tempo de design ou em tempo de execução.  
  
### Para desativar a adição e exclusão em tempo de design  
  
1.  No Windows Forms Designer, selecione o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
    > [!NOTE]
    >  Você deve selecionar a seção inferior do controle.  Se você selecionar a seção de modelo de item, um conjunto diferente de propriedades será exibido.  
  
2.  Na janela Properties, defina a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToAddItems%2A> propriedade para  **False**.  
  
3.  Definir o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToDeleteItems%2A> propriedade para  **False**.  
  
4.  No Windows Forms Designer, selecione o <xref:System.Windows.Forms.BindingNavigator> controle e, em seguida, clique no  **AddNewItem** o botão \(o botão com um sinal de mais nele\).  
  
5.  Na janela Properties, defina a <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> propriedade para  **False**.  
  
6.  No Windows Forms Designer, selecione o <xref:System.Windows.Forms.BindingNavigator> controle e, em seguida, clique no  **DeleteItem** o botão \(o botão com um x vermelho sobre ele\).  
  
7.  Na janela Properties, defina a <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> propriedade para  **False**.  
  
8.  Na bandeja do componente, selecione o <xref:System.Windows.Forms.BindingSource> ao qual o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> está vinculado.  
  
9. Na janela Properties, defina a <xref:System.Windows.Forms.BindingSource.AllowNew%2A> propriedade para  **False**.  
  
10. No Windows Forms Designer, clique duas vezes o  **DeleteItem** o botão para abrir o Editor de código.  
  
11. Na lista drop\-down de eventos, selecione o `BindingNavigatorDeleteItem_EnabledChanged` evento.  
  
12. Adicione o seguinte código para o manipulador de eventos `BindingNavigatorDeleteItem_EnabledChanged`:  
  
     [!code-cs[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  Essa etapa é necessária porque a <xref:System.Windows.Forms.BindingSource> permitirá que o  **DeleteItem** botão toda vez que o registro atual é alterado.  
  
### Para desativar a adição e exclusão em tempo de execução  
  
1.  No Windows Forms Designer, clique duas vezes no formulário para abrir o Editor de código.  
  
2.  Adicione o seguinte código para o `Form_Load` evento:  
  
     [!code-cs[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.vb)]  
  
3.  Adicione o seguinte código para o manipulador de eventos `BindingNavigatorDeleteItem_EnabledChanged`:  
  
     [!code-cs[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  Essa etapa é necessária porque a <xref:System.Windows.Forms.BindingSource> permitirá que o  **DeleteItem** botão toda vez que o registro atual é alterado.  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 [Introdução ao controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [Solucionando problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)