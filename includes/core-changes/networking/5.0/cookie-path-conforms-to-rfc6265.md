---
ms.openlocfilehash: 7140f6d4cac063088b3663ab98d292104218b542
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465501"
---
### <a name="cookie-path-handling-now-conforms-to-rfc-6265"></a><span data-ttu-id="c807a-101">O tratamento de caminho de cookie agora está em conformidade com RFC 6265</span><span class="sxs-lookup"><span data-stu-id="c807a-101">Cookie Path handling now conforms to RFC 6265</span></span>

<span data-ttu-id="c807a-102">Os algoritmos de tratamento de caminho definidos no [RFC 6265](https://tools.ietf.org/html/rfc6265) foram implementados para as <xref:System.Net.Cookie> <xref:System.Net.CookieContainer> classes e.</span><span class="sxs-lookup"><span data-stu-id="c807a-102">Path-handling algorithms defined in [RFC 6265](https://tools.ietf.org/html/rfc6265) were implemented for the <xref:System.Net.Cookie> and <xref:System.Net.CookieContainer> classes.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c807a-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="c807a-103">Version introduced</span></span>

<span data-ttu-id="c807a-104">5,0</span><span class="sxs-lookup"><span data-stu-id="c807a-104">5.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="c807a-105">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="c807a-105">Change description</span></span>

- <span data-ttu-id="c807a-106">A <xref:System.Net.Cookie.Path> propriedade não é mais necessária para ser um prefixo do caminho da solicitação.</span><span class="sxs-lookup"><span data-stu-id="c807a-106">The <xref:System.Net.Cookie.Path> property is no longer required to be a prefix of the request path.</span></span>
- <span data-ttu-id="c807a-107">O cálculo do valor padrão do <xref:System.Net.Cookie.Path> e dos algoritmos de correspondência de caminho foram implementados conforme definido na [seção 5.1.4](https://tools.ietf.org/html/rfc6265#section-5.1.4) do RFC 6265.</span><span class="sxs-lookup"><span data-stu-id="c807a-107">The calculation of the default value of <xref:System.Net.Cookie.Path> and path-matching algorithms were implemented as defined in [section 5.1.4](https://tools.ietf.org/html/rfc6265#section-5.1.4) of RFC 6265.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c807a-108">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="c807a-108">Recommended action</span></span>

<span data-ttu-id="c807a-109">Na maioria dos casos, você não precisará realizar nenhuma ação.</span><span class="sxs-lookup"><span data-stu-id="c807a-109">In most cases, you won't need to take any action.</span></span> <span data-ttu-id="c807a-110">No entanto, se o seu código depender da <xref:System.Net.Cookie.Path> validação, você precisará implementar a validação necessária em seu código.</span><span class="sxs-lookup"><span data-stu-id="c807a-110">However, if your code was dependent on <xref:System.Net.Cookie.Path> validation, you'll need to implement required validation in your code.</span></span> <span data-ttu-id="c807a-111">Se o seu código depender do cálculo do valor padrão para <xref:System.Net.Cookie.Path> , considere fornecer o <xref:System.Net.Cookie.Path> valor manualmente em vez de usar o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="c807a-111">If your code was dependent on default value calculation for <xref:System.Net.Cookie.Path>, consider supplying the <xref:System.Net.Cookie.Path> value manually instead of using the default value.</span></span>

#### <a name="category"></a><span data-ttu-id="c807a-112">Categoria</span><span class="sxs-lookup"><span data-stu-id="c807a-112">Category</span></span>

<span data-ttu-id="c807a-113">Rede</span><span class="sxs-lookup"><span data-stu-id="c807a-113">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c807a-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="c807a-114">Affected APIs</span></span>

- <xref:System.Net.Cookie?displayProperty=fullName>
- <xref:System.Net.CookieContainer?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Net.Cookie`
- `T:System.Net.CookieContainer`

-->
