---
title: Como usar chaves de fontes do sistema
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemFonts class
ms.assetid: 036ebea7-5677-4f60-8ba4-56c9f9d9b8bd
ms.openlocfilehash: c68f197daebd7423aa4ad2e7fdfb6e7f89c74ed0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544421"
---
# <a name="how-to-use-system-fonts-keys"></a><span data-ttu-id="349a0-102">Como usar chaves de fontes do sistema</span><span class="sxs-lookup"><span data-stu-id="349a0-102">How to: Use System Fonts Keys</span></span>
<span data-ttu-id="349a0-103">Os recursos do sistema expõem inúmeras métricas do sistema como recursos para ajudar os desenvolvedores a criar recursos visuais consistentes com as configurações do sistema.</span><span class="sxs-lookup"><span data-stu-id="349a0-103">System resources expose a number of system metrics as resources to help developers create visuals that are consistent with system settings.</span></span> <span data-ttu-id="349a0-104"><xref:System.Windows.SystemFonts> é uma classe que contém valores de fonte e os recursos de fonte do sistema que mapeiam para os valores — por exemplo, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> e <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="349a0-104"><xref:System.Windows.SystemFonts> is a class that contains both system font values and system font resources that bind to the values—for example, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> and <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>.</span></span>  
  
 <span data-ttu-id="349a0-105">As métricas de fonte do sistema podem ser usadas como recursos estáticos ou dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="349a0-105">System font metrics can be used as either static or dynamic resources.</span></span> <span data-ttu-id="349a0-106">Use um recurso dinâmico se desejar que a métrica da fonte seja atualizada automaticamente enquanto o aplicativo é executado; caso contrário, use um recurso estático.</span><span class="sxs-lookup"><span data-stu-id="349a0-106">Use a dynamic resource if you want the font metric to update automatically while the application runs; otherwise use a static resource.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="349a0-107">Recursos dinâmicos têm a palavra-chave *chave* acrescentado ao nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="349a0-107">Dynamic resources have the keyword *Key* appended to the property name.</span></span>  
  
 <span data-ttu-id="349a0-108">O exemplo a seguir mostra como acessar e usar recursos dinâmicos de fonte do sistema para estilizar ou personalizar um botão.</span><span class="sxs-lookup"><span data-stu-id="349a0-108">The following example shows how to access and use system font dynamic resources to style or customize a button.</span></span> <span data-ttu-id="349a0-109">Isso [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] exemplo cria um estilo de botão que atribui <xref:System.Windows.SystemFonts> valores a um botão.</span><span class="sxs-lookup"><span data-stu-id="349a0-109">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example creates a button style that assigns <xref:System.Windows.SystemFonts> values to a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="349a0-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="349a0-110">Example</span></span>  
 [!code-xaml[SystemRes_snip#FontDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## <a name="see-also"></a><span data-ttu-id="349a0-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="349a0-111">See Also</span></span>  
 [<span data-ttu-id="349a0-112">Pintar uma área com um pincel de sistema</span><span class="sxs-lookup"><span data-stu-id="349a0-112">Paint an Area with a System Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [<span data-ttu-id="349a0-113">Usar SystemParameters</span><span class="sxs-lookup"><span data-stu-id="349a0-113">Use SystemParameters</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)  
 [<span data-ttu-id="349a0-114">Usar SystemFonts</span><span class="sxs-lookup"><span data-stu-id="349a0-114">Use SystemFonts</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)
