---
title: 'Como: Usar chaves de parâmetros do sistema'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemParameters class
- classes [WPF], SystemParameters
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
ms.openlocfilehash: edacb4b98ab01f081f668dc3374f6588492210d9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918379"
---
# <a name="how-to-use-system-parameters-keys"></a><span data-ttu-id="c91c1-102">Como: Usar chaves de parâmetros do sistema</span><span class="sxs-lookup"><span data-stu-id="c91c1-102">How to: Use System Parameters Keys</span></span>
<span data-ttu-id="c91c1-103">Os recursos do sistema expõem inúmeras métricas do sistema como recursos para ajudar os desenvolvedores a criar recursos visuais consistentes com as configurações do sistema.</span><span class="sxs-lookup"><span data-stu-id="c91c1-103">System resources expose a number of system metrics as resources to help developers create visuals that are consistent with system settings.</span></span> <span data-ttu-id="c91c1-104"><xref:System.Windows.SystemParameters>é uma classe que contém os valores de parâmetro do sistema e as chaves de recurso que se associam aos <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> valores <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>— por exemplo, e.</span><span class="sxs-lookup"><span data-stu-id="c91c1-104"><xref:System.Windows.SystemParameters> is a class that contains both system parameter values and resource keys that bind to the values—for example, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> and <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>.</span></span> <span data-ttu-id="c91c1-105">As métricas de parâmetro do sistema podem ser usadas como recursos estáticos ou dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="c91c1-105">System parameter metrics can be used as either static or dynamic resources.</span></span> <span data-ttu-id="c91c1-106">Use um recurso dinâmico se desejar que a métrica de parâmetro seja atualizada automaticamente enquanto o aplicativo for executado; caso contrário, use um recurso estático.</span><span class="sxs-lookup"><span data-stu-id="c91c1-106">Use a dynamic resource if you want the parameter metric to update automatically while the application runs; otherwise use a static resource.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c91c1-107">Os recursos dinâmicos têm a *tecla* keyword anexada ao nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="c91c1-107">Dynamic resources have the keyword *Key* appended to the property name.</span></span>  
  
 <span data-ttu-id="c91c1-108">O exemplo a seguir mostra como acessar e usar recursos dinâmicos de parâmetros do sistema para estilizar ou personalizar um botão.</span><span class="sxs-lookup"><span data-stu-id="c91c1-108">The following example shows how to access and use system parameter dynamic resources to style or customize a button.</span></span> <span data-ttu-id="c91c1-109">Este [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] exemplo dimensiona um botão <xref:System.Windows.SystemParameters> atribuindo valores à largura e à altura do botão.</span><span class="sxs-lookup"><span data-stu-id="c91c1-109">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example sizes a button by assigning <xref:System.Windows.SystemParameters> values to the button's width and height.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c91c1-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c91c1-110">Example</span></span>  
 [!code-xaml[SystemRes_snip#ParameterDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## <a name="see-also"></a><span data-ttu-id="c91c1-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c91c1-111">See also</span></span>

- [<span data-ttu-id="c91c1-112">Pintar uma área com um pincel de sistema</span><span class="sxs-lookup"><span data-stu-id="c91c1-112">Paint an Area with a System Brush</span></span>](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="c91c1-113">Usar SystemFonts</span><span class="sxs-lookup"><span data-stu-id="c91c1-113">Use SystemFonts</span></span>](how-to-use-systemfonts.md)
- [<span data-ttu-id="c91c1-114">Usar SystemParameters</span><span class="sxs-lookup"><span data-stu-id="c91c1-114">Use SystemParameters</span></span>](how-to-use-systemparameters.md)
