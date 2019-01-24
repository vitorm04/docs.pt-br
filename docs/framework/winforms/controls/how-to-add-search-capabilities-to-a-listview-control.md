---
title: 'Como: Adicionar recursos de pesquisa a um controle ListView'
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
ms.openlocfilehash: 0f8b9535539f7f9cd8d0c8ba3a362e9ab7bef03a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716785"
---
# <a name="how-to-add-search-capabilities-to-a-listview-control"></a><span data-ttu-id="f7834-102">Como: Adicionar recursos de pesquisa a um controle ListView</span><span class="sxs-lookup"><span data-stu-id="f7834-102">How to: Add Search Capabilities to a ListView Control</span></span>
<span data-ttu-id="f7834-103">Muitas vezes, ao trabalhar com uma grande lista de itens em um <xref:System.Windows.Forms.ListView> controle, que você deseja oferecer recursos de pesquisa para o usuário.</span><span class="sxs-lookup"><span data-stu-id="f7834-103">Oftentimes when working with a large list of items in a <xref:System.Windows.Forms.ListView> control, you want to offer search capabilities to the user.</span></span> <span data-ttu-id="f7834-104">O <xref:System.Windows.Forms.ListView> controle oferece essa funcionalidade de duas maneiras diferentes: correspondência de texto e pesquisa de localização.</span><span class="sxs-lookup"><span data-stu-id="f7834-104">The <xref:System.Windows.Forms.ListView> control offers this capability in two different ways: text matching and location searching.</span></span>  
  
 <span data-ttu-id="f7834-105">O <xref:System.Windows.Forms.ListView.FindItemWithText%2A> método permite que você execute uma pesquisa de texto em um <xref:System.Windows.Forms.ListView> na exibição de lista ou detalhes, dada uma cadeia de caracteres de pesquisa e um opcional Iniciando e encerrando o índice.</span><span class="sxs-lookup"><span data-stu-id="f7834-105">The <xref:System.Windows.Forms.ListView.FindItemWithText%2A> method allows you to perform a text search on a <xref:System.Windows.Forms.ListView> in list or details view, given a search string and an optional starting and ending index.</span></span> <span data-ttu-id="f7834-106">Em contraste, o <xref:System.Windows.Forms.ListView.FindNearestItem%2A> método permite que você encontre um item em um <xref:System.Windows.Forms.ListView> no modo de exibição de ícone ou bloco, dado um conjunto de coordenadas x e y e uma direção de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="f7834-106">In contrast, the <xref:System.Windows.Forms.ListView.FindNearestItem%2A> method allows you to find an item in a <xref:System.Windows.Forms.ListView> in icon or tile view, given a set of x- and y-coordinates and a direction to search.</span></span>  
  
### <a name="to-find-an-item-using-text"></a><span data-ttu-id="f7834-107">Localizar um item usando texto</span><span class="sxs-lookup"><span data-stu-id="f7834-107">To find an item using text</span></span>  
  
1.  <span data-ttu-id="f7834-108">Criar uma <xref:System.Windows.Forms.ListView> com o <xref:System.Windows.Forms.ListView.View%2A> propriedade definida como <xref:System.Windows.Forms.View.Details> ou <xref:System.Windows.Forms.View.List>e, em seguida, preencha o <xref:System.Windows.Forms.ListView> com itens.</span><span class="sxs-lookup"><span data-stu-id="f7834-108">Create a <xref:System.Windows.Forms.ListView> with the <xref:System.Windows.Forms.ListView.View%2A> property set to <xref:System.Windows.Forms.View.Details> or <xref:System.Windows.Forms.View.List>, and then populate the <xref:System.Windows.Forms.ListView> with items.</span></span>  
  
2.  <span data-ttu-id="f7834-109">Chamar o <xref:System.Windows.Forms.ListView.FindItemWithText%2A> método, passando o texto do item que você deseja localizar.</span><span class="sxs-lookup"><span data-stu-id="f7834-109">Call the <xref:System.Windows.Forms.ListView.FindItemWithText%2A> method, passing the text of the item you would like to find.</span></span>  
  
3.  <span data-ttu-id="f7834-110">O exemplo de código a seguir demonstra como criar um basic <xref:System.Windows.Forms.ListView>, preenchê-lo com itens e usar a entrada de texto do usuário para localizar um item na lista.</span><span class="sxs-lookup"><span data-stu-id="f7834-110">The following code example demonstrates how to create a basic <xref:System.Windows.Forms.ListView>, populate it with items, and use text input from the user to find an item in the list.</span></span>  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#1)]  
  
### <a name="to-find-an-item-using-x--and-y-coordinates"></a><span data-ttu-id="f7834-111">Localizar um item usando coordenadas x e y</span><span class="sxs-lookup"><span data-stu-id="f7834-111">To find an item using x- and y-coordinates</span></span>  
  
1.  <span data-ttu-id="f7834-112">Criar uma <xref:System.Windows.Forms.ListView> com o <xref:System.Windows.Forms.View> propriedade definida como <xref:System.Windows.Forms.View.SmallIcon> ou <xref:System.Windows.Forms.View.LargeIcon>e, em seguida, preencha o <xref:System.Windows.Forms.ListView> com itens.</span><span class="sxs-lookup"><span data-stu-id="f7834-112">Create a <xref:System.Windows.Forms.ListView> with the <xref:System.Windows.Forms.View> property set to <xref:System.Windows.Forms.View.SmallIcon> or <xref:System.Windows.Forms.View.LargeIcon>, and then populate the <xref:System.Windows.Forms.ListView> with items.</span></span>  
  
2.  <span data-ttu-id="f7834-113">Chamar o <xref:System.Windows.Forms.ListView.FindNearestItem%2A> método, passando a desejado coordenadas x e y- e a direção em que você deseja pesquisar.</span><span class="sxs-lookup"><span data-stu-id="f7834-113">Call the <xref:System.Windows.Forms.ListView.FindNearestItem%2A> method, passing the desired x- and y-coordinates and the direction you would like to search.</span></span>  
  
3.  <span data-ttu-id="f7834-114">O exemplo de código a seguir demonstra como criar um ícone básico <xref:System.Windows.Forms.ListView>, preenchê-lo com itens e capture o <xref:System.Windows.Forms.Control.MouseDown> evento para encontrar o item mais próximo na direção para cima.</span><span class="sxs-lookup"><span data-stu-id="f7834-114">The following code example demonstrates how to create a basic icon <xref:System.Windows.Forms.ListView>, populate it with items, and capture the <xref:System.Windows.Forms.Control.MouseDown> event to find the nearest item in the up direction.</span></span>  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#2)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#2)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="f7834-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f7834-115">See also</span></span>
- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.FindItemWithText%2A>
- <xref:System.Windows.Forms.ListView.FindNearestItem%2A>
- [<span data-ttu-id="f7834-116">Controle ListView</span><span class="sxs-lookup"><span data-stu-id="f7834-116">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)
- [<span data-ttu-id="f7834-117">Visão geral do controle ListView</span><span class="sxs-lookup"><span data-stu-id="f7834-117">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
- [<span data-ttu-id="f7834-118">Como: Adicionar e remover itens com o controle ListView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f7834-118">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
