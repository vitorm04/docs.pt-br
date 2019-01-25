---
title: 'Como: Usar chaves de fontes do sistema'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemFonts class
ms.assetid: 036ebea7-5677-4f60-8ba4-56c9f9d9b8bd
ms.openlocfilehash: aec3ba8b84836d068b7efcfe53b34b126334b8de
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628702"
---
# <a name="how-to-use-system-fonts-keys"></a><span data-ttu-id="03a70-102">Como: Usar chaves de fontes do sistema</span><span class="sxs-lookup"><span data-stu-id="03a70-102">How to: Use System Fonts Keys</span></span>
<span data-ttu-id="03a70-103">Os recursos do sistema expõem inúmeras métricas do sistema como recursos para ajudar os desenvolvedores a criar recursos visuais consistentes com as configurações do sistema.</span><span class="sxs-lookup"><span data-stu-id="03a70-103">System resources expose a number of system metrics as resources to help developers create visuals that are consistent with system settings.</span></span> <span data-ttu-id="03a70-104"><xref:System.Windows.SystemFonts> é uma classe que contém valores de fonte e recursos de fonte de sistema que se associam aos valores — por exemplo, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> e <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="03a70-104"><xref:System.Windows.SystemFonts> is a class that contains both system font values and system font resources that bind to the values—for example, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> and <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>.</span></span>  
  
 <span data-ttu-id="03a70-105">As métricas de fonte do sistema podem ser usadas como recursos estáticos ou dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="03a70-105">System font metrics can be used as either static or dynamic resources.</span></span> <span data-ttu-id="03a70-106">Use um recurso dinâmico se desejar que a métrica da fonte seja atualizada automaticamente enquanto o aplicativo é executado; caso contrário, use um recurso estático.</span><span class="sxs-lookup"><span data-stu-id="03a70-106">Use a dynamic resource if you want the font metric to update automatically while the application runs; otherwise use a static resource.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="03a70-107">Recursos dinâmicos têm a palavra-chave *chave* acrescentado ao nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="03a70-107">Dynamic resources have the keyword *Key* appended to the property name.</span></span>  
  
 <span data-ttu-id="03a70-108">O exemplo a seguir mostra como acessar e usar recursos dinâmicos de fonte do sistema para estilizar ou personalizar um botão.</span><span class="sxs-lookup"><span data-stu-id="03a70-108">The following example shows how to access and use system font dynamic resources to style or customize a button.</span></span> <span data-ttu-id="03a70-109">Isso [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] exemplo cria um estilo de botão que atribui <xref:System.Windows.SystemFonts> valores a um botão.</span><span class="sxs-lookup"><span data-stu-id="03a70-109">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example creates a button style that assigns <xref:System.Windows.SystemFonts> values to a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03a70-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="03a70-110">Example</span></span>  
 [!code-xaml[SystemRes_snip#FontDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## <a name="see-also"></a><span data-ttu-id="03a70-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="03a70-111">See also</span></span>
- [<span data-ttu-id="03a70-112">Pintar uma área com um pincel de sistema</span><span class="sxs-lookup"><span data-stu-id="03a70-112">Paint an Area with a System Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="03a70-113">Usar SystemParameters</span><span class="sxs-lookup"><span data-stu-id="03a70-113">Use SystemParameters</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)
- [<span data-ttu-id="03a70-114">Usar SystemFonts</span><span class="sxs-lookup"><span data-stu-id="03a70-114">Use SystemFonts</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)
