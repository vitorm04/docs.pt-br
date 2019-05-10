---
title: Globalizando e localizando aplicativos do .NET
ms.date: 06/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- international applications [.NET]
- globalization [.NET], encoding
- global applications
- internationalization
- world-ready applications
- application development [.NET], globalization
- multilingual application development
ms.assetid: 9a59696b-d89b-45bd-946d-c75da4732d02
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 501e23656b3a31dc14e0b2213252ef52c598140f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622636"
---
# <a name="globalizing-and-localizing-net-applications"></a><span data-ttu-id="a0547-102">Globalizando e localizando aplicativos do .NET</span><span class="sxs-lookup"><span data-stu-id="a0547-102">Globalizing and localizing .NET applications</span></span>

<span data-ttu-id="a0547-103">O desenvolvimento de um aplicativo que possa ser usado em todo o mundo, incluindo ser localizado em um ou mais idiomas, envolve três etapas: a globalização, a análise da possibilidade de localização e a localização em si.</span><span class="sxs-lookup"><span data-stu-id="a0547-103">Developing a world-ready application, including an application that can be localized into one or more languages, involves three steps: globalization, localizability review, and localization.</span></span>

[<span data-ttu-id="a0547-104">Globalização</span><span class="sxs-lookup"><span data-stu-id="a0547-104">Globalization</span></span>](globalization.md)

<span data-ttu-id="a0547-105">Esta etapa envolve a criação e a codificação de um aplicativo que seja independente de cultura e idioma, bem como que ofereça suporte a interfaces de usuário localizadas e dados regionais para todos os usuários.</span><span class="sxs-lookup"><span data-stu-id="a0547-105">This step involves designing and coding an application that is culture-neutral and language-neutral, and that supports localized user interfaces and regional data for all users.</span></span> <span data-ttu-id="a0547-106">Ela envolve a tomada de decisões de design e de programação que não sejam baseadas em suposições para culturas específicas.</span><span class="sxs-lookup"><span data-stu-id="a0547-106">It involves making design and programming decisions that are not based on culture-specific assumptions.</span></span> <span data-ttu-id="a0547-107">Mesmo quando um aplicativo globalizado não está localizado, ele foi criado e escrito para que possa ser localizado posteriormente em um ou mais idiomas com relativa facilidade.</span><span class="sxs-lookup"><span data-stu-id="a0547-107">While a globalized application is not localized, it nevertheless is designed and written so that it can be subsequently localized into one or more languages with relative ease.</span></span>

[<span data-ttu-id="a0547-108">Análise de possibilidade de localização</span><span class="sxs-lookup"><span data-stu-id="a0547-108">Localizability review</span></span>](localizability-review.md)

<span data-ttu-id="a0547-109">Essa etapa envolve a verificação do código e do design de um aplicativo para garantir que ele possa ser facilmente localizado e para identificar potenciais obstáculos à localização, bem como verificar se o código executável do aplicativo está separado de seus recursos.</span><span class="sxs-lookup"><span data-stu-id="a0547-109">This step involves reviewing an application's code and design to ensure that it can be localized easily and to identify potential roadblocks for localization, and verifying that the application's executable code is separated from its resources.</span></span> <span data-ttu-id="a0547-110">Se a fase de globalização foi eficaz, a análise de capacidade de localização confirmará as opções de design e codificação feitas durante a globalização.</span><span class="sxs-lookup"><span data-stu-id="a0547-110">If the globalization stage was effective, the localizability review will confirm the design and coding choices made during globalization.</span></span> <span data-ttu-id="a0547-111">O estágio de localizabilidade também pode identificar todos os problemas restantes para que o código-fonte do aplicativo não precise ser modificado durante o estágio de localização.</span><span class="sxs-lookup"><span data-stu-id="a0547-111">The localizability stage may also identify any remaining issues so that an application's source code doesn't have to be modified during the localization stage.</span></span>

[<span data-ttu-id="a0547-112">Localização</span><span class="sxs-lookup"><span data-stu-id="a0547-112">Localization</span></span>](localization.md)

