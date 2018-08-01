---
title: Nomenclatura de recursos
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], localized resources
- localization, naming guidelines
- resource names
- global applications, naming guidelines
- international applications, naming guidelines
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b7cfda4e6a340d040de02903b9b64f0339751c5c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571180"
---
# <a name="naming-resources"></a><span data-ttu-id="e61d7-102">Nomenclatura de recursos</span><span class="sxs-lookup"><span data-stu-id="e61d7-102">Naming Resources</span></span>
<span data-ttu-id="e61d7-103">Como recursos localizáveis podem ser referenciados por meio de determinados objetos, como se fossem propriedades, as diretrizes de nomeação para os recursos são semelhantes às diretrizes de propriedade.</span><span class="sxs-lookup"><span data-stu-id="e61d7-103">Because localizable resources can be referenced via certain objects as if they were properties, the naming guidelines for resources are similar to property guidelines.</span></span>  
  
 <span data-ttu-id="e61d7-104">**✓ DO** usar PascalCasing em chaves de recurso.</span><span class="sxs-lookup"><span data-stu-id="e61d7-104">**✓ DO** use PascalCasing in resource keys.</span></span>  
  
 <span data-ttu-id="e61d7-105">**✓ DO** fornecer descritivo em vez de identificadores curtos.</span><span class="sxs-lookup"><span data-stu-id="e61d7-105">**✓ DO** provide descriptive rather than short identifiers.</span></span>  
  
 <span data-ttu-id="e61d7-106">**X DO NOT** usar palavras-chave das linguagens CLR principais.</span><span class="sxs-lookup"><span data-stu-id="e61d7-106">**X DO NOT** use language-specific keywords of the main CLR languages.</span></span>  
  
 <span data-ttu-id="e61d7-107">**✓ DO** use somente caracteres alfanuméricos e sublinhados em nomes de recursos.</span><span class="sxs-lookup"><span data-stu-id="e61d7-107">**✓ DO** use only alphanumeric characters and underscores in naming resources.</span></span>  
  
 <span data-ttu-id="e61d7-108">**✓ DO** usam a seguinte convenção de nomenclatura para os recursos de mensagem de exceção.</span><span class="sxs-lookup"><span data-stu-id="e61d7-108">**✓ DO** use the following naming convention for exception message resources.</span></span>  
  
 <span data-ttu-id="e61d7-109">O identificador de recurso deve ser o nome do tipo de exceção mais um identificador curto da exceção:</span><span class="sxs-lookup"><span data-stu-id="e61d7-109">The resource identifier should be the exception type name plus a short identifier of the exception:</span></span>  
  
 `ArgumentExceptionIllegalCharacters`  
 `ArgumentExceptionInvalidName`  
 `ArgumentExceptionFileNameIsMalformed`  
  
 <span data-ttu-id="e61d7-110">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="e61d7-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="e61d7-111">*Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="e61d7-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e61d7-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e61d7-112">See Also</span></span>  
 [<span data-ttu-id="e61d7-113">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="e61d7-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="e61d7-114">Diretrizes de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="e61d7-114">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
