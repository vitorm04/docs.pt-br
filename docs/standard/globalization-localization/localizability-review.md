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
ms.openlocfilehash: ef23cff2416792f13fda04dbe9beb34cbacfd7ea
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288271"
---
# <a name="localizability-review"></a><span data-ttu-id="f52a8-102">Revisão de localização</span><span class="sxs-lookup"><span data-stu-id="f52a8-102">Localizability review</span></span>

<span data-ttu-id="f52a8-103">A revisão de localização é uma etapa intermediária no desenvolvimento de um aplicativo pronto para o mundo.</span><span class="sxs-lookup"><span data-stu-id="f52a8-103">The localizability review is an intermediate step in the development of a world-ready application.</span></span> <span data-ttu-id="f52a8-104">Ela verifica se um aplicativo globalizado está pronto para a localização e identifica qualquer código ou aspecto da interface do usuário que exija tratamento especial.</span><span class="sxs-lookup"><span data-stu-id="f52a8-104">It verifies that a globalized application is ready for localization and identifies any code or any aspects of the user interface that require special handling.</span></span> <span data-ttu-id="f52a8-105">Esta etapa também ajuda a garantir que o processo de localização não apresente qualquer defeito funcionais em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f52a8-105">This step also helps ensure that the localization process will not introduce any functional defects into your application.</span></span> <span data-ttu-id="f52a8-106">Quando todos os problemas levantados pela revisão de localização forem resolvidos, o aplicativo estará pronto para a localização.</span><span class="sxs-lookup"><span data-stu-id="f52a8-106">When all the issues raised by the localizability review have been addressed, your application is ready for localization.</span></span> <span data-ttu-id="f52a8-107">Se a revisão de localização estiver concluída, você não precisará modificar qualquer código-fonte durante o processo de localização.</span><span class="sxs-lookup"><span data-stu-id="f52a8-107">If the localizability review is thorough, you should not have to modify any source code during the localization process.</span></span>

<span data-ttu-id="f52a8-108">A revisão de localização é composta pelas três verificações a seguir:</span><span class="sxs-lookup"><span data-stu-id="f52a8-108">The localizability review consists of the following three checks:</span></span>

