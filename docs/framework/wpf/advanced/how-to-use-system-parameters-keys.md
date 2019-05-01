---
title: 'Como: Usar chaves de parâmetros do sistema'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemParameters class
- classes [WPF], SystemParameters
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
ms.openlocfilehash: 147f65b4bb214c12317309081c345251d7426cd6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62001436"
---
# <a name="how-to-use-system-parameters-keys"></a><span data-ttu-id="ca60f-102">Como: Usar chaves de parâmetros do sistema</span><span class="sxs-lookup"><span data-stu-id="ca60f-102">How to: Use System Parameters Keys</span></span>
<span data-ttu-id="ca60f-103">Os recursos do sistema expõem inúmeras métricas do sistema como recursos para ajudar os desenvolvedores a criar recursos visuais consistentes com as configurações do sistema.</span><span class="sxs-lookup"><span data-stu-id="ca60f-103">System resources expose a number of system metrics as resources to help developers create visuals that are consistent with system settings.</span></span> <span data-ttu-id="ca60f-104"><xref:System.Windows.SystemParameters> é uma classe que contém os valores de parâmetro do sistema e as chaves associadas aos valores — por exemplo, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> e <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="ca60f-104"><xref:System.Windows.SystemParameters> is a class that contains both system parameter values and resource keys that bind to the values—for example, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> and <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>.</span></span> <span data-ttu-id="ca60f-105">Métricas de parâmetro do sistema podem ser usadas como recursos estáticos ou dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="ca60f-105">System parameter metrics can be used as either static or dynamic resources.</span></span> <span data-ttu-id="ca60f-106">Use um recurso dinâmico se desejar que a métrica de parâmetro atualize automaticamente enquanto o aplicativo é executado; Caso contrário, use um recurso estático.</span><span class="sxs-lookup"><span data-stu-id="ca60f-106">Use a dynamic resource if you want the parameter metric to update automatically while the application runs; otherwise use a static resource.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ca60f-107">Recursos dinâmicos têm a palavra-chave *chave* acrescentado ao nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="ca60f-107">Dynamic resources have the keyword *Key* appended to the property name.</span></span>  
  
 <span data-ttu-id="ca60f-108">O exemplo a seguir mostra como acessar e usar recursos dinâmicos de parâmetros de sistema para estilizar ou personalizar um botão.</span><span class="sxs-lookup"><span data-stu-id="ca60f-108">The following example shows how to access and use system parameter dynamic resources to style or customize a button.</span></span> <span data-ttu-id="ca60f-109">Isso [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] exemplo dimensiona um botão atribuindo <xref:System.Windows.SystemParameters> valores para a largura e a altura do botão.</span><span class="sxs-lookup"><span data-stu-id="ca60f-109">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example sizes a button by assigning <xref:System.Windows.SystemParameters> values to the button's width and height.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca60f-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ca60f-110">Example</span></span>  
 [!code-xaml[SystemRes_snip#ParameterDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## <a name="see-also"></a><span data-ttu-id="ca60f-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ca60f-111">See also</span></span>

- [<span data-ttu-id="ca60f-112">Pintar uma área com um pincel de sistema</span><span class="sxs-lookup"><span data-stu-id="ca60f-112">Paint an Area with a System Brush</span></span>](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="ca60f-113">Usar SystemFonts</span><span class="sxs-lookup"><span data-stu-id="ca60f-113">Use SystemFonts</span></span>](how-to-use-systemfonts.md)
- [<span data-ttu-id="ca60f-114">Usar SystemParameters</span><span class="sxs-lookup"><span data-stu-id="ca60f-114">Use SystemParameters</span></span>](how-to-use-systemparameters.md)
