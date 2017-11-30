---
title: "Revisão de localização"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7633c7fe9e99bde96ee108460e983eff48f1c7f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="localizability-review"></a><span data-ttu-id="931ae-102">Revisão de localização</span><span class="sxs-lookup"><span data-stu-id="931ae-102">Localizability Review</span></span>
<span data-ttu-id="931ae-103">A revisão de localização é uma etapa intermediária no desenvolvimento de um aplicativo preparado para o mundo.</span><span class="sxs-lookup"><span data-stu-id="931ae-103">The localizability review is an intermediate step in the development of a world-ready application.</span></span> <span data-ttu-id="931ae-104">Ele verifica se um aplicativo globalizado está pronto para a localização e identifica qualquer código ou qualquer aspectos da interface do usuário que requerem tratamento especial.</span><span class="sxs-lookup"><span data-stu-id="931ae-104">It verifies that a globalized application is ready for localization and identifies any code or any aspects of the user interface that require special handling.</span></span> <span data-ttu-id="931ae-105">Esta etapa também ajuda a garantir que o processo de localização não apresentará qualquer funcionais defeitos em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="931ae-105">This step also helps ensure that the localization process will not introduce any functional defects into your application.</span></span> <span data-ttu-id="931ae-106">Quando todos os problemas gerados pela revisão de localização foram resolvidos, o aplicativo está pronto para localização.</span><span class="sxs-lookup"><span data-stu-id="931ae-106">When all the issues raised by the localizability review have been addressed, your application is ready for localization.</span></span> <span data-ttu-id="931ae-107">Se a revisão de localização estiver completa, você não deve ter que modificar qualquer código de origem durante o processo de localização.</span><span class="sxs-lookup"><span data-stu-id="931ae-107">If the localizability review is thorough, you should not have to modify any source code during the localization process.</span></span>  
  
 <span data-ttu-id="931ae-108">A revisão de localização consiste as seguintes verificações de três:</span><span class="sxs-lookup"><span data-stu-id="931ae-108">The localizability review consists of the following three checks:</span></span>  
  
