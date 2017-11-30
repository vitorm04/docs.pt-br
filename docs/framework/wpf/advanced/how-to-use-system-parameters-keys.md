---
title: "Como usar chaves de parâmetros do sistema"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resource keys [WPF], SystemParameters class
- classes [WPF], SystemParameters
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2b5f45f386c58b0577a2716c6fe1396f4c44f4ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-system-parameters-keys"></a><span data-ttu-id="e38b1-102">Como usar chaves de parâmetros do sistema</span><span class="sxs-lookup"><span data-stu-id="e38b1-102">How to: Use System Parameters Keys</span></span>
<span data-ttu-id="e38b1-103">Os recursos do sistema expõem inúmeras métricas do sistema como recursos para ajudar os desenvolvedores a criar recursos visuais consistentes com as configurações do sistema.</span><span class="sxs-lookup"><span data-stu-id="e38b1-103">System resources expose a number of system metrics as resources to help developers create visuals that are consistent with system settings.</span></span> <span data-ttu-id="e38b1-104"><xref:System.Windows.SystemParameters>é uma classe que contém os valores de parâmetros de sistema e as chaves associadas aos valores — por exemplo, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> e <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="e38b1-104"><xref:System.Windows.SystemParameters> is a class that contains both system parameter values and resource keys that bind to the values—for example, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> and <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>.</span></span> <span data-ttu-id="e38b1-105">Métricas de parâmetros de sistema podem ser usadas como recursos estáticos ou dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="e38b1-105">System parameter metrics can be used as either static or dynamic resources.</span></span> <span data-ttu-id="e38b1-106">Use um recurso dinâmico se você quiser que a métrica de parâmetro para atualizar automaticamente enquanto o aplicativo é executado; Caso contrário, use um recurso estático.</span><span class="sxs-lookup"><span data-stu-id="e38b1-106">Use a dynamic resource if you want the parameter metric to update automatically while the application runs; otherwise use a static resource.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e38b1-107">Recursos dinâmicos têm a palavra-chave *chave* acrescentado ao nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="e38b1-107">Dynamic resources have the keyword *Key* appended to the property name.</span></span>  
  
 <span data-ttu-id="e38b1-108">O exemplo a seguir mostra como acessar e usar recursos dinâmicos de parâmetros de sistema para estilizar ou personalizar um botão.</span><span class="sxs-lookup"><span data-stu-id="e38b1-108">The following example shows how to access and use system parameter dynamic resources to style or customize a button.</span></span> <span data-ttu-id="e38b1-109">Isso [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] exemplo dimensiona um botão atribuindo <xref:System.Windows.SystemParameters> valores para a largura e a altura do botão.</span><span class="sxs-lookup"><span data-stu-id="e38b1-109">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example sizes a button by assigning <xref:System.Windows.SystemParameters> values to the button's width and height.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e38b1-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e38b1-110">Example</span></span>  
 [!code-xaml[SystemRes_snip#ParameterDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## <a name="see-also"></a><span data-ttu-id="e38b1-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e38b1-111">See Also</span></span>  
 [<span data-ttu-id="e38b1-112">Pintar uma área com um pincel de sistema</span><span class="sxs-lookup"><span data-stu-id="e38b1-112">Paint an Area with a System Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [<span data-ttu-id="e38b1-113">Usar SystemFonts</span><span class="sxs-lookup"><span data-stu-id="e38b1-113">Use SystemFonts</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)  
 [<span data-ttu-id="e38b1-114">Usar SystemParameters</span><span class="sxs-lookup"><span data-stu-id="e38b1-114">Use SystemParameters</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)
