---
ms.openlocfilehash: 480cbdecd681408a7e1d6fa366e3f1a4b131ab42
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857470"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a><span data-ttu-id="6cb1b-101">Categorias do padrão Unicode versão 8.0 agora são compatíveis</span><span class="sxs-lookup"><span data-stu-id="6cb1b-101">Unicode standard version 8.0 categories now supported</span></span>

|   |   |
|---|---|
|<span data-ttu-id="6cb1b-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="6cb1b-102">Details</span></span>|<span data-ttu-id="6cb1b-103">No .NET Framework 4.6.2, os dados Unicode foram atualizados do Unicode Standard versão 6.3 para a versão 8.0.</span><span class="sxs-lookup"><span data-stu-id="6cb1b-103">In .NET Framework 4.6.2, Unicode data has been upgraded from Unicode Standard version 6.3 to version 8.0.</span></span>  <span data-ttu-id="6cb1b-104">Ao solicitar a categorias de caracteres Unicode no .NET Framework 4.6.2, alguns resultados poderão não corresponder aos resultados nas versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6cb1b-104">When requesting Unicode character categories in .NET Framework 4.6.2, some results might not match the results in previous .NET Framework versions.</span></span>  <span data-ttu-id="6cb1b-105">Essa alteração afeta principalmente as sílabas Cheroqui, bem como os símbolos vocálicos e as marcas de tom Tai Lue Novo.</span><span class="sxs-lookup"><span data-stu-id="6cb1b-105">This change mostly affects Cherokee syllables and New Tai Lue vowels signs and tone marks.</span></span>|
|<span data-ttu-id="6cb1b-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="6cb1b-106">Suggestion</span></span>|<span data-ttu-id="6cb1b-107">Examine o código e remova ou altere a lógica que depende de categorias de caractere Unicode embutido em código.</span><span class="sxs-lookup"><span data-stu-id="6cb1b-107">Review code and remove/change logic that depends on hard-coded Unicode character categories.</span></span>|
|<span data-ttu-id="6cb1b-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="6cb1b-108">Scope</span></span>|<span data-ttu-id="6cb1b-109">Secundário</span><span class="sxs-lookup"><span data-stu-id="6cb1b-109">Minor</span></span>|
|<span data-ttu-id="6cb1b-110">Versão</span><span class="sxs-lookup"><span data-stu-id="6cb1b-110">Version</span></span>|<span data-ttu-id="6cb1b-111">4.6.2</span><span class="sxs-lookup"><span data-stu-id="6cb1b-111">4.6.2</span></span>|
|<span data-ttu-id="6cb1b-112">Tipo</span><span class="sxs-lookup"><span data-stu-id="6cb1b-112">Type</span></span>|<span data-ttu-id="6cb1b-113">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="6cb1b-113">Runtime</span></span>|
|<span data-ttu-id="6cb1b-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="6cb1b-114">Affected APIs</span></span>|<ul><li><xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|

