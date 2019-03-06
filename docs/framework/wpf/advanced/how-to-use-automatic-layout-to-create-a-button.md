---
title: 'Como: Usar layout automático para criar um botão'
ms.date: 03/30/2017
helpviewer_keywords:
- Button controls [WPF], creating with automatic layout
- automatic layout [WPF], creating buttons
ms.assetid: 96c206d0-9e77-4784-9d2d-5045aed2021c
ms.openlocfilehash: 2172aba80fe963be33036a7245f228e8d5bfedda
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370339"
---
# <a name="how-to-use-automatic-layout-to-create-a-button"></a><span data-ttu-id="bc5c8-102">Como: Usar layout automático para criar um botão</span><span class="sxs-lookup"><span data-stu-id="bc5c8-102">How to: Use Automatic Layout to Create a Button</span></span>
<span data-ttu-id="bc5c8-103">Este exemplo descreve como usar a abordagem de layout automático para criar um botão em um aplicativo localizável.</span><span class="sxs-lookup"><span data-stu-id="bc5c8-103">This example describes how to use the automatic layout approach to create a button in a localizable application.</span></span>  
  
 <span data-ttu-id="bc5c8-104">Localização de um [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] pode ser um processo demorado.</span><span class="sxs-lookup"><span data-stu-id="bc5c8-104">Localization of a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] can be a time consuming process.</span></span> <span data-ttu-id="bc5c8-105">Geralmente, localizadores precisam redimensionar e reposicionar elementos além de traduzir o texto.</span><span class="sxs-lookup"><span data-stu-id="bc5c8-105">Often localizers need to resize and reposition elements in addition to translating text.</span></span> <span data-ttu-id="bc5c8-106">No passado cada idioma que um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] foi adaptado exigia um ajuste.</span><span class="sxs-lookup"><span data-stu-id="bc5c8-106">In the past each language that a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] was adapted for required adjustment.</span></span> <span data-ttu-id="bc5c8-107">Agora, com os recursos do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] você pode criar elementos que reduzem a necessidade de ajuste.</span><span class="sxs-lookup"><span data-stu-id="bc5c8-107">Now with the capabilities of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] you can design elements that reduce the need for adjustment.</span></span> <span data-ttu-id="bc5c8-108">A abordagem para escrever aplicativos que podem ser mais facilmente redimensionados e reposicionados é chamada `automatic layout`.</span><span class="sxs-lookup"><span data-stu-id="bc5c8-108">The approach to writing applications that can be more easily resized and repositioned is called `automatic layout`.</span></span>  
  
 <span data-ttu-id="bc5c8-109">Os dois seguintes [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] exemplos criam aplicativos que criar uma instância de um botão, uma com texto em inglês e outra com texto em espanhol.</span><span class="sxs-lookup"><span data-stu-id="bc5c8-109">The following two [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples create applications that instantiate a button; one with English text and one with Spanish text.</span></span> <span data-ttu-id="bc5c8-110">Observe que o código é o mesmo, exceto para o texto; o botão é ajustada para se ajustar ao texto.</span><span class="sxs-lookup"><span data-stu-id="bc5c8-110">Notice that the code is the same except for the text; the button adjusts to fit the text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc5c8-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bc5c8-111">Example</span></span>  
 [!code-xaml[LocalizationBtn_snip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 [!code-xaml[LocalizationBtn#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 <span data-ttu-id="bc5c8-112">O gráfico a seguir mostra a saída dos exemplos de código.</span><span class="sxs-lookup"><span data-stu-id="bc5c8-112">The following graphic shows the output of the code samples.</span></span>  
  
 <span data-ttu-id="bc5c8-113">![O mesmo botão com texto em diferentes idiomas](./media/globalizationbutton.png "GlobalizationButton")</span><span class="sxs-lookup"><span data-stu-id="bc5c8-113">![The same button with text in different languages](./media/globalizationbutton.png "GlobalizationButton")</span></span>  
<span data-ttu-id="bc5c8-114">Botão redimensionável automaticamente</span><span class="sxs-lookup"><span data-stu-id="bc5c8-114">Auto Resizable Button</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc5c8-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bc5c8-115">See also</span></span>
- [<span data-ttu-id="bc5c8-116">Visão geral do uso de layout automático</span><span class="sxs-lookup"><span data-stu-id="bc5c8-116">Use Automatic Layout Overview</span></span>](use-automatic-layout-overview.md)
- [<span data-ttu-id="bc5c8-117">Usar uma grade para layout automático</span><span class="sxs-lookup"><span data-stu-id="bc5c8-117">Use a Grid for Automatic Layout</span></span>](how-to-use-a-grid-for-automatic-layout.md)
