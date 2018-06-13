---
title: Como adicionar recursos de pesquisa a um controle ListView
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
ms.openlocfilehash: 2049638998f7a8d099e14fab9c95384a49c67833
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528266"
---
# <a name="how-to-add-search-capabilities-to-a-listview-control"></a><span data-ttu-id="927c0-102">Como adicionar recursos de pesquisa a um controle ListView</span><span class="sxs-lookup"><span data-stu-id="927c0-102">How to: Add Search Capabilities to a ListView Control</span></span>
<span data-ttu-id="927c0-103">Muitas vezes, ao trabalhar com uma grande lista de itens em uma <xref:System.Windows.Forms.ListView> controle, que você quer oferecer recursos de pesquisa para o usuário.</span><span class="sxs-lookup"><span data-stu-id="927c0-103">Oftentimes when working with a large list of items in a <xref:System.Windows.Forms.ListView> control, you want to offer search capabilities to the user.</span></span> <span data-ttu-id="927c0-104">O <xref:System.Windows.Forms.ListView> controle oferece esse recurso de duas maneiras diferentes: correspondência de texto e pesquisa de localidade.</span><span class="sxs-lookup"><span data-stu-id="927c0-104">The <xref:System.Windows.Forms.ListView> control offers this capability in two different ways: text matching and location searching.</span></span>  
  
 <span data-ttu-id="927c0-105">O <xref:System.Windows.Forms.ListView.FindItemWithText%2A> método permite que você executar uma pesquisa de texto em uma <xref:System.Windows.Forms.ListView> na exibição de lista ou detalhes, recebe uma cadeia de caracteres de pesquisa e um opcional começando e terminando o índice.</span><span class="sxs-lookup"><span data-stu-id="927c0-105">The <xref:System.Windows.Forms.ListView.FindItemWithText%2A> method allows you to perform a text search on a <xref:System.Windows.Forms.ListView> in list or details view, given a search string and an optional starting and ending index.</span></span> <span data-ttu-id="927c0-106">Em contraste, o <xref:System.Windows.Forms.ListView.FindNearestItem%2A> método permite que você encontre um item em uma <xref:System.Windows.Forms.ListView> no modo de exibição de ícone ou lado a lado, dado um conjunto de coordenadas x e y e uma direção de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="927c0-106">In contrast, the <xref:System.Windows.Forms.ListView.FindNearestItem%2A> method allows you to find an item in a <xref:System.Windows.Forms.ListView> in icon or tile view, given a set of x- and y-coordinates and a direction to search.</span></span>  
  
### <a name="to-find-an-item-using-text"></a><span data-ttu-id="927c0-107">Localizar um item usando texto</span><span class="sxs-lookup"><span data-stu-id="927c0-107">To find an item using text</span></span>  
  
1.  <span data-ttu-id="927c0-108">Criar um <xref:System.Windows.Forms.ListView> com o <xref:System.Windows.Forms.ListView.View%2A> propriedade definida como <xref:System.Windows.Forms.View.Details> ou <xref:System.Windows.Forms.View.List>e, em seguida, preencha o <xref:System.Windows.Forms.ListView> com itens.</span><span class="sxs-lookup"><span data-stu-id="927c0-108">Create a <xref:System.Windows.Forms.ListView> with the <xref:System.Windows.Forms.ListView.View%2A> property set to <xref:System.Windows.Forms.View.Details> or <xref:System.Windows.Forms.View.List>, and then populate the <xref:System.Windows.Forms.ListView> with items.</span></span>  
  
2.  <span data-ttu-id="927c0-109">Chamar o <xref:System.Windows.Forms.ListView.FindItemWithText%2A> método, passando o texto do item que você deseja localizar.</span><span class="sxs-lookup"><span data-stu-id="927c0-109">Call the <xref:System.Windows.Forms.ListView.FindItemWithText%2A> method, passing the text of the item you would like to find.</span></span>  
  
3.  <span data-ttu-id="927c0-110">O exemplo de código a seguir demonstra como criar um basic <xref:System.Windows.Forms.ListView>, preenchê-lo com os itens e usar a entrada de texto do usuário para localizar um item na lista.</span><span class="sxs-lookup"><span data-stu-id="927c0-110">The following code example demonstrates how to create a basic <xref:System.Windows.Forms.ListView>, populate it with items, and use text input from the user to find an item in the list.</span></span>  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#1)]  
  
### <a name="to-find-an-item-using-x--and-y-coordinates"></a><span data-ttu-id="927c0-111">Localizar um item usando coordenadas x e y</span><span class="sxs-lookup"><span data-stu-id="927c0-111">To find an item using x- and y-coordinates</span></span>  
  
1.  <span data-ttu-id="927c0-112">Criar um <xref:System.Windows.Forms.ListView> com o <xref:System.Windows.Forms.View> propriedade definida como <xref:System.Windows.Forms.View.SmallIcon> ou <xref:System.Windows.Forms.View.LargeIcon>e, em seguida, preencha o <xref:System.Windows.Forms.ListView> com itens.</span><span class="sxs-lookup"><span data-stu-id="927c0-112">Create a <xref:System.Windows.Forms.ListView> with the <xref:System.Windows.Forms.View> property set to <xref:System.Windows.Forms.View.SmallIcon> or <xref:System.Windows.Forms.View.LargeIcon>, and then populate the <xref:System.Windows.Forms.ListView> with items.</span></span>  
  
2.  <span data-ttu-id="927c0-113">Chamar o <xref:System.Windows.Forms.ListView.FindNearestItem%2A> método, passando a desejado e y-coordenadas x e a direção em que você deseja pesquisar.</span><span class="sxs-lookup"><span data-stu-id="927c0-113">Call the <xref:System.Windows.Forms.ListView.FindNearestItem%2A> method, passing the desired x- and y-coordinates and the direction you would like to search.</span></span>  
  
3.  <span data-ttu-id="927c0-114">O exemplo de código a seguir demonstra como criar um ícone básico <xref:System.Windows.Forms.ListView>, preenchê-lo com os itens e capture o <xref:System.Windows.Forms.Control.MouseDown> evento para encontrar o item mais próximo na direção se.</span><span class="sxs-lookup"><span data-stu-id="927c0-114">The following code example demonstrates how to create a basic icon <xref:System.Windows.Forms.ListView>, populate it with items, and capture the <xref:System.Windows.Forms.Control.MouseDown> event to find the nearest item in the up direction.</span></span>  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#2)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#2)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="927c0-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="927c0-115">See Also</span></span>  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.FindItemWithText%2A>  
 <xref:System.Windows.Forms.ListView.FindNearestItem%2A>  
 [<span data-ttu-id="927c0-116">Controle ListView</span><span class="sxs-lookup"><span data-stu-id="927c0-116">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [<span data-ttu-id="927c0-117">Visão geral do controle ListView</span><span class="sxs-lookup"><span data-stu-id="927c0-117">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="927c0-118">Como Adicionar e Remover Itens com o Controle ListView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="927c0-118">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
