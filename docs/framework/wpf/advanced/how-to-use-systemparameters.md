---
title: 'Como: Usar SystemParameters'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes [WPF], SystemParameters
ms.assetid: 02e7a5de-94eb-4953-b91c-52e6c872ad5b
ms.openlocfilehash: 344fb54b48bcbf188b36a29d8205c21deff713c4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62001449"
---
# <a name="how-to-use-systemparameters"></a><span data-ttu-id="c6cf4-102">Como: Usar SystemParameters</span><span class="sxs-lookup"><span data-stu-id="c6cf4-102">How to: Use SystemParameters</span></span>
<span data-ttu-id="c6cf4-103">Este exemplo mostra como acessar e usar as propriedades de <xref:System.Windows.SystemParameters> para estilizar ou personalizar um botão.</span><span class="sxs-lookup"><span data-stu-id="c6cf4-103">This example shows how to access and use the properties of <xref:System.Windows.SystemParameters> in order to style or customize a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6cf4-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c6cf4-104">Example</span></span>  
 <span data-ttu-id="c6cf4-105">Os recursos do sistema expõem várias configurações baseadas no sistema como recursos para ajudá-lo a criar recursos visuais consistentes com as configurações do sistema.</span><span class="sxs-lookup"><span data-stu-id="c6cf4-105">System resources expose several system based settings as resources in order to help you create visuals that are consistent with system settings.</span></span> <span data-ttu-id="c6cf4-106"><xref:System.Windows.SystemParameters> é uma classe que contém propriedades de valor de parâmetro do sistema e as chaves associadas aos valores.</span><span class="sxs-lookup"><span data-stu-id="c6cf4-106"><xref:System.Windows.SystemParameters> is a class that contains both system parameter value properties, and resource keys that bind to the values.</span></span> <span data-ttu-id="c6cf4-107">Por exemplo, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> é um <xref:System.Windows.SystemParameters> o valor da propriedade e <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A> é a chave de recurso correspondente.</span><span class="sxs-lookup"><span data-stu-id="c6cf4-107">For example, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> is a <xref:System.Windows.SystemParameters> property value and <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A> is the corresponding resource key.</span></span>  
  
 <span data-ttu-id="c6cf4-108">Na [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você pode usar os membros de <xref:System.Windows.SystemParameters> como uso de uma propriedade estática ou uma referência de recurso dinâmico (com o valor da propriedade estática como a chave).</span><span class="sxs-lookup"><span data-stu-id="c6cf4-108">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can use the members of <xref:System.Windows.SystemParameters> as either a static property usage, or a dynamic resource references (with the static property value as the key).</span></span> <span data-ttu-id="c6cf4-109">Use uma referência de recurso dinâmico se desejar que o valor baseado no sistema seja atualizado automaticamente enquanto o aplicativo é executado; caso contrário, use uma referência estática.</span><span class="sxs-lookup"><span data-stu-id="c6cf4-109">Use a dynamic resource reference if you want the system based value to update automatically while the application runs; otherwise, use a static reference.</span></span> <span data-ttu-id="c6cf4-110">Chaves de recurso têm o sufixo `Key` acrescentado ao nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="c6cf4-110">Resource keys have the suffix `Key` appended to the property name.</span></span>  
  
 <span data-ttu-id="c6cf4-111">O exemplo a seguir mostra como acessar e usar os valores estáticos de <xref:System.Windows.SystemParameters> para estilizar ou personalizar um botão.</span><span class="sxs-lookup"><span data-stu-id="c6cf4-111">The following example shows how to access and use the static values of <xref:System.Windows.SystemParameters> to style or customize a button.</span></span> <span data-ttu-id="c6cf4-112">Este exemplo de marcação dimensiona um botão aplicando <xref:System.Windows.SystemParameters> valores a um botão.</span><span class="sxs-lookup"><span data-stu-id="c6cf4-112">This markup example sizes a button by applying <xref:System.Windows.SystemParameters> values to a button.</span></span>  
  
 [!code-xaml[SystemRes_snip#ParameterStaticResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#parameterstaticresources)]  
  
 <span data-ttu-id="c6cf4-113">Para usar os valores de <xref:System.Windows.SystemParameters> no código, você não precisa usar referências estáticas ou referências a recursos dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="c6cf4-113">To use the values of <xref:System.Windows.SystemParameters> in code, you do not have to use either static references or dynamic resource references.</span></span> <span data-ttu-id="c6cf4-114">Em vez disso, use os valores da <xref:System.Windows.SystemParameters> classe.</span><span class="sxs-lookup"><span data-stu-id="c6cf4-114">Instead, use the values of the <xref:System.Windows.SystemParameters> class.</span></span> <span data-ttu-id="c6cf4-115">Embora as propriedades não chave sejam aparentemente definidas como propriedades estáticas, o comportamento de tempo de execução de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] como hospedado pelo sistema será reavaliar as propriedades em tempo real e responderá adequadamente para alterações controlada pelo usuário para valores do sistema.</span><span class="sxs-lookup"><span data-stu-id="c6cf4-115">Although the non-key properties are apparently defined as static properties, the runtime behavior of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] as hosted by the system will reevaluate the properties in realtime, and will properly account for user-driven changes to system values.</span></span> <span data-ttu-id="c6cf4-116">O exemplo a seguir mostra como definir a largura e altura de um botão usando <xref:System.Windows.SystemParameters> valores.</span><span class="sxs-lookup"><span data-stu-id="c6cf4-116">The following example shows how to set the width and height of a button by using <xref:System.Windows.SystemParameters> values.</span></span>  
  
 [!code-csharp[SystemRes_snip#ParameterResourcesCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#parameterresourcescode)]
 [!code-vb[SystemRes_snip#ParameterResourcesCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#parameterresourcescode)]  
  
## <a name="see-also"></a><span data-ttu-id="c6cf4-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6cf4-117">See also</span></span>

- <xref:System.Windows.SystemParameters>
- [<span data-ttu-id="c6cf4-118">Pintar uma área com um pincel de sistema</span><span class="sxs-lookup"><span data-stu-id="c6cf4-118">Paint an Area with a System Brush</span></span>](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="c6cf4-119">Usar SystemFonts</span><span class="sxs-lookup"><span data-stu-id="c6cf4-119">Use SystemFonts</span></span>](how-to-use-systemfonts.md)
- [<span data-ttu-id="c6cf4-120">Usar chaves de parâmetros do sistema</span><span class="sxs-lookup"><span data-stu-id="c6cf4-120">Use System Parameters Keys</span></span>](how-to-use-system-parameters-keys.md)
- [<span data-ttu-id="c6cf4-121">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="c6cf4-121">How-to Topics</span></span>](resources-how-to-topics.md)
