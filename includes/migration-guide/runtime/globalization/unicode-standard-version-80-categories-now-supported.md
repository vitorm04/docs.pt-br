---
ms.openlocfilehash: 480cbdecd681408a7e1d6fa366e3f1a4b131ab42
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760607"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a><span data-ttu-id="6d73c-101">Categorias do padrão Unicode versão 8.0 agora são compatíveis</span><span class="sxs-lookup"><span data-stu-id="6d73c-101">Unicode standard version 8.0 categories now supported</span></span>

|   |   |
|---|---|
|<span data-ttu-id="6d73c-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="6d73c-102">Details</span></span>|<span data-ttu-id="6d73c-103">No .NET Framework 4.6.2, os dados Unicode foram atualizados do Unicode Standard versão 6.3 para a versão 8.0.</span><span class="sxs-lookup"><span data-stu-id="6d73c-103">In .NET Framework 4.6.2, Unicode data has been upgraded from Unicode Standard version 6.3 to version 8.0.</span></span>  <span data-ttu-id="6d73c-104">Ao solicitar a categorias de caracteres Unicode no .NET Framework 4.6.2, alguns resultados poderão não corresponder aos resultados nas versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6d73c-104">When requesting Unicode character categories in .NET Framework 4.6.2, some results might not match the results in previous .NET Framework versions.</span></span>  <span data-ttu-id="6d73c-105">Essa alteração afeta principalmente as sílabas Cheroqui, bem como os símbolos vocálicos e as marcas de tom Tai Lue Novo.</span><span class="sxs-lookup"><span data-stu-id="6d73c-105">This change mostly affects Cherokee syllables and New Tai Lue vowels signs and tone marks.</span></span>|
|<span data-ttu-id="6d73c-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="6d73c-106">Suggestion</span></span>|<span data-ttu-id="6d73c-107">Examine o código e remova ou altere a lógica que depende de categorias de caractere Unicode embutido em código.</span><span class="sxs-lookup"><span data-stu-id="6d73c-107">Review code and remove/change logic that depends on hard-coded Unicode character categories.</span></span>|
|<span data-ttu-id="6d73c-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="6d73c-108">Scope</span></span>|<span data-ttu-id="6d73c-109">Secundário</span><span class="sxs-lookup"><span data-stu-id="6d73c-109">Minor</span></span>|
|<span data-ttu-id="6d73c-110">Versão</span><span class="sxs-lookup"><span data-stu-id="6d73c-110">Version</span></span>|<span data-ttu-id="6d73c-111">4.6.2</span><span class="sxs-lookup"><span data-stu-id="6d73c-111">4.6.2</span></span>|
|<span data-ttu-id="6d73c-112">Tipo</span><span class="sxs-lookup"><span data-stu-id="6d73c-112">Type</span></span>|<span data-ttu-id="6d73c-113">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="6d73c-113">Runtime</span></span>|
|<span data-ttu-id="6d73c-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="6d73c-114">Affected APIs</span></span>|<ul><li><xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|

