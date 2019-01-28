---
title: Revisão de localização
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- world-ready applications, localizability
- application development [.NET Framework], localization
- localizability [.NET Framework]
- international applications [.NET Framework], localizability
- globalization [.NET Framework], localizability
- culture, localizability
- localization [.NET Framework], localizability
- global applications, localizability
- localizing resources
ms.assetid: 3aee2fbb-de47-4e37-8fe4-ddebb9719247
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a4c205d61e6de3e835954e405cece143520b4d2c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54623971"
---
# <a name="localizability-review"></a><span data-ttu-id="14645-102">Revisão de localização</span><span class="sxs-lookup"><span data-stu-id="14645-102">Localizability Review</span></span>
<span data-ttu-id="14645-103">A revisão de localização é uma etapa intermediária no desenvolvimento de um aplicativo pronto para o mundo.</span><span class="sxs-lookup"><span data-stu-id="14645-103">The localizability review is an intermediate step in the development of a world-ready application.</span></span> <span data-ttu-id="14645-104">Ela verifica se um aplicativo globalizado está pronto para a localização e identifica qualquer código ou aspecto da interface do usuário que exija tratamento especial.</span><span class="sxs-lookup"><span data-stu-id="14645-104">It verifies that a globalized application is ready for localization and identifies any code or any aspects of the user interface that require special handling.</span></span> <span data-ttu-id="14645-105">Esta etapa também ajuda a garantir que o processo de localização não apresente qualquer defeito funcionais em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="14645-105">This step also helps ensure that the localization process will not introduce any functional defects into your application.</span></span> <span data-ttu-id="14645-106">Quando todos os problemas levantados pela revisão de localização forem resolvidos, o aplicativo estará pronto para a localização.</span><span class="sxs-lookup"><span data-stu-id="14645-106">When all the issues raised by the localizability review have been addressed, your application is ready for localization.</span></span> <span data-ttu-id="14645-107">Se a revisão de localização estiver concluída, você não precisará modificar qualquer código-fonte durante o processo de localização.</span><span class="sxs-lookup"><span data-stu-id="14645-107">If the localizability review is thorough, you should not have to modify any source code during the localization process.</span></span>  
  
 <span data-ttu-id="14645-108">A revisão de localização é composta pelas três verificações a seguir:</span><span class="sxs-lookup"><span data-stu-id="14645-108">The localizability review consists of the following three checks:</span></span>  
  
