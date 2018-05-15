---
title: Como usar o layout automático para criar um botão
ms.date: 03/30/2017
helpviewer_keywords:
- Button controls [WPF], creating with automatic layout
- automatic layout [WPF], creating buttons
ms.assetid: 96c206d0-9e77-4784-9d2d-5045aed2021c
ms.openlocfilehash: 34b372e886b31e801b5598da90299f9815c47620
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-automatic-layout-to-create-a-button"></a><span data-ttu-id="2f126-102">Como usar o layout automático para criar um botão</span><span class="sxs-lookup"><span data-stu-id="2f126-102">How to: Use Automatic Layout to Create a Button</span></span>
<span data-ttu-id="2f126-103">Este exemplo descreve como usar a abordagem de layout automático para criar um botão em um aplicativo localizável.</span><span class="sxs-lookup"><span data-stu-id="2f126-103">This example describes how to use the automatic layout approach to create a button in a localizable application.</span></span>  
  
 <span data-ttu-id="2f126-104">Localização de um [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] pode ser um processo demorado.</span><span class="sxs-lookup"><span data-stu-id="2f126-104">Localization of a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] can be a time consuming process.</span></span> <span data-ttu-id="2f126-105">Geralmente localizadores precisam redimensionar e reposicionar elementos além de traduções.</span><span class="sxs-lookup"><span data-stu-id="2f126-105">Often localizers need to resize and reposition elements in addition to translating text.</span></span> <span data-ttu-id="2f126-106">No passado cada idioma que um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] foi adaptado para ajuste necessário.</span><span class="sxs-lookup"><span data-stu-id="2f126-106">In the past each language that a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] was adapted for required adjustment.</span></span> <span data-ttu-id="2f126-107">Agora com os recursos do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] você pode criar elementos que reduzem a necessidade de ajuste.</span><span class="sxs-lookup"><span data-stu-id="2f126-107">Now with the capabilities of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] you can design elements that reduce the need for adjustment.</span></span> <span data-ttu-id="2f126-108">A abordagem para escrever aplicativos que podem ser mais facilmente redimensionadas e reposicionadas é chamada `automatic layout`.</span><span class="sxs-lookup"><span data-stu-id="2f126-108">The approach to writing applications that can be more easily resized and repositioned is called `automatic layout`.</span></span>  
  
 <span data-ttu-id="2f126-109">Os dois seguintes [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] exemplos criam aplicativos que instanciam um botão; um com texto em inglês e outro com texto em espanhol.</span><span class="sxs-lookup"><span data-stu-id="2f126-109">The following two [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples create applications that instantiate a button; one with English text and one with Spanish text.</span></span> <span data-ttu-id="2f126-110">Observe que o código é o mesmo, exceto o texto. o botão ajustado para acomodar o texto.</span><span class="sxs-lookup"><span data-stu-id="2f126-110">Notice that the code is the same except for the text; the button adjusts to fit the text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f126-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2f126-111">Example</span></span>  
 [!code-xaml[LocalizationBtn_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 [!code-xaml[LocalizationBtn#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 <span data-ttu-id="2f126-112">O gráfico a seguir mostra a saída dos exemplos de código.</span><span class="sxs-lookup"><span data-stu-id="2f126-112">The following graphic shows the output of the code samples.</span></span>  
  
 <span data-ttu-id="2f126-113">![O mesmo botão com texto em idiomas diferentes](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")</span><span class="sxs-lookup"><span data-stu-id="2f126-113">![The same button with text in different languages](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")</span></span>  
<span data-ttu-id="2f126-114">Botão redimensionável automaticamente</span><span class="sxs-lookup"><span data-stu-id="2f126-114">Auto Resizable Button</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f126-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2f126-115">See Also</span></span>  
 [<span data-ttu-id="2f126-116">Visão geral do uso de layout automático</span><span class="sxs-lookup"><span data-stu-id="2f126-116">Use Automatic Layout Overview</span></span>](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)  
 [<span data-ttu-id="2f126-117">Usar uma grade para layout automático</span><span class="sxs-lookup"><span data-stu-id="2f126-117">Use a Grid for Automatic Layout</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)
