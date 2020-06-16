---
title: Recursos de nomenclatura
description: Examine as diretrizes de nomenclatura para recursos no .NET, que são semelhantes às diretrizes para nomear Propriedades.
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], localized resources
- localization, naming guidelines
- resource names
- global applications, naming guidelines
- international applications, naming guidelines
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
ms.openlocfilehash: 765337bcf9fad4f9a8c9272a15b5c77d02770471
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768242"
---
# <a name="naming-resources"></a><span data-ttu-id="495d4-103">Recursos de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="495d4-103">Naming Resources</span></span>
<span data-ttu-id="495d4-104">Como os recursos localizáveis podem ser referenciados por meio de determinados objetos como se fossem Propriedades, as diretrizes de nomenclatura para recursos são semelhantes às diretrizes de propriedade.</span><span class="sxs-lookup"><span data-stu-id="495d4-104">Because localizable resources can be referenced via certain objects as if they were properties, the naming guidelines for resources are similar to property guidelines.</span></span>

 <span data-ttu-id="495d4-105">✔️ usar PascalCasing em chaves de recurso.</span><span class="sxs-lookup"><span data-stu-id="495d4-105">✔️ DO use PascalCasing in resource keys.</span></span>

 <span data-ttu-id="495d4-106">✔️ fornecem identificadores descritivos, em vez de curtos.</span><span class="sxs-lookup"><span data-stu-id="495d4-106">✔️ DO provide descriptive rather than short identifiers.</span></span>

 <span data-ttu-id="495d4-107">❌Não use palavras-chave específicas de idioma das principais linguagens do CLR.</span><span class="sxs-lookup"><span data-stu-id="495d4-107">❌ DO NOT use language-specific keywords of the main CLR languages.</span></span>

 <span data-ttu-id="495d4-108">✔️ usar somente caracteres alfanuméricos e sublinhados na nomenclatura de recursos.</span><span class="sxs-lookup"><span data-stu-id="495d4-108">✔️ DO use only alphanumeric characters and underscores in naming resources.</span></span>

 <span data-ttu-id="495d4-109">✔️ Use a seguinte convenção de nomenclatura para recursos de mensagem de exceção.</span><span class="sxs-lookup"><span data-stu-id="495d4-109">✔️ DO use the following naming convention for exception message resources.</span></span>

 <span data-ttu-id="495d4-110">O identificador de recurso deve ser o nome do tipo de exceção, além de um identificador curto da exceção:</span><span class="sxs-lookup"><span data-stu-id="495d4-110">The resource identifier should be the exception type name plus a short identifier of the exception:</span></span>

 <span data-ttu-id="495d4-111">`ArgumentExceptionIllegalCharacters` `ArgumentExceptionInvalidName`</span><span class="sxs-lookup"><span data-stu-id="495d4-111">`ArgumentExceptionIllegalCharacters` `ArgumentExceptionInvalidName`</span></span>
 `ArgumentExceptionFileNameIsMalformed`

 <span data-ttu-id="495d4-112">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="495d4-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="495d4-113">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="495d4-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="495d4-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="495d4-114">See also</span></span>

- [<span data-ttu-id="495d4-115">Diretrizes de design de estrutura</span><span class="sxs-lookup"><span data-stu-id="495d4-115">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="495d4-116">Diretrizes de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="495d4-116">Naming Guidelines</span></span>](naming-guidelines.md)
