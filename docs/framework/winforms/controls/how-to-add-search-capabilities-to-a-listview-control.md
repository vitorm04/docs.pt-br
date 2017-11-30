---
title: Como adicionar recursos de pesquisa a um controle ListView
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- lists [Windows Forms], enabling searching
- list views [Windows Forms], enabling searching
- ListView control [Windows Forms], adding search capabilities
- searching [Windows Forms], adding search capabilities to ListView control
ms.assetid: 557782d9-b705-4bab-b496-9938afddac82
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fd6c3011b234f9d281a68a51fa8d9ef9d610816c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-search-capabilities-to-a-listview-control"></a>Como adicionar recursos de pesquisa a um controle ListView
Muitas vezes, ao trabalhar com uma grande lista de itens em uma <xref:System.Windows.Forms.ListView> controle, que você quer oferecer recursos de pesquisa para o usuário. O <xref:System.Windows.Forms.ListView> controle oferece esse recurso de duas maneiras diferentes: correspondência de texto e pesquisa de localidade.  
  
 O <xref:System.Windows.Forms.ListView.FindItemWithText%2A> método permite que você executar uma pesquisa de texto em uma <xref:System.Windows.Forms.ListView> na exibição de lista ou detalhes, recebe uma cadeia de caracteres de pesquisa e um opcional começando e terminando o índice. Em contraste, o <xref:System.Windows.Forms.ListView.FindNearestItem%2A> método permite que você encontre um item em uma <xref:System.Windows.Forms.ListView> no modo de exibição de ícone ou lado a lado, dado um conjunto de coordenadas x e y e uma direção de pesquisa.  
  
### <a name="to-find-an-item-using-text"></a>Localizar um item usando texto  
  
1.  Criar um <xref:System.Windows.Forms.ListView> com o <xref:System.Windows.Forms.ListView.View%2A> propriedade definida como <xref:System.Windows.Forms.View.Details> ou <xref:System.Windows.Forms.View.List>e, em seguida, preencha o <xref:System.Windows.Forms.ListView> com itens.  
  
2.  Chamar o <xref:System.Windows.Forms.ListView.FindItemWithText%2A> método, passando o texto do item que você deseja localizar.  
  
3.  O exemplo de código a seguir demonstra como criar um basic <xref:System.Windows.Forms.ListView>, preenchê-lo com os itens e usar a entrada de texto do usuário para localizar um item na lista.  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#1)]  
  
### <a name="to-find-an-item-using-x--and-y-coordinates"></a>Localizar um item usando coordenadas x e y  
  
1.  Criar um <xref:System.Windows.Forms.ListView> com o <xref:System.Windows.Forms.View> propriedade definida como <xref:System.Windows.Forms.View.SmallIcon> ou <xref:System.Windows.Forms.View.LargeIcon>e, em seguida, preencha o <xref:System.Windows.Forms.ListView> com itens.  
  
2.  Chamar o <xref:System.Windows.Forms.ListView.FindNearestItem%2A> método, passando a desejado e y-coordenadas x e a direção em que você deseja pesquisar.  
  
3.  O exemplo de código a seguir demonstra como criar um ícone básico <xref:System.Windows.Forms.ListView>, preenchê-lo com os itens e capture o <xref:System.Windows.Forms.Control.MouseDown> evento para encontrar o item mais próximo na direção se.  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#2)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#2)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.FindItemWithText%2A>  
 <xref:System.Windows.Forms.ListView.FindNearestItem%2A>  
 [Controle ListView](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [Visão geral do controle ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Como Adicionar e Remover Itens com o Controle ListView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
