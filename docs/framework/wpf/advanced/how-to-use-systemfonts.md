---
title: Como usar SystemFonts
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- system fonts [WPF]
- fonts [WPF], system fonts
- classes [WPF], SystemFonts
ms.assetid: 3f46a4ec-2225-408a-8123-8838a8f7057a
ms.openlocfilehash: 305d0cf18db5dc96b2d3cde863cf4ba2ae8dbb96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-systemfonts"></a><span data-ttu-id="50398-102">Como usar SystemFonts</span><span class="sxs-lookup"><span data-stu-id="50398-102">How to: Use SystemFonts</span></span>
<span data-ttu-id="50398-103">Este exemplo mostra como usar os recursos estáticos do <xref:System.Windows.SystemFonts> classe para definir o estilo ou personalizar um botão.</span><span class="sxs-lookup"><span data-stu-id="50398-103">This example shows how to use the static resources of the <xref:System.Windows.SystemFonts> class in order to style or customize a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50398-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="50398-104">Example</span></span>  
 <span data-ttu-id="50398-105">Os recursos do sistema expõem vários valores determinados pelo sistema como recursos e propriedades para ajudar a criar recursos visuais consistentes com as configurações do sistema.</span><span class="sxs-lookup"><span data-stu-id="50398-105">System resources expose several system-determined values as both resources and properties in order to help you create visuals that are consistent with system settings.</span></span> <span data-ttu-id="50398-106"><xref:System.Windows.SystemFonts> é uma classe que contém os dois valores de fonte como propriedades estáticas e as propriedades que fazem referência a chaves de recurso que podem ser usadas para acessar esses valores dinamicamente em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="50398-106"><xref:System.Windows.SystemFonts> is a class that contains both system font values as static properties, and properties that reference resource keys that can be used to access those values dynamically at run time.</span></span> <span data-ttu-id="50398-107">Por exemplo, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> é um <xref:System.Windows.SystemFonts> valor, e <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> é uma chave de recurso correspondente.</span><span class="sxs-lookup"><span data-stu-id="50398-107">For example, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> is a <xref:System.Windows.SystemFonts> value, and <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> is a corresponding resource key.</span></span>  
  
 <span data-ttu-id="50398-108">Em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você pode usar os membros de <xref:System.Windows.SystemFonts> como propriedades estáticas ou referências a recursos dinâmicos (com o valor da propriedade estática como a chave).</span><span class="sxs-lookup"><span data-stu-id="50398-108">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can use the members of <xref:System.Windows.SystemFonts> as either static properties or dynamic resource references (with the static property value as the key).</span></span> <span data-ttu-id="50398-109">Use uma referência de recurso dinâmica se quiser que a métrica de fonte atualize automaticamente enquanto o aplicativo é executado; caso contrário, use uma referência estática ao valor.</span><span class="sxs-lookup"><span data-stu-id="50398-109">Use a dynamic resource reference if you want the font metric to automatically update while the application runs; otherwise, use a static value reference.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="50398-110">As chaves de recurso têm o sufixo “Chave” anexado ao nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="50398-110">The resource keys have the suffix "Key" appended to the property name.</span></span>  
  
 <span data-ttu-id="50398-111">O exemplo a seguir mostra como acessar e usar as propriedades de <xref:System.Windows.SystemFonts> como valores estáticos para estilizar ou personalizar um botão.</span><span class="sxs-lookup"><span data-stu-id="50398-111">The following example shows how to access and use the properties of <xref:System.Windows.SystemFonts> as static values in order to style or customize a button.</span></span> <span data-ttu-id="50398-112">Este exemplo de marcação atribui <xref:System.Windows.SystemFonts> valores a um botão.</span><span class="sxs-lookup"><span data-stu-id="50398-112">This markup example assigns <xref:System.Windows.SystemFonts> values to a button.</span></span>  
  
 [!code-xaml[SystemRes_snip#FontStaticResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#fontstaticresources)]  
  
 <span data-ttu-id="50398-113">Para usar os valores de <xref:System.Windows.SystemFonts> no código, você não precisa usar um valor estático ou uma referência de recurso dinâmico.</span><span class="sxs-lookup"><span data-stu-id="50398-113">To use the values of <xref:System.Windows.SystemFonts> in code, you do not have to use either a static value or a dynamic resource reference.</span></span> <span data-ttu-id="50398-114">Em vez disso, use as propriedades não-chave do <xref:System.Windows.SystemFonts> classe.</span><span class="sxs-lookup"><span data-stu-id="50398-114">Instead, use the non-key properties of the <xref:System.Windows.SystemFonts> class.</span></span> <span data-ttu-id="50398-115">Embora as propriedades não-chave sejam aparentemente definidas como propriedades estáticas, o comportamento de tempo de execução [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] como hospedado pelo sistema irá reavaliar as propriedades em tempo real e irá corretamente considerar para alterações de valores do sistema controlada pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="50398-115">Although the non-key properties are apparently defined as static properties, the run-time behavior of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] as hosted by the system will reevaluate the properties in real time and will properly account for user-driven changes to system values.</span></span> <span data-ttu-id="50398-116">O exemplo a seguir mostra como especificar as configurações de fonte de um botão.</span><span class="sxs-lookup"><span data-stu-id="50398-116">The following example shows how to specify the font settings of a button.</span></span>  
  
 [!code-csharp[SystemRes_snip#FontResourcesCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#fontresourcescode)]
 [!code-vb[SystemRes_snip#FontResourcesCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#fontresourcescode)]  
  
## <a name="see-also"></a><span data-ttu-id="50398-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="50398-117">See Also</span></span>  
 <xref:System.Windows.SystemFonts>  
 [<span data-ttu-id="50398-118">Pintar uma área com um pincel de sistema</span><span class="sxs-lookup"><span data-stu-id="50398-118">Paint an Area with a System Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [<span data-ttu-id="50398-119">Usar SystemParameters</span><span class="sxs-lookup"><span data-stu-id="50398-119">Use SystemParameters</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)  
 [<span data-ttu-id="50398-120">Usar chaves de fontes do sistema</span><span class="sxs-lookup"><span data-stu-id="50398-120">Use System Fonts Keys</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-system-fonts-keys.md)  
 [<span data-ttu-id="50398-121">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="50398-121">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)  
 [<span data-ttu-id="50398-122">Extensão de marcação x:Static</span><span class="sxs-lookup"><span data-stu-id="50398-122">x:Static Markup Extension</span></span>](../../../../docs/framework/xaml-services/x-static-markup-extension.md)  
 [<span data-ttu-id="50398-123">Recursos XAML</span><span class="sxs-lookup"><span data-stu-id="50398-123">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="50398-124">Extensão de marcação DynamicResource</span><span class="sxs-lookup"><span data-stu-id="50398-124">DynamicResource Markup Extension</span></span>](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)
