---
title: Como criar uma linha em um ListView que implemente um GridView
ms.date: 03/30/2017
helpviewer_keywords:
- GridView controls [WPF], styling rows
- styling rows in ListViews implementing GridViews [WPF]
- ListView controls [WPF], styling rows with GridViews
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
ms.openlocfilehash: 150988aab368e3ffef0107d29bea5ebc53163946
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459312"
---
# <a name="how-to-style-a-row-in-a-listview-that-implements-a-gridview"></a><span data-ttu-id="af008-102">Como criar uma linha em um ListView que implemente um GridView</span><span class="sxs-lookup"><span data-stu-id="af008-102">How to: Style a Row in a ListView That Implements a GridView</span></span>
<span data-ttu-id="af008-103">Este exemplo mostra como Estilizar uma linha em um controle de <xref:System.Windows.Controls.ListView> que implementa um modo de <xref:System.Windows.Controls.ListView.View%2A> de <xref:System.Windows.Controls.GridView>.</span><span class="sxs-lookup"><span data-stu-id="af008-103">This example shows how to style a row in a <xref:System.Windows.Controls.ListView> control that implements a <xref:System.Windows.Controls.GridView><xref:System.Windows.Controls.ListView.View%2A> mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af008-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="af008-104">Example</span></span>  
 <span data-ttu-id="af008-105">Você pode Estilizar uma linha em um controle de <xref:System.Windows.Controls.ListView> definindo um <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> no controle de <xref:System.Windows.Controls.ListView>.</span><span class="sxs-lookup"><span data-stu-id="af008-105">You can style a row in a <xref:System.Windows.Controls.ListView> control by setting an <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> on the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="af008-106">Defina o estilo para seus itens que são representados como objetos <xref:System.Windows.Controls.ListViewItem>.</span><span class="sxs-lookup"><span data-stu-id="af008-106">Set the style for its items that are represented as <xref:System.Windows.Controls.ListViewItem> objects.</span></span> <span data-ttu-id="af008-107">O <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> faz referência aos objetos <xref:System.Windows.Controls.ControlTemplate> usados para exibir o conteúdo da linha.</span><span class="sxs-lookup"><span data-stu-id="af008-107">The <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> references the <xref:System.Windows.Controls.ControlTemplate> objects that are used to display the row content.</span></span>  
  
 <span data-ttu-id="af008-108">O exemplo completo, do qual os exemplos a seguir foram extraídos, exibe uma coleção de informações de músicas que são armazenadas em um banco de dados do [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="af008-108">The complete sample, which the following examples are extracted from, displays a collection of song information that is stored in an [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] database.</span></span> <span data-ttu-id="af008-109">Cada música no banco de dados tem um campo de classificação e o valor desse campo especifica como exibir uma linha de informações sobre a música.</span><span class="sxs-lookup"><span data-stu-id="af008-109">Each song in the database has a rating field and the value of this field specifies how to display a row of song information.</span></span>  
  
 <span data-ttu-id="af008-110">O exemplo a seguir mostra como definir <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> para os objetos <xref:System.Windows.Controls.ListViewItem> que representam as músicas na coleção de músicas.</span><span class="sxs-lookup"><span data-stu-id="af008-110">The following example shows how to define <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> for the <xref:System.Windows.Controls.ListViewItem> objects that represent the songs in the song collection.</span></span> <span data-ttu-id="af008-111">O <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> faz referência a objetos <xref:System.Windows.Controls.ControlTemplate> que especificam como exibir uma linha de informações de música.</span><span class="sxs-lookup"><span data-stu-id="af008-111">The <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> references <xref:System.Windows.Controls.ControlTemplate> objects that specify how to display a row of song information.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#ItemContainerStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#itemcontainerstyle)]  
  
 <span data-ttu-id="af008-112">O exemplo a seguir mostra um <xref:System.Windows.Controls.ControlTemplate> que adiciona a cadeia de caracteres de texto `"Strongly Recommended"` à linha.</span><span class="sxs-lookup"><span data-stu-id="af008-112">The following example shows a <xref:System.Windows.Controls.ControlTemplate> that adds the text string `"Strongly Recommended"` to the row.</span></span> <span data-ttu-id="af008-113">Esse modelo é referenciado na <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> e é exibido quando a classificação da música tem um valor de 5 (cinco).</span><span class="sxs-lookup"><span data-stu-id="af008-113">This template is referenced in the <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> and displays when the song's rating has a value of 5 (five).</span></span> <span data-ttu-id="af008-114">O <xref:System.Windows.Controls.ControlTemplate> inclui um objeto <xref:System.Windows.Controls.GridViewRowPresenter> que dispõe o conteúdo da linha em colunas, conforme definido pelo modo de exibição <xref:System.Windows.Controls.GridView>.</span><span class="sxs-lookup"><span data-stu-id="af008-114">The <xref:System.Windows.Controls.ControlTemplate> includes a <xref:System.Windows.Controls.GridViewRowPresenter> object that lays out the contents of the row in columns as defined by the <xref:System.Windows.Controls.GridView> view mode.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#ControlTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#controltemplate)]  
  
 <span data-ttu-id="af008-115">O exemplo a seguir define <xref:System.Windows.Controls.GridView>.</span><span class="sxs-lookup"><span data-stu-id="af008-115">The following example defines <xref:System.Windows.Controls.GridView>.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#GridView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#gridview)]  
  
## <a name="see-also"></a><span data-ttu-id="af008-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="af008-116">See also</span></span>

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="af008-117">Tópicos explicativos</span><span class="sxs-lookup"><span data-stu-id="af008-117">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="af008-118">Visão geral de ListView</span><span class="sxs-lookup"><span data-stu-id="af008-118">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="af008-119">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="af008-119">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