<span data-ttu-id="a0547-113">Essa etapa envolve a personalização de um aplicativo para culturas ou regiões específicas.</span><span class="sxs-lookup"><span data-stu-id="a0547-113">This step involves customizing an application for specific cultures or regions.</span></span> <span data-ttu-id="a0547-114">Se as etapas de globalização e localizabilidade tiverem sido feitas corretamente, a localização consistirá principalmente na tradução da interface de usuário.</span><span class="sxs-lookup"><span data-stu-id="a0547-114">If the globalization and localizability steps have been performed correctly, localization consists primarily of translating the user interface.</span></span>

<span data-ttu-id="a0547-115">Seguir estas três etapas oferece duas vantagens:</span><span class="sxs-lookup"><span data-stu-id="a0547-115">Following these three steps provides two advantages:</span></span>

- <span data-ttu-id="a0547-116">Libera você de ter que readaptar um aplicativo projetado para uma única cultura, como inglês dos EUA, para oferecer suporte a culturas adicionais.</span><span class="sxs-lookup"><span data-stu-id="a0547-116">It frees you from having to retrofit an application that is designed to support a single culture, such as U.S. English, to support additional cultures.</span></span>

- <span data-ttu-id="a0547-117">Isso resulta em aplicativos localizados que são mais estáveis e possuem menos bugs.</span><span class="sxs-lookup"><span data-stu-id="a0547-117">It results in localized applications that are more stable and have fewer bugs.</span></span>

<span data-ttu-id="a0547-118">O .NET fornece suporte abrangente ao desenvolvimento de aplicativos preparados para o mundo e localizados.</span><span class="sxs-lookup"><span data-stu-id="a0547-118">.NET provides extensive support for the development of world-ready and localized applications.</span></span> <span data-ttu-id="a0547-119">Em particular, muitos membros de tipos na biblioteca de classes do .NET auxiliam na globalização ao retornarem valores que refletem as convenções da cultura do usuário atual ou de uma cultura específica.</span><span class="sxs-lookup"><span data-stu-id="a0547-119">In particular, many type members in the .NET class library aid globalization by returning values that reflect the conventions of either the current user's culture or a specified culture.</span></span> <span data-ttu-id="a0547-120">Além disso, o .NET Framework dá suporte a assemblies satélites que facilitam o processo de localizar um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a0547-120">Also, .NET supports satellite assemblies, which facilitate the process of localizing an application.</span></span>

<span data-ttu-id="a0547-121">Confira mais informações na [Documentação de globalização](/globalization/).</span><span class="sxs-lookup"><span data-stu-id="a0547-121">For additional information, see the [Globalization documentation](/globalization/).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="a0547-122">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="a0547-122">In this section</span></span>

[<span data-ttu-id="a0547-123">Globalização</span><span class="sxs-lookup"><span data-stu-id="a0547-123">Globalization</span></span>](globalization.md)

<span data-ttu-id="a0547-124">Discute o primeiro estágio da criação de um aplicativo pronto para o mundo, o que envolve o projeto e a codificação de um aplicativo independente de cultura e idioma.</span><span class="sxs-lookup"><span data-stu-id="a0547-124">Discusses the first stage of creating a world-ready application, which involves designing and coding an application that is culture-neutral and language-neutral.</span></span>

[<span data-ttu-id="a0547-125">Análise de possibilidade de localização</span><span class="sxs-lookup"><span data-stu-id="a0547-125">Localizability review</span></span>](localizability-review.md)

<span data-ttu-id="a0547-126">Discute o segundo estágio da criação de um aplicativo localizado, o que envolve a identificação de obstáculos potenciais à localização.</span><span class="sxs-lookup"><span data-stu-id="a0547-126">Discusses the second stage of creating a localized application, which involves identifying potential roadblocks to localization.</span></span>

[<span data-ttu-id="a0547-127">Localização</span><span class="sxs-lookup"><span data-stu-id="a0547-127">Localization</span></span>](localization.md)

