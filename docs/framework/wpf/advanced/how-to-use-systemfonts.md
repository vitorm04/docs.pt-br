---
title: 'Como: Usar SystemFonts'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- system fonts [WPF]
- fonts [WPF], system fonts
- classes [WPF], SystemFonts
ms.assetid: 3f46a4ec-2225-408a-8123-8838a8f7057a
ms.openlocfilehash: 7438705a82faee464649b5f6f577627a379e9a8c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918356"
---
# <a name="how-to-use-systemfonts"></a><span data-ttu-id="ae566-102">Como: Usar SystemFonts</span><span class="sxs-lookup"><span data-stu-id="ae566-102">How to: Use SystemFonts</span></span>
<span data-ttu-id="ae566-103">Este exemplo mostra como usar os recursos estáticos da <xref:System.Windows.SystemFonts> classe para estilizar ou personalizar um botão.</span><span class="sxs-lookup"><span data-stu-id="ae566-103">This example shows how to use the static resources of the <xref:System.Windows.SystemFonts> class in order to style or customize a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae566-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ae566-104">Example</span></span>  
 <span data-ttu-id="ae566-105">Os recursos do sistema expõem vários valores determinados pelo sistema como recursos e propriedades para ajudar a criar recursos visuais consistentes com as configurações do sistema.</span><span class="sxs-lookup"><span data-stu-id="ae566-105">System resources expose several system-determined values as both resources and properties in order to help you create visuals that are consistent with system settings.</span></span> <span data-ttu-id="ae566-106"><xref:System.Windows.SystemFonts>é uma classe que contém ambos os valores de fonte do sistema como propriedades estáticas e propriedades que fazem referência a chaves de recurso que podem ser usadas para acessar esses valores dinamicamente em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ae566-106"><xref:System.Windows.SystemFonts> is a class that contains both system font values as static properties, and properties that reference resource keys that can be used to access those values dynamically at run time.</span></span> <span data-ttu-id="ae566-107">Por exemplo, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> é um <xref:System.Windows.SystemFonts> valor e <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> é uma chave de recurso correspondente.</span><span class="sxs-lookup"><span data-stu-id="ae566-107">For example, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> is a <xref:System.Windows.SystemFonts> value, and <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> is a corresponding resource key.</span></span>  
  
 <span data-ttu-id="ae566-108">No [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você pode usar os membros de <xref:System.Windows.SystemFonts> como propriedades estáticas ou referências de recursos dinâmicos (com o valor da propriedade estática como a chave).</span><span class="sxs-lookup"><span data-stu-id="ae566-108">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can use the members of <xref:System.Windows.SystemFonts> as either static properties or dynamic resource references (with the static property value as the key).</span></span> <span data-ttu-id="ae566-109">Use uma referência de recurso dinâmica se quiser que a métrica de fonte atualize automaticamente enquanto o aplicativo é executado; caso contrário, use uma referência estática ao valor.</span><span class="sxs-lookup"><span data-stu-id="ae566-109">Use a dynamic resource reference if you want the font metric to automatically update while the application runs; otherwise, use a static value reference.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ae566-110">As chaves de recurso têm o sufixo “Chave” anexado ao nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="ae566-110">The resource keys have the suffix "Key" appended to the property name.</span></span>  
  
 <span data-ttu-id="ae566-111">O exemplo a seguir mostra como acessar e usar as propriedades de <xref:System.Windows.SystemFonts> como valores estáticos para estilizar ou personalizar um botão.</span><span class="sxs-lookup"><span data-stu-id="ae566-111">The following example shows how to access and use the properties of <xref:System.Windows.SystemFonts> as static values in order to style or customize a button.</span></span> <span data-ttu-id="ae566-112">Este exemplo de marcação atribui <xref:System.Windows.SystemFonts> valores a um botão.</span><span class="sxs-lookup"><span data-stu-id="ae566-112">This markup example assigns <xref:System.Windows.SystemFonts> values to a button.</span></span>  
  
 [!code-xaml[SystemRes_snip#FontStaticResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#fontstaticresources)]  
  
 <span data-ttu-id="ae566-113">Para usar os valores de <xref:System.Windows.SystemFonts> no código, você não precisa usar um valor estático ou uma referência de recurso dinâmico.</span><span class="sxs-lookup"><span data-stu-id="ae566-113">To use the values of <xref:System.Windows.SystemFonts> in code, you do not have to use either a static value or a dynamic resource reference.</span></span> <span data-ttu-id="ae566-114">Em vez disso, use as propriedades não chave da <xref:System.Windows.SystemFonts> classe.</span><span class="sxs-lookup"><span data-stu-id="ae566-114">Instead, use the non-key properties of the <xref:System.Windows.SystemFonts> class.</span></span> <span data-ttu-id="ae566-115">Embora as propriedades não chave sejam, aparentemente, definidas como propriedades estáticas, o comportamento de tempo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de execução do como hospedado pelo sistema reavaliará as propriedades em tempo real e irão considerar adequadamente as alterações controladas pelo usuário em valores do sistema.</span><span class="sxs-lookup"><span data-stu-id="ae566-115">Although the non-key properties are apparently defined as static properties, the run-time behavior of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] as hosted by the system will reevaluate the properties in real time and will properly account for user-driven changes to system values.</span></span> <span data-ttu-id="ae566-116">O exemplo a seguir mostra como especificar as configurações de fonte de um botão.</span><span class="sxs-lookup"><span data-stu-id="ae566-116">The following example shows how to specify the font settings of a button.</span></span>  
  
 [!code-csharp[SystemRes_snip#FontResourcesCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#fontresourcescode)]
 [!code-vb[SystemRes_snip#FontResourcesCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#fontresourcescode)]  
  
## <a name="see-also"></a><span data-ttu-id="ae566-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae566-117">See also</span></span>

- <xref:System.Windows.SystemFonts>
- [<span data-ttu-id="ae566-118">Pintar uma área com um pincel de sistema</span><span class="sxs-lookup"><span data-stu-id="ae566-118">Paint an Area with a System Brush</span></span>](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="ae566-119">Usar SystemParameters</span><span class="sxs-lookup"><span data-stu-id="ae566-119">Use SystemParameters</span></span>](how-to-use-systemparameters.md)
- [<span data-ttu-id="ae566-120">Usar chaves de fontes do sistema</span><span class="sxs-lookup"><span data-stu-id="ae566-120">Use System Fonts Keys</span></span>](how-to-use-system-fonts-keys.md)
- [<span data-ttu-id="ae566-121">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="ae566-121">How-to Topics</span></span>](resources-how-to-topics.md)
- [<span data-ttu-id="ae566-122">Extensão de marcação x:Static</span><span class="sxs-lookup"><span data-stu-id="ae566-122">x:Static Markup Extension</span></span>](../../xaml-services/x-static-markup-extension.md)
- [<span data-ttu-id="ae566-123">Recursos XAML</span><span class="sxs-lookup"><span data-stu-id="ae566-123">XAML Resources</span></span>](xaml-resources.md)
- [<span data-ttu-id="ae566-124">Extensão de marcação DynamicResource</span><span class="sxs-lookup"><span data-stu-id="ae566-124">DynamicResource Markup Extension</span></span>](dynamicresource-markup-extension.md)
