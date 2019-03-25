---
title: 'Como: Usar layout automático para criar um botão'
ms.date: 03/30/2017
helpviewer_keywords:
- Button controls [WPF], creating with automatic layout
- automatic layout [WPF], creating buttons
ms.assetid: 96c206d0-9e77-4784-9d2d-5045aed2021c
ms.openlocfilehash: 8eb1e93dd87c210812c9b7758c744a616ef2d862
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409777"
---
# <a name="how-to-use-automatic-layout-to-create-a-button"></a><span data-ttu-id="ae36b-102">Como: Usar layout automático para criar um botão</span><span class="sxs-lookup"><span data-stu-id="ae36b-102">How to: Use Automatic Layout to Create a Button</span></span>
<span data-ttu-id="ae36b-103">Este exemplo descreve como usar a abordagem de layout automático para criar um botão em um aplicativo localizável.</span><span class="sxs-lookup"><span data-stu-id="ae36b-103">This example describes how to use the automatic layout approach to create a button in a localizable application.</span></span>  
  
 <span data-ttu-id="ae36b-104">Localização de um [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] pode ser um processo demorado.</span><span class="sxs-lookup"><span data-stu-id="ae36b-104">Localization of a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] can be a time consuming process.</span></span> <span data-ttu-id="ae36b-105">Geralmente, localizadores precisam redimensionar e reposicionar elementos além de traduzir o texto.</span><span class="sxs-lookup"><span data-stu-id="ae36b-105">Often localizers need to resize and reposition elements in addition to translating text.</span></span> <span data-ttu-id="ae36b-106">No passado cada idioma que um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] foi adaptado exigia um ajuste.</span><span class="sxs-lookup"><span data-stu-id="ae36b-106">In the past each language that a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] was adapted for required adjustment.</span></span> <span data-ttu-id="ae36b-107">Agora, com os recursos do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] você pode criar elementos que reduzem a necessidade de ajuste.</span><span class="sxs-lookup"><span data-stu-id="ae36b-107">Now with the capabilities of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] you can design elements that reduce the need for adjustment.</span></span> <span data-ttu-id="ae36b-108">A abordagem para escrever aplicativos que podem ser mais facilmente redimensionados e reposicionados é chamada `automatic layout`.</span><span class="sxs-lookup"><span data-stu-id="ae36b-108">The approach to writing applications that can be more easily resized and repositioned is called `automatic layout`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae36b-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ae36b-109">Example</span></span>  

<span data-ttu-id="ae36b-110">Os dois seguintes [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] exemplos criam aplicativos que criar uma instância de um botão, uma com texto em inglês e outra com texto em espanhol.</span><span class="sxs-lookup"><span data-stu-id="ae36b-110">The following two [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples create applications that instantiate a button; one with English text and one with Spanish text.</span></span> <span data-ttu-id="ae36b-111">Observe que o código é o mesmo, exceto para o texto; o botão é ajustada para se ajustar ao texto.</span><span class="sxs-lookup"><span data-stu-id="ae36b-111">Notice that the code is the same except for the text; the button adjusts to fit the text.</span></span>

[!code-xaml[LocalizationBtn_snip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
[!code-xaml[LocalizationBtn#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 <span data-ttu-id="ae36b-112">O gráfico a seguir mostra a saída dos exemplos de código com botões redimensionável automaticamente:</span><span class="sxs-lookup"><span data-stu-id="ae36b-112">The following graphic shows the output of the code samples with auto-resizable buttons:</span></span>
  
 ![O mesmo botão com texto em idiomas diferentes](./media/use-automatic-layout-overview/auto-resizable-button.png)  
  
## <a name="see-also"></a><span data-ttu-id="ae36b-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae36b-114">See also</span></span>

- [<span data-ttu-id="ae36b-115">Visão geral do uso de layout automático</span><span class="sxs-lookup"><span data-stu-id="ae36b-115">Use Automatic Layout Overview</span></span>](use-automatic-layout-overview.md)
- [<span data-ttu-id="ae36b-116">Usar uma grade para layout automático</span><span class="sxs-lookup"><span data-stu-id="ae36b-116">Use a Grid for Automatic Layout</span></span>](how-to-use-a-grid-for-automatic-layout.md)