<span data-ttu-id="a0547-128">Discute o estágio final da criação de um aplicativo localizado, o que envolve a personalização da interface de usuário de um aplicativo para regiões ou culturas específicas.</span><span class="sxs-lookup"><span data-stu-id="a0547-128">Discusses the final stage of creating a localized application, which involves customizing an application's user interface for specific regions or cultures.</span></span>

[<span data-ttu-id="a0547-129">Operações de cadeia de caracteres sem diferenciação de cultura</span><span class="sxs-lookup"><span data-stu-id="a0547-129">Culture-insensitive string operations</span></span>](culture-insensitive-string-operations.md)

<span data-ttu-id="a0547-130">Descreve como usar métodos e classes do .NET sensíveis a culturas por padrão para obter resultados sem diferenciação de cultura.</span><span class="sxs-lookup"><span data-stu-id="a0547-130">Describes how to use .NET methods and classes that are culture-sensitive by default to obtain culture-insensitive results.</span></span>

[<span data-ttu-id="a0547-131">Práticas recomendadas para o desenvolvimento de aplicativos prontos para o mundo</span><span class="sxs-lookup"><span data-stu-id="a0547-131">Best practices for developing world-ready applications</span></span>](best-practices-for-developing-world-ready-apps.md)

<span data-ttu-id="a0547-132">Descreve as práticas recomendadas a serem seguidas para globalização, localização e desenvolvimento de aplicativos ASP.NET prontos para o mundo.</span><span class="sxs-lookup"><span data-stu-id="a0547-132">Describes the best practices to follow for globalization, localization, and developing world-ready ASP.NET applications.</span></span>

## <a name="reference"></a><span data-ttu-id="a0547-133">Referência</span><span class="sxs-lookup"><span data-stu-id="a0547-133">Reference</span></span>

- <span data-ttu-id="a0547-134">Namespace <xref:System.Globalization?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="a0547-134"><xref:System.Globalization?displayProperty=nameWithType> namespace</span></span>

   <span data-ttu-id="a0547-135">Contém classes que definem informações relacionadas à cultura, incluindo idioma, país/região, calendários em uso, padrões de formato para datas, moeda, números e ordem de classificação para cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a0547-135">Contains classes that define culture-related information, including the language, the country/region, the calendars in use, the format patterns for dates, currency, and numbers, and the sort order for strings.</span></span>

- <span data-ttu-id="a0547-136">Namespace <xref:System.Resources></span><span class="sxs-lookup"><span data-stu-id="a0547-136"><xref:System.Resources> namespace</span></span>

   <span data-ttu-id="a0547-137">Fornece classes para a criação, manipulação e utilização de recursos.</span><span class="sxs-lookup"><span data-stu-id="a0547-137">Provides classes for creating, manipulating, and using resources.</span></span>

- <span data-ttu-id="a0547-138">Namespace <xref:System.Text></span><span class="sxs-lookup"><span data-stu-id="a0547-138"><xref:System.Text> namespace</span></span>

   <span data-ttu-id="a0547-139">Contém classes que representam ASCII, ANSI, Unicode e outras codificações de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a0547-139">Contains classes representing ASCII, ANSI, Unicode, and other character encodings.</span></span>

- [<span data-ttu-id="a0547-140">Resgen.exe (Gerador de Arquivo de Recurso)</span><span class="sxs-lookup"><span data-stu-id="a0547-140">Resgen.exe (Resource File Generator)</span></span>](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)

   <span data-ttu-id="a0547-141">Descreve como usar Resgen.exe para converter arquivos .txt e XML (.resx) para arquivos .resources binários do Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="a0547-141">Describes how to use Resgen.exe to convert .txt files and XML-based resource format (.resx) files to common language runtime binary .resources files.</span></span>

- [<span data-ttu-id="a0547-142">Winres.exe (Editor de Recursos do Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="a0547-142">Winres.exe (Windows Forms Resource Editor)</span></span>](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md)

   <span data-ttu-id="a0547-143">Descreve como usar Winres.exe para localizar formulários do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a0547-143">Describes how to use Winres.exe to localize Windows Forms forms.</span></span>
