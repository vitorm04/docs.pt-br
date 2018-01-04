---
title: "Como usar o layout automático para criar um botão"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Button controls [WPF], creating with automatic layout
- automatic layout [WPF], creating buttons
ms.assetid: 96c206d0-9e77-4784-9d2d-5045aed2021c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c642e6491722e9bfe35337d066e3870f5a70f38c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-automatic-layout-to-create-a-button"></a><span data-ttu-id="28474-102">Como usar o layout automático para criar um botão</span><span class="sxs-lookup"><span data-stu-id="28474-102">How to: Use Automatic Layout to Create a Button</span></span>
<span data-ttu-id="28474-103">Este exemplo descreve como usar a abordagem de layout automático para criar um botão em um aplicativo localizável.</span><span class="sxs-lookup"><span data-stu-id="28474-103">This example describes how to use the automatic layout approach to create a button in a localizable application.</span></span>  
  
 <span data-ttu-id="28474-104">Localização de um [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] pode ser um processo demorado.</span><span class="sxs-lookup"><span data-stu-id="28474-104">Localization of a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] can be a time consuming process.</span></span> <span data-ttu-id="28474-105">Geralmente localizadores precisam redimensionar e reposicionar elementos além de traduções.</span><span class="sxs-lookup"><span data-stu-id="28474-105">Often localizers need to resize and reposition elements in addition to translating text.</span></span> <span data-ttu-id="28474-106">No passado cada idioma que um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] foi adaptado para ajuste necessário.</span><span class="sxs-lookup"><span data-stu-id="28474-106">In the past each language that a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] was adapted for required adjustment.</span></span> <span data-ttu-id="28474-107">Agora com os recursos do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] você pode criar elementos que reduzem a necessidade de ajuste.</span><span class="sxs-lookup"><span data-stu-id="28474-107">Now with the capabilities of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] you can design elements that reduce the need for adjustment.</span></span> <span data-ttu-id="28474-108">A abordagem para escrever aplicativos que podem ser mais facilmente redimensionadas e reposicionadas é chamada `automatic layout`.</span><span class="sxs-lookup"><span data-stu-id="28474-108">The approach to writing applications that can be more easily resized and repositioned is called `automatic layout`.</span></span>  
  
 <span data-ttu-id="28474-109">Os dois seguintes [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] exemplos criam aplicativos que instanciam um botão; um com texto em inglês e outro com texto em espanhol.</span><span class="sxs-lookup"><span data-stu-id="28474-109">The following two [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples create applications that instantiate a button; one with English text and one with Spanish text.</span></span> <span data-ttu-id="28474-110">Observe que o código é o mesmo, exceto o texto. o botão ajustado para acomodar o texto.</span><span class="sxs-lookup"><span data-stu-id="28474-110">Notice that the code is the same except for the text; the button adjusts to fit the text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28474-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="28474-111">Example</span></span>  
 [!code-xaml[LocalizationBtn_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 [!code-xaml[LocalizationBtn#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 <span data-ttu-id="28474-112">O gráfico a seguir mostra a saída dos exemplos de código.</span><span class="sxs-lookup"><span data-stu-id="28474-112">The following graphic shows the output of the code samples.</span></span>  
  
 <span data-ttu-id="28474-113">![O mesmo botão com texto em idiomas diferentes](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")</span><span class="sxs-lookup"><span data-stu-id="28474-113">![The same button with text in different languages](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")</span></span>  
<span data-ttu-id="28474-114">Botão redimensionável automaticamente</span><span class="sxs-lookup"><span data-stu-id="28474-114">Auto Resizable Button</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28474-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="28474-115">See Also</span></span>  
 [<span data-ttu-id="28474-116">Visão geral do uso de layout automático</span><span class="sxs-lookup"><span data-stu-id="28474-116">Use Automatic Layout Overview</span></span>](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)  
 [<span data-ttu-id="28474-117">Usar uma grade para layout automático</span><span class="sxs-lookup"><span data-stu-id="28474-117">Use a Grid for Automatic Layout</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)
