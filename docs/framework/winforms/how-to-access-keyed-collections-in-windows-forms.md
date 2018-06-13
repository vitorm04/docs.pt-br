---
title: Como acessar coleções indexadas por chave no Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyed collections [Windows Forms]
- collections [Windows Forms], accessing with keys
ms.assetid: b9b79b8b-d9bf-4f8c-b9d6-9578bc3219d3
ms.openlocfilehash: 59e5cea29ee520b1f13f8fae98ae4042cc86fef7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538720"
---
# <a name="how-to-access-keyed-collections-in-windows-forms"></a><span data-ttu-id="82a7b-102">Como acessar coleções indexadas por chave no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="82a7b-102">How to: Access Keyed Collections in Windows Forms</span></span>
-   <span data-ttu-id="82a7b-103">Você pode acessar itens de coleção individuais por chave.</span><span class="sxs-lookup"><span data-stu-id="82a7b-103">You can access individual collection items by key.</span></span> <span data-ttu-id="82a7b-104">Essa funcionalidade foi adicionada a muitas classes de coleção que normalmente são usadas por aplicativos dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="82a7b-104">This functionality has been added to many collection classes that are typically used by Windows Forms applications.</span></span> <span data-ttu-id="82a7b-105">A lista a seguir exibe algumas das classes de coleção que têm coleções acessíveis por chave:</span><span class="sxs-lookup"><span data-stu-id="82a7b-105">The following list shows some of the collection classes that have accessible keyed collections:</span></span>  
  
-   <xref:System.Windows.Forms.ListView.ListViewItemCollection>  
  
-   <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection>  
  
-   <xref:System.Windows.Forms.Control.ControlCollection>  
  
-   <xref:System.Windows.Forms.TabControl.TabPageCollection>  
  
-   <xref:System.Windows.Forms.TreeNodeCollection>  
  
 <span data-ttu-id="82a7b-106">Normalmente, a chave associada a um item em uma coleção é o nome do item.</span><span class="sxs-lookup"><span data-stu-id="82a7b-106">The key associated with an item in a collection is typically the name of the item.</span></span> <span data-ttu-id="82a7b-107">Os procedimentos a seguir mostram como usar classes de coleção para executar tarefas comuns.</span><span class="sxs-lookup"><span data-stu-id="82a7b-107">The following procedures show you how to use collection classes to perform common tasks.</span></span>  
  
### <a name="to-find-and-give-focus-to-a-nested-control-in-a-control-collection"></a><span data-ttu-id="82a7b-108">Para localizar e colocar em foco um controle aninhado em uma coleção de controles</span><span class="sxs-lookup"><span data-stu-id="82a7b-108">To find and give focus to a nested control in a control collection</span></span>  
  
-   <span data-ttu-id="82a7b-109">Use o <xref:System.Windows.Forms.Control.ControlCollection.Find%2A> e <xref:System.Windows.Forms.Control.Focus%2A> métodos para especificar o nome do controle para localizar e colocado em foco.</span><span class="sxs-lookup"><span data-stu-id="82a7b-109">Use the <xref:System.Windows.Forms.Control.ControlCollection.Find%2A> and <xref:System.Windows.Forms.Control.Focus%2A> methods to specify the name of the control to find and give focus to.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#1)]  
  
### <a name="to-access-an-image-in-an-image-collection"></a><span data-ttu-id="82a7b-110">Para acessar uma imagem em uma coleção de imagens</span><span class="sxs-lookup"><span data-stu-id="82a7b-110">To access an image in an image collection</span></span>  
  
-   <span data-ttu-id="82a7b-111">Use o <xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A> propriedade para especificar o nome da imagem que você deseja acessar.</span><span class="sxs-lookup"><span data-stu-id="82a7b-111">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A> property to specify the name of the image you want to access.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#2)]  
  
### <a name="to-set-a-tab-page-as-the-selected-tab"></a><span data-ttu-id="82a7b-112">Para definir uma página da guia como a guia selecionada</span><span class="sxs-lookup"><span data-stu-id="82a7b-112">To set a tab page as the selected tab</span></span>  
  
-   <span data-ttu-id="82a7b-113">Use o <xref:System.Windows.Forms.TabControl.SelectedTab%2A> propriedade junto com o <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A> propriedade para especificar o nome da página da guia para definir como a guia selecionada.</span><span class="sxs-lookup"><span data-stu-id="82a7b-113">Use the <xref:System.Windows.Forms.TabControl.SelectedTab%2A> property together with the <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A> property to specify the name of the tab page to set as the selected tab.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="82a7b-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82a7b-114">See Also</span></span>  
 [<span data-ttu-id="82a7b-115">Guia de introdução ao Windows Forms</span><span class="sxs-lookup"><span data-stu-id="82a7b-115">Getting Started with Windows Forms</span></span>](../../../docs/framework/winforms/getting-started-with-windows-forms.md)  
 [<span data-ttu-id="82a7b-116">Como adicionar ou remover imagens com o componente ImageList dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="82a7b-116">How to: Add or Remove Images with the Windows Forms ImageList Component</span></span>](../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