-   [<span data-ttu-id="14645-109">As recomendações de globalização foram implementadas?</span><span class="sxs-lookup"><span data-stu-id="14645-109">Are the globalization recommendations implemented?</span></span>](#global)  
  
-   [<span data-ttu-id="14645-110">Os recursos sensíveis à cultura foram tratados corretamente?</span><span class="sxs-lookup"><span data-stu-id="14645-110">Are culture-sensitive features handled correctly?</span></span>](#culture)  
  
-   [<span data-ttu-id="14645-111">Você testou seu aplicativo com dados internacionais?</span><span class="sxs-lookup"><span data-stu-id="14645-111">Have you tested your application with international data?</span></span>](#test)  
  
<a name="global"></a>   
## <a name="implementing-globalization-recommendations"></a><span data-ttu-id="14645-112">Implementando recomendações de globalização</span><span class="sxs-lookup"><span data-stu-id="14645-112">Implementing globalization recommendations</span></span>  
 <span data-ttu-id="14645-113">Se você tiver projetado e desenvolvido seu aplicativo com a localização em mente, e se tiver seguido as recomendações discutidas no artigo [Globalização](../../../docs/standard/globalization-localization/globalization.md), a revisão de localização será essencialmente uma aprovação da garantia de qualidade.</span><span class="sxs-lookup"><span data-stu-id="14645-113">If you have designed and developed your application with localization in mind, and if you have followed the recommendations discussed in the [Globalization](../../../docs/standard/globalization-localization/globalization.md) article, the localizability review will largely be a quality assurance pass.</span></span> <span data-ttu-id="14645-114">Caso contrário, durante esse estágio, examine e implemente as recomendações para [globalização](../../../docs/standard/globalization-localization/globalization.md) e corrija os erros no código-fonte que impedem a localização.</span><span class="sxs-lookup"><span data-stu-id="14645-114">Otherwise, during this stage you should review and implement the recommendations for [globalization](../../../docs/standard/globalization-localization/globalization.md), and fix the errors in source code that prevent localization.</span></span>  
  
<a name="culture"></a>   
## <a name="handling-culture-sensitive-features"></a><span data-ttu-id="14645-115">Tratando Recursos Sensíveis à Cultura</span><span class="sxs-lookup"><span data-stu-id="14645-115">Handling culture-sensitive features</span></span>  
 <span data-ttu-id="14645-116">O .NET Framework não dá suporte de programação em várias áreas que podem variar amplamente com a cultura.</span><span class="sxs-lookup"><span data-stu-id="14645-116">The .NET Framework does not provide programmatic support in a number of areas that vary widely by culture.</span></span> <span data-ttu-id="14645-117">Na maioria dos casos, você deve escrever um código personalizado para lidar com áreas de recurso como as seguintes:</span><span class="sxs-lookup"><span data-stu-id="14645-117">In most cases, you have to write custom code to handle feature areas like the following:</span></span>  
  
-   <span data-ttu-id="14645-118">Endereços.</span><span class="sxs-lookup"><span data-stu-id="14645-118">Addresses.</span></span>  
  
-   <span data-ttu-id="14645-119">Números de telefone.</span><span class="sxs-lookup"><span data-stu-id="14645-119">Telephone numbers.</span></span>  
  
-   <span data-ttu-id="14645-120">Tamanhos de papel.</span><span class="sxs-lookup"><span data-stu-id="14645-120">Paper sizes.</span></span>  
  
-   <span data-ttu-id="14645-121">Unidades de medida usadas para comprimentos, pesos, área, volume e temperaturas.</span><span class="sxs-lookup"><span data-stu-id="14645-121">Units of measure used for lengths, weights, area, volume, and temperatures.</span></span> <span data-ttu-id="14645-122">Embora o .NET Framework não ofereça suporte interno para conversão de unidades de medida, você pode usar a propriedade <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> para determinar se um certo país ou região usa o sistema métrico, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="14645-122">Although the .NET Framework does not offer built-in support for converting between units of measure, you can use the <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> property to determine whether a particular country or region uses the metric system, as the following example illustrates.</span></span>  
  
     [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
     [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]  
  
<a name="test"></a>   
## <a name="testing-your-application"></a><span data-ttu-id="14645-123">Testando o aplicativo</span><span class="sxs-lookup"><span data-stu-id="14645-123">Testing your application</span></span>  
 <span data-ttu-id="14645-124">Antes de localizar seu aplicativo, você deve testá-lo usando dados internacionais em versões internacionais do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="14645-124">Before you localize your application, you should test it by using international data on international versions of the operating system.</span></span> <span data-ttu-id="14645-125">Apesar de grande parte da interface do usuário não estar localizada neste ponto, você será capaz de detectar problemas, como os seguintes:</span><span class="sxs-lookup"><span data-stu-id="14645-125">Although most of the user interface will not be localized at this point, you will be able to detect problems such as the following:</span></span>  
  
-   <span data-ttu-id="14645-126">Os dados serializados que não desserializam corretamente entre as versões do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="14645-126">Serialized data that does not deserialize correctly across operating system versions.</span></span>  
  
-   <span data-ttu-id="14645-127">Os dados numéricos que não refletem as convenções da cultura atual.</span><span class="sxs-lookup"><span data-stu-id="14645-127">Numeric data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="14645-128">Por exemplo, os números poderão ser exibidos com separadores de grupo imprecisos, separadores decimais ou símbolos de moeda.</span><span class="sxs-lookup"><span data-stu-id="14645-128">For example, numbers may be displayed with inaccurate group separators, decimal separators, or currency symbols.</span></span>  
  
-   <span data-ttu-id="14645-129">Dados de data e hora que não refletem as convenções da cultura atual.</span><span class="sxs-lookup"><span data-stu-id="14645-129">Date and time data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="14645-130">Por exemplo, números que representam o mês e o dia podem aparecer na ordem errada, separadores de data podem estar incorretos ou informações de fuso horário podem estar incorretas.</span><span class="sxs-lookup"><span data-stu-id="14645-130">For example, numbers that represent the month and day may appear in the wrong order, date separators may be incorrect, or time zone information may be incorrect.</span></span>  
  
-   <span data-ttu-id="14645-131">Os recursos que não podem ser encontrados porque você não identificou uma cultura padrão para o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="14645-131">Resources that cannot be found because you have not identified a default culture for your application.</span></span>  
  
-   <span data-ttu-id="14645-132">As cadeias de caracteres que são exibidas em uma ordem incomum para a cultura específica.</span><span class="sxs-lookup"><span data-stu-id="14645-132">Strings that are displayed in an unusual order for the specific culture.</span></span>  
  
-   <span data-ttu-id="14645-133">As comparações de cadeia de caracteres ou comparações de igualdade que retornam resultados inesperados.</span><span class="sxs-lookup"><span data-stu-id="14645-133">String comparisons or comparisons for equality that return unexpected results.</span></span>  
  
 <span data-ttu-id="14645-134">Se você tiver seguido as recomendações de globalização ao desenvolver seu aplicativo, sendo tratadas corretamente, tratado os recursos sensíveis à cultura e identificado e resolvido os problemas de localização que surgiram durante o teste, você poderá prosseguir para a próxima etapa, [Localização](../../../docs/standard/globalization-localization/localization.md).</span><span class="sxs-lookup"><span data-stu-id="14645-134">If you've followed the globalization recommendations when developing your application, handled culture-sensitive features correctly, and identified and addressed the localization issues that arose during testing, you can proceed to the next step, [Localization](../../../docs/standard/globalization-localization/localization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14645-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="14645-135">See also</span></span>

- [<span data-ttu-id="14645-136">Globalização e localização</span><span class="sxs-lookup"><span data-stu-id="14645-136">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)
- [<span data-ttu-id="14645-137">Localização</span><span class="sxs-lookup"><span data-stu-id="14645-137">Localization</span></span>](../../../docs/standard/globalization-localization/localization.md)
- [<span data-ttu-id="14645-138">Globalização</span><span class="sxs-lookup"><span data-stu-id="14645-138">Globalization</span></span>](../../../docs/standard/globalization-localization/globalization.md)
- [<span data-ttu-id="14645-139">Recursos em aplicativos de área de trabalho</span><span class="sxs-lookup"><span data-stu-id="14645-139">Resources in Desktop Apps</span></span>](../../../docs/framework/resources/index.md)
