---
title: 'Como: Adicionar Recursos de Pesquisa a um Controle ListView'
ms.date: 03/30/2017
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
ms.openlocfilehash: d5d4dae55fc9f0613ab6535b2fe57e262d0ef141
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59314016"
---
# <a name="how-to-add-search-capabilities-to-a-listview-control"></a>Como: Adicionar Recursos de Pesquisa a um Controle ListView
Muitas vezes, ao trabalhar com uma grande lista de itens em um <xref:System.Windows.Forms.ListView> controle, que você deseja oferecer recursos de pesquisa para o usuário. O <xref:System.Windows.Forms.ListView> controle oferece essa funcionalidade de duas maneiras diferentes: correspondência de texto e pesquisa de localização.  
  
 O <xref:System.Windows.Forms.ListView.FindItemWithText%2A> método permite que você execute uma pesquisa de texto em um <xref:System.Windows.Forms.ListView> na exibição de lista ou detalhes, dada uma cadeia de caracteres de pesquisa e um opcional Iniciando e encerrando o índice. Em contraste, o <xref:System.Windows.Forms.ListView.FindNearestItem%2A> método permite que você encontre um item em um <xref:System.Windows.Forms.ListView> no modo de exibição de ícone ou bloco, dado um conjunto de coordenadas x e y e uma direção de pesquisa.  
  
### <a name="to-find-an-item-using-text"></a>Localizar um item usando texto  
  
1. Criar uma <xref:System.Windows.Forms.ListView> com o <xref:System.Windows.Forms.ListView.View%2A> propriedade definida como <xref:System.Windows.Forms.View.Details> ou <xref:System.Windows.Forms.View.List>e, em seguida, preencha o <xref:System.Windows.Forms.ListView> com itens.  
  
2. Chamar o <xref:System.Windows.Forms.ListView.FindItemWithText%2A> método, passando o texto do item que você deseja localizar.  
  
3. O exemplo de código a seguir demonstra como criar um basic <xref:System.Windows.Forms.ListView>, preenchê-lo com itens e usar a entrada de texto do usuário para localizar um item na lista.  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#1)]  
  
### <a name="to-find-an-item-using-x--and-y-coordinates"></a>Localizar um item usando coordenadas x e y  
  
1. Criar uma <xref:System.Windows.Forms.ListView> com o <xref:System.Windows.Forms.View> propriedade definida como <xref:System.Windows.Forms.View.SmallIcon> ou <xref:System.Windows.Forms.View.LargeIcon>e, em seguida, preencha o <xref:System.Windows.Forms.ListView> com itens.  
  
2. Chamar o <xref:System.Windows.Forms.ListView.FindNearestItem%2A> método, passando a desejado coordenadas x e y- e a direção em que você deseja pesquisar.  
  
3. O exemplo de código a seguir demonstra como criar um ícone básico <xref:System.Windows.Forms.ListView>, preenchê-lo com itens e capture o <xref:System.Windows.Forms.Control.MouseDown> evento para encontrar o item mais próximo na direção para cima.  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#2](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#2)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#2)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#2)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.FindItemWithText%2A>
- <xref:System.Windows.Forms.ListView.FindNearestItem%2A>
- [Controle ListView](listview-control-windows-forms.md)
- [Visão geral do controle ListView](listview-control-overview-windows-forms.md)
- [Como: Adicionar e remover itens com o controle ListView do Windows Forms](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