- [<span data-ttu-id="f52a8-109">As recomendações de globalização foram implementadas?</span><span class="sxs-lookup"><span data-stu-id="f52a8-109">Are the globalization recommendations implemented?</span></span>](#global)

- [<span data-ttu-id="f52a8-110">Os recursos sensíveis à cultura foram tratados corretamente?</span><span class="sxs-lookup"><span data-stu-id="f52a8-110">Are culture-sensitive features handled correctly?</span></span>](#culture)

- [<span data-ttu-id="f52a8-111">Você testou seu aplicativo com dados internacionais?</span><span class="sxs-lookup"><span data-stu-id="f52a8-111">Have you tested your application with international data?</span></span>](#test)

<a name="global"></a>
## <a name="implement-globalization-recommendations"></a><span data-ttu-id="f52a8-112">Implementar as recomendações de globalização</span><span class="sxs-lookup"><span data-stu-id="f52a8-112">Implement globalization recommendations</span></span>

<span data-ttu-id="f52a8-113">Se você tiver projetado e desenvolvido seu aplicativo com a localização em mente, e se tiver seguido as recomendações discutidas no artigo [Globalização](globalization.md), a revisão de localização será essencialmente uma aprovação da garantia de qualidade.</span><span class="sxs-lookup"><span data-stu-id="f52a8-113">If you have designed and developed your application with localization in mind, and if you have followed the recommendations discussed in the [Globalization](globalization.md) article, the localizability review will largely be a quality assurance pass.</span></span> <span data-ttu-id="f52a8-114">Caso contrário, durante este estágio, examine e implemente as recomendações de [globalização](globalization.md) e corrija os erros no código-fonte que impedem a localização.</span><span class="sxs-lookup"><span data-stu-id="f52a8-114">Otherwise, during this stage you should review and implement the recommendations for [globalization](globalization.md) and fix the errors in source code that prevent localization.</span></span>

<a name="culture"></a>
## <a name="handle-culture-sensitive-features"></a><span data-ttu-id="f52a8-115">Lidar com recursos com detecção de cultura</span><span class="sxs-lookup"><span data-stu-id="f52a8-115">Handle culture-sensitive features</span></span>

<span data-ttu-id="f52a8-116">O .NET não dá suporte de programação em várias áreas, que podem variar amplamente com a cultura.</span><span class="sxs-lookup"><span data-stu-id="f52a8-116">.NET does not provide programmatic support in a number of areas that vary widely by culture.</span></span> <span data-ttu-id="f52a8-117">Na maioria dos casos, você deve escrever um código personalizado para lidar com áreas de recurso como as seguintes:</span><span class="sxs-lookup"><span data-stu-id="f52a8-117">In most cases, you have to write custom code to handle feature areas like the following:</span></span>

- <span data-ttu-id="f52a8-118">Endereços</span><span class="sxs-lookup"><span data-stu-id="f52a8-118">Addresses</span></span>

- <span data-ttu-id="f52a8-119">Números de telefone</span><span class="sxs-lookup"><span data-stu-id="f52a8-119">Telephone numbers</span></span>

- <span data-ttu-id="f52a8-120">Tamanhos de papel</span><span class="sxs-lookup"><span data-stu-id="f52a8-120">Paper sizes</span></span>

- <span data-ttu-id="f52a8-121">Unidades de medida usadas para comprimentos, pesos, área, volume e temperaturas</span><span class="sxs-lookup"><span data-stu-id="f52a8-121">Units of measure used for lengths, weights, area, volume, and temperatures</span></span>

   <span data-ttu-id="f52a8-122">Embora o .NET não oferece suporte interno para conversão de unidades de medida, você pode usar a propriedade <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> para determinar se um certo país ou região usa o sistema métrico, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f52a8-122">Although .NET does not offer built-in support for converting between units of measure, you can use the <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> property to determine whether a particular country or region uses the metric system, as the following example illustrates.</span></span>

   [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
   [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]

<a name="test"></a>
## <a name="test-your-application"></a><span data-ttu-id="f52a8-123">Teste seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="f52a8-123">Test your application</span></span>

<span data-ttu-id="f52a8-124">Antes de localizar seu aplicativo, você deve testá-lo usando dados internacionais em versões internacionais do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="f52a8-124">Before you localize your application, you should test it by using international data on international versions of the operating system.</span></span> <span data-ttu-id="f52a8-125">Apesar de grande parte da interface do usuário não estar localizada neste ponto, você será capaz de detectar problemas, como os seguintes:</span><span class="sxs-lookup"><span data-stu-id="f52a8-125">Although most of the user interface will not be localized at this point, you will be able to detect problems such as the following:</span></span>

- <span data-ttu-id="f52a8-126">Os dados serializados que não desserializam corretamente entre as versões do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="f52a8-126">Serialized data that does not deserialize correctly across operating system versions.</span></span>

- <span data-ttu-id="f52a8-127">Os dados numéricos que não refletem as convenções da cultura atual.</span><span class="sxs-lookup"><span data-stu-id="f52a8-127">Numeric data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="f52a8-128">Por exemplo, os números poderão ser exibidos com separadores de grupo imprecisos, separadores decimais ou símbolos de moeda.</span><span class="sxs-lookup"><span data-stu-id="f52a8-128">For example, numbers may be displayed with inaccurate group separators, decimal separators, or currency symbols.</span></span>

- <span data-ttu-id="f52a8-129">Dados de data e hora que não refletem as convenções da cultura atual.</span><span class="sxs-lookup"><span data-stu-id="f52a8-129">Date and time data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="f52a8-130">Por exemplo, números que representam o mês e o dia podem aparecer na ordem errada, separadores de data podem estar incorretos ou informações de fuso horário podem estar incorretas.</span><span class="sxs-lookup"><span data-stu-id="f52a8-130">For example, numbers that represent the month and day may appear in the wrong order, date separators may be incorrect, or time zone information may be incorrect.</span></span>

- <span data-ttu-id="f52a8-131">Os recursos que não podem ser encontrados porque você não identificou uma cultura padrão para o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f52a8-131">Resources that cannot be found because you have not identified a default culture for your application.</span></span>

- <span data-ttu-id="f52a8-132">As cadeias de caracteres que são exibidas em uma ordem incomum para a cultura específica.</span><span class="sxs-lookup"><span data-stu-id="f52a8-132">Strings that are displayed in an unusual order for the specific culture.</span></span>

- <span data-ttu-id="f52a8-133">As comparações de cadeia de caracteres ou comparações de igualdade que retornam resultados inesperados.</span><span class="sxs-lookup"><span data-stu-id="f52a8-133">String comparisons or comparisons for equality that return unexpected results.</span></span>

<span data-ttu-id="f52a8-134">Se você tiver seguido as recomendações de globalização ao desenvolver seu aplicativo, sendo tratadas corretamente, tratado os recursos sensíveis à cultura e identificado e resolvido os problemas de localização que surgiram durante o teste, você poderá prosseguir para a próxima etapa, [Localização](localization.md).</span><span class="sxs-lookup"><span data-stu-id="f52a8-134">If you've followed the globalization recommendations when developing your application, handled culture-sensitive features correctly, and identified and addressed the localization issues that arose during testing, you can proceed to the next step, [Localization](localization.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f52a8-135">Veja também</span><span class="sxs-lookup"><span data-stu-id="f52a8-135">See also</span></span>

- [<span data-ttu-id="f52a8-136">Globalização e localização</span><span class="sxs-lookup"><span data-stu-id="f52a8-136">Globalization and Localization</span></span>](index.md)
- [<span data-ttu-id="f52a8-137">Localização</span><span class="sxs-lookup"><span data-stu-id="f52a8-137">Localization</span></span>](localization.md)
- [<span data-ttu-id="f52a8-138">Globalização</span><span class="sxs-lookup"><span data-stu-id="f52a8-138">Globalization</span></span>](globalization.md)
- [<span data-ttu-id="f52a8-139">Recursos em aplicativos da área de trabalho</span><span class="sxs-lookup"><span data-stu-id="f52a8-139">Resources in Desktop Apps</span></span>](../../framework/resources/index.md)