-   [<span data-ttu-id="931ae-109">As recomendações de globalização são implementadas?</span><span class="sxs-lookup"><span data-stu-id="931ae-109">Are the globalization recommendations implemented?</span></span>](#global)  
  
-   [<span data-ttu-id="931ae-110">Recursos de cultura são tratados corretamente?</span><span class="sxs-lookup"><span data-stu-id="931ae-110">Are culture-sensitive features handled correctly?</span></span>](#culture)  
  
-   [<span data-ttu-id="931ae-111">Teste seu aplicativo com dados internacionais?</span><span class="sxs-lookup"><span data-stu-id="931ae-111">Have you tested your application with international data?</span></span>](#test)  
  
<a name="global"></a>   
## <a name="implementing-globalization-recommendations"></a><span data-ttu-id="931ae-112">Implementando recomendações de globalização</span><span class="sxs-lookup"><span data-stu-id="931ae-112">Implementing globalization recommendations</span></span>  
 <span data-ttu-id="931ae-113">Se você tiver criado e desenvolvido seu aplicativo com a localização em mente e se você tiver seguido as recomendações discutido no [globalização](../../../docs/standard/globalization-localization/globalization.md) artigo, a revisão de localização será amplamente uma passagem de garantia de qualidade .</span><span class="sxs-lookup"><span data-stu-id="931ae-113">If you have designed and developed your application with localization in mind, and if you have followed the recommendations discussed in the [Globalization](../../../docs/standard/globalization-localization/globalization.md) article, the localizability review will largely be a quality assurance pass.</span></span> <span data-ttu-id="931ae-114">Caso contrário, durante esse estágio Examine e implementar as recomendações para [globalização](../../../docs/standard/globalization-localization/globalization.md)e corrija os erros que impedem a localização no código-fonte.</span><span class="sxs-lookup"><span data-stu-id="931ae-114">Otherwise, during this stage you should review and implement the recommendations for [globalization](../../../docs/standard/globalization-localization/globalization.md), and fix the errors in source code that prevent localization.</span></span>  
  
<a name="culture"></a>   
## <a name="handling-culture-sensitive-features"></a><span data-ttu-id="931ae-115">Tratando Recursos Sensíveis à Cultura</span><span class="sxs-lookup"><span data-stu-id="931ae-115">Handling culture-sensitive features</span></span>  
 <span data-ttu-id="931ae-116">O .NET Framework não dá suporte em um número de áreas que podem variar amplamente pela cultura.</span><span class="sxs-lookup"><span data-stu-id="931ae-116">The .NET Framework does not provide programmatic support in a number of areas that vary widely by culture.</span></span> <span data-ttu-id="931ae-117">Na maioria dos casos, você deve escrever código personalizado para lidar com áreas de recurso com o seguinte:</span><span class="sxs-lookup"><span data-stu-id="931ae-117">In most cases, you have to write custom code to handle feature areas like the following:</span></span>  
  
-   <span data-ttu-id="931ae-118">Endereços.</span><span class="sxs-lookup"><span data-stu-id="931ae-118">Addresses.</span></span>  
  
-   <span data-ttu-id="931ae-119">Números de telefone.</span><span class="sxs-lookup"><span data-stu-id="931ae-119">Telephone numbers.</span></span>  
  
-   <span data-ttu-id="931ae-120">Tamanhos de papel.</span><span class="sxs-lookup"><span data-stu-id="931ae-120">Paper sizes.</span></span>  
  
-   <span data-ttu-id="931ae-121">Unidades de medida usado para comprimentos, pesos, área, volume e temperaturas.</span><span class="sxs-lookup"><span data-stu-id="931ae-121">Units of measure used for lengths, weights, area, volume, and temperatures.</span></span> <span data-ttu-id="931ae-122">Embora o .NET Framework não oferece suporte interno para converter entre unidades de medida, você pode usar o <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> para determinar se um determinado país ou região usa o sistema métrico, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="931ae-122">Although the .NET Framework does not offer built-in support for converting between units of measure, you can use the <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> property to determine whether a particular country or region uses the metric system, as the following example illustrates.</span></span>  
  
     [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
     [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]  
  
<a name="test"></a>   
## <a name="testing-your-application"></a><span data-ttu-id="931ae-123">Testando o aplicativo</span><span class="sxs-lookup"><span data-stu-id="931ae-123">Testing your application</span></span>  
 <span data-ttu-id="931ae-124">Antes de você localiza o aplicativo, você deve testá-lo usando dados internacionais em versões internacionais do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="931ae-124">Before you localize your application, you should test it by using international data on international versions of the operating system.</span></span> <span data-ttu-id="931ae-125">Embora a maioria da interface do usuário não será localizada neste ponto, você será capaz de detectar problemas, como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="931ae-125">Although most of the user interface will not be localized at this point, you will be able to detect problems such as the following:</span></span>  
  
-   <span data-ttu-id="931ae-126">Dados serializados não desserializar corretamente nas versões do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="931ae-126">Serialized data that does not deserialize correctly across operating system versions.</span></span>  
  
-   <span data-ttu-id="931ae-127">Dados numéricos que não refletem as convenções da cultura atual.</span><span class="sxs-lookup"><span data-stu-id="931ae-127">Numeric data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="931ae-128">Por exemplo, os números poderão ser exibidos com separadores de grupo precisas, separadores decimais ou símbolos de moeda.</span><span class="sxs-lookup"><span data-stu-id="931ae-128">For example, numbers may be displayed with inaccurate group separators, decimal separators, or currency symbols.</span></span>  
  
-   <span data-ttu-id="931ae-129">Dados de data e hora que não refletem as convenções da cultura atual.</span><span class="sxs-lookup"><span data-stu-id="931ae-129">Date and time data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="931ae-130">Por exemplo, números que representam o mês e dia podem aparecer na ordem errada, separadores de data podem estar incorretos ou informações de fuso horário podem estar incorretas.</span><span class="sxs-lookup"><span data-stu-id="931ae-130">For example, numbers that represent the month and day may appear in the wrong order, date separators may be incorrect, or time zone information may be incorrect.</span></span>  
  
-   <span data-ttu-id="931ae-131">Recursos que não podem ser encontrados porque não identificou uma cultura padrão para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="931ae-131">Resources that cannot be found because you have not identified a default culture for your application.</span></span>  
  
-   <span data-ttu-id="931ae-132">Cadeias de caracteres que são exibidas em uma ordem incomum para a cultura específica.</span><span class="sxs-lookup"><span data-stu-id="931ae-132">Strings that are displayed in an unusual order for the specific culture.</span></span>  
  
-   <span data-ttu-id="931ae-133">Comparações de igualdade que retornam resultados inesperados ou de comparações de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="931ae-133">String comparisons or comparisons for equality that return unexpected results.</span></span>  
  
 <span data-ttu-id="931ae-134">Se você tiver seguido as recomendações de globalização ao desenvolver seu aplicativo, sendo tratadas corretamente, os recursos de cultura e identificados e resolvidos os problemas de localização que ocorreu durante o teste, você pode prosseguir para a próxima etapa, [Localização](../../../docs/standard/globalization-localization/localization.md).</span><span class="sxs-lookup"><span data-stu-id="931ae-134">If you've followed the globalization recommendations when developing your application, handled culture-sensitive features correctly, and identified and addressed the localization issues that arose during testing, you can proceed to the next step, [Localization](../../../docs/standard/globalization-localization/localization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="931ae-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="931ae-135">See Also</span></span>  
 [<span data-ttu-id="931ae-136">Globalização e localização</span><span class="sxs-lookup"><span data-stu-id="931ae-136">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)  
 [<span data-ttu-id="931ae-137">Localização</span><span class="sxs-lookup"><span data-stu-id="931ae-137">Localization</span></span>](../../../docs/standard/globalization-localization/localization.md)  
 [<span data-ttu-id="931ae-138">Globalização</span><span class="sxs-lookup"><span data-stu-id="931ae-138">Globalization</span></span>](../../../docs/standard/globalization-localization/globalization.md)  
 [<span data-ttu-id="931ae-139">Recursos em aplicativos de área de trabalho</span><span class="sxs-lookup"><span data-stu-id="931ae-139">Resources in Desktop Apps</span></span>](../../../docs/framework/resources/index.md)
