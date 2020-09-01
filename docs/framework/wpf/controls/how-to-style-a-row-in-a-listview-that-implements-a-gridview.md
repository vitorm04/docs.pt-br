---
title: 'Como: Estilizar uma linha em um ListView que usa um GridView'
ms.date: 03/30/2017
helpviewer_keywords:
- GridView controls [WPF], styling rows
- styling rows in ListViews implementing GridViews [WPF]
- ListView controls [WPF], styling rows with GridViews
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
ms.openlocfilehash: 4b8b8e2f1b2d7207a37205d981bf2dab3f65122e
ms.sourcegitcommit: e0803b8975d3eb12e735a5d07637020dd6dac5ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2020
ms.locfileid: "89271939"
---
# <a name="how-to-style-a-row-in-a-listview-that-implements-a-gridview"></a><span data-ttu-id="7f927-102">Como criar uma linha em um ListView que implemente um GridView</span><span class="sxs-lookup"><span data-stu-id="7f927-102">How to: Style a Row in a ListView That Implements a GridView</span></span>
<span data-ttu-id="7f927-103">Este exemplo mostra como Estilizar uma linha em um <xref:System.Windows.Controls.ListView> controle que usa um <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ListView.View%2A> modo.</span><span class="sxs-lookup"><span data-stu-id="7f927-103">This example shows how to style a row in a <xref:System.Windows.Controls.ListView> control that uses a <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ListView.View%2A> mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f927-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7f927-104">Example</span></span>  
 <span data-ttu-id="7f927-105">Você pode Estilizar uma linha em um <xref:System.Windows.Controls.ListView> controle definindo um <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> no <xref:System.Windows.Controls.ListView> controle.</span><span class="sxs-lookup"><span data-stu-id="7f927-105">You can style a row in a <xref:System.Windows.Controls.ListView> control by setting an <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> on the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="7f927-106">Defina o estilo para seus itens que são representados como <xref:System.Windows.Controls.ListViewItem> objetos.</span><span class="sxs-lookup"><span data-stu-id="7f927-106">Set the style for its items that are represented as <xref:System.Windows.Controls.ListViewItem> objects.</span></span> <span data-ttu-id="7f927-107">O <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> faz referência aos <xref:System.Windows.Controls.ControlTemplate> objetos que são usados para exibir o conteúdo da linha.</span><span class="sxs-lookup"><span data-stu-id="7f927-107">The <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> references the <xref:System.Windows.Controls.ControlTemplate> objects that are used to display the row content.</span></span>  
  
 <span data-ttu-id="7f927-108">O exemplo completo, do qual os exemplos a seguir são extraídos, exibe uma coleção de informações de música que são armazenadas em um banco de dados XML.</span><span class="sxs-lookup"><span data-stu-id="7f927-108">The complete sample, which the following examples are extracted from, displays a collection of song information that is stored in an XML database.</span></span> <span data-ttu-id="7f927-109">Cada música no banco de dados tem um campo de classificação e o valor desse campo especifica como exibir uma linha de informações sobre a música.</span><span class="sxs-lookup"><span data-stu-id="7f927-109">Each song in the database has a rating field and the value of this field specifies how to display a row of song information.</span></span>  
  
 <span data-ttu-id="7f927-110">O exemplo a seguir mostra como definir <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> para os <xref:System.Windows.Controls.ListViewItem> objetos que representam as músicas na coleção de músicas.</span><span class="sxs-lookup"><span data-stu-id="7f927-110">The following example shows how to define <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> for the <xref:System.Windows.Controls.ListViewItem> objects that represent the songs in the song collection.</span></span> <span data-ttu-id="7f927-111">Os <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> objetos de referências <xref:System.Windows.Controls.ControlTemplate> que especificam como exibir uma linha de informações de música.</span><span class="sxs-lookup"><span data-stu-id="7f927-111">The <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> references <xref:System.Windows.Controls.ControlTemplate> objects that specify how to display a row of song information.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#ItemContainerStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#itemcontainerstyle)]  
  
 <span data-ttu-id="7f927-112">O exemplo a seguir mostra um <xref:System.Windows.Controls.ControlTemplate> que adiciona a cadeia de texto `"Strongly Recommended"` à linha.</span><span class="sxs-lookup"><span data-stu-id="7f927-112">The following example shows a <xref:System.Windows.Controls.ControlTemplate> that adds the text string `"Strongly Recommended"` to the row.</span></span> <span data-ttu-id="7f927-113">Esse modelo é referenciado no <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> e exibe quando a classificação da música tem um valor de 5 (cinco).</span><span class="sxs-lookup"><span data-stu-id="7f927-113">This template is referenced in the <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> and displays when the song's rating has a value of 5 (five).</span></span> <span data-ttu-id="7f927-114">O <xref:System.Windows.Controls.ControlTemplate> inclui um <xref:System.Windows.Controls.GridViewRowPresenter> objeto que dispõe o conteúdo da linha em colunas, conforme definido pelo modo de <xref:System.Windows.Controls.GridView> exibição.</span><span class="sxs-lookup"><span data-stu-id="7f927-114">The <xref:System.Windows.Controls.ControlTemplate> includes a <xref:System.Windows.Controls.GridViewRowPresenter> object that lays out the contents of the row in columns as defined by the <xref:System.Windows.Controls.GridView> view mode.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#ControlTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#controltemplate)]  
  
 <span data-ttu-id="7f927-115">O exemplo a seguir define <xref:System.Windows.Controls.GridView> .</span><span class="sxs-lookup"><span data-stu-id="7f927-115">The following example defines <xref:System.Windows.Controls.GridView>.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#GridView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#gridview)]  
  
## <a name="see-also"></a><span data-ttu-id="7f927-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="7f927-116">See also</span></span>

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="7f927-117">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="7f927-117">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="7f927-118">Visão geral de ListView</span><span class="sxs-lookup"><span data-stu-id="7f927-118">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="7f927-119">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="7f927-119">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
