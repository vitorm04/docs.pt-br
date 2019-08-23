---
title: 'Como: Usar chaves de fontes do sistema'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemFonts class
ms.assetid: 036ebea7-5677-4f60-8ba4-56c9f9d9b8bd
ms.openlocfilehash: 7283e4225b75909322fa312583e9f1a0679762e2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918380"
---
# <a name="how-to-use-system-fonts-keys"></a><span data-ttu-id="2acf3-102">Como: Usar chaves de fontes do sistema</span><span class="sxs-lookup"><span data-stu-id="2acf3-102">How to: Use System Fonts Keys</span></span>
<span data-ttu-id="2acf3-103">Os recursos do sistema expõem inúmeras métricas do sistema como recursos para ajudar os desenvolvedores a criar recursos visuais consistentes com as configurações do sistema.</span><span class="sxs-lookup"><span data-stu-id="2acf3-103">System resources expose a number of system metrics as resources to help developers create visuals that are consistent with system settings.</span></span> <span data-ttu-id="2acf3-104"><xref:System.Windows.SystemFonts>é uma classe que contém valores de fontes do sistema e recursos de fontes do sistema que se associam aos valores <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> — <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>por exemplo, e.</span><span class="sxs-lookup"><span data-stu-id="2acf3-104"><xref:System.Windows.SystemFonts> is a class that contains both system font values and system font resources that bind to the values—for example, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> and <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>.</span></span>  
  
 <span data-ttu-id="2acf3-105">As métricas de fonte do sistema podem ser usadas como recursos estáticos ou dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="2acf3-105">System font metrics can be used as either static or dynamic resources.</span></span> <span data-ttu-id="2acf3-106">Use um recurso dinâmico se desejar que a métrica da fonte seja atualizada automaticamente enquanto o aplicativo é executado; caso contrário, use um recurso estático.</span><span class="sxs-lookup"><span data-stu-id="2acf3-106">Use a dynamic resource if you want the font metric to update automatically while the application runs; otherwise use a static resource.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2acf3-107">Os recursos dinâmicos têm a *tecla* keyword anexada ao nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="2acf3-107">Dynamic resources have the keyword *Key* appended to the property name.</span></span>  
  
 <span data-ttu-id="2acf3-108">O exemplo a seguir mostra como acessar e usar recursos dinâmicos de fonte do sistema para estilizar ou personalizar um botão.</span><span class="sxs-lookup"><span data-stu-id="2acf3-108">The following example shows how to access and use system font dynamic resources to style or customize a button.</span></span> <span data-ttu-id="2acf3-109">Este [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] exemplo cria um estilo de botão que <xref:System.Windows.SystemFonts> atribui valores a um botão.</span><span class="sxs-lookup"><span data-stu-id="2acf3-109">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example creates a button style that assigns <xref:System.Windows.SystemFonts> values to a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2acf3-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2acf3-110">Example</span></span>  
 [!code-xaml[SystemRes_snip#FontDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## <a name="see-also"></a><span data-ttu-id="2acf3-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2acf3-111">See also</span></span>

- [<span data-ttu-id="2acf3-112">Pintar uma área com um pincel de sistema</span><span class="sxs-lookup"><span data-stu-id="2acf3-112">Paint an Area with a System Brush</span></span>](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="2acf3-113">Usar SystemParameters</span><span class="sxs-lookup"><span data-stu-id="2acf3-113">Use SystemParameters</span></span>](how-to-use-systemparameters.md)
- [<span data-ttu-id="2acf3-114">Usar SystemFonts</span><span class="sxs-lookup"><span data-stu-id="2acf3-114">Use SystemFonts</span></span>](how-to-use-systemfonts.md)
