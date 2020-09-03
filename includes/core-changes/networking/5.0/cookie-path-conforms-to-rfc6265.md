---
ms.openlocfilehash: fdbe8ca9b6dbf24c08a2d041c5c7f2e869995f69
ms.sourcegitcommit: b1f4756120deaecb8b554477bb040620f69a4209
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2020
ms.locfileid: "89414442"
---
### <a name="cookie-path-handling-now-conforms-to-rfc-6265"></a><span data-ttu-id="87e8c-101">O tratamento de caminho de cookie agora está em conformidade com RFC 6265</span><span class="sxs-lookup"><span data-stu-id="87e8c-101">Cookie Path handling now conforms to RFC 6265</span></span>

<span data-ttu-id="87e8c-102">Algoritmos de tratamento de caminho definidos no [RFC 6265](https://tools.ietf.org/html/rfc6265) foram implementados para `Cookie` `CookieContainer` classes e.</span><span class="sxs-lookup"><span data-stu-id="87e8c-102">Path handling algorithms defined in [RFC 6265](https://tools.ietf.org/html/rfc6265) were implemented for `Cookie` and `CookieContainer` classes.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="87e8c-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="87e8c-103">Version introduced</span></span>

<span data-ttu-id="87e8c-104">5,0</span><span class="sxs-lookup"><span data-stu-id="87e8c-104">5.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="87e8c-105">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="87e8c-105">Change description</span></span>

- <span data-ttu-id="87e8c-106">A restrição para o `Path` atributo é removida (não é mais esperado que seja um prefixo do caminho da solicitação).</span><span class="sxs-lookup"><span data-stu-id="87e8c-106">Restriction for the `Path` attribute is removed (it's no longer expected to be a prefix of the request path).</span></span>
- <span data-ttu-id="87e8c-107">O cálculo do valor padrão `Path` e dos algoritmos de correspondência de caminho foram implementados conforme definido na [seção 5.1.4](https://tools.ietf.org/html/rfc6265#section-5.1.4) do RFC 6265.</span><span class="sxs-lookup"><span data-stu-id="87e8c-107">Calculation of the default value of `Path` and path matching algorithms were implemented as defined in [section 5.1.4](https://tools.ietf.org/html/rfc6265#section-5.1.4) of RFC 6265.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="87e8c-108">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="87e8c-108">Recommended action</span></span>

<span data-ttu-id="87e8c-109">Na maioria dos casos, você não precisará realizar nenhuma ação.</span><span class="sxs-lookup"><span data-stu-id="87e8c-109">In most cases, you won't need to take any action.</span></span> <span data-ttu-id="87e8c-110">No entanto, se o seu código depender da `Path` validação, você precisaria implementar a validação necessária em seu código; ou se o seu código fosse dependente `Path` do cálculo do valor padrão, talvez você queira fornecer o `Path` valor manualmente em vez de usar o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="87e8c-110">However, if your code was dependent on `Path` validation you would need to implement required validation in your code; or if your code was dependent on `Path`'s default value calculation, you might want to supply the `Path` value manually instead of using the default value.</span></span>

#### <a name="category"></a><span data-ttu-id="87e8c-111">Categoria</span><span class="sxs-lookup"><span data-stu-id="87e8c-111">Category</span></span>

<span data-ttu-id="87e8c-112">Rede</span><span class="sxs-lookup"><span data-stu-id="87e8c-112">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="87e8c-113">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="87e8c-113">Affected APIs</span></span>

- <xref:System.Net.Cookie?displayProperty=fullName>
- <xref:System.Net.CookieContainer?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Net.Cookie`
- `T:System.Net.CookieContainer`

-->
