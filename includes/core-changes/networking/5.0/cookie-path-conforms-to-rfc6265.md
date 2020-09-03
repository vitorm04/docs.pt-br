---
ms.openlocfilehash: fdbe8ca9b6dbf24c08a2d041c5c7f2e869995f69
ms.sourcegitcommit: b1f4756120deaecb8b554477bb040620f69a4209
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2020
ms.locfileid: "89414442"
---
### <a name="cookie-path-handling-now-conforms-to-rfc-6265"></a>O tratamento de caminho de cookie agora está em conformidade com RFC 6265

Algoritmos de tratamento de caminho definidos no [RFC 6265](https://tools.ietf.org/html/rfc6265) foram implementados para `Cookie` `CookieContainer` classes e.

#### <a name="version-introduced"></a>Versão introduzida

5,0

#### <a name="change-description"></a>Descrição das alterações

- A restrição para o `Path` atributo é removida (não é mais esperado que seja um prefixo do caminho da solicitação).
- O cálculo do valor padrão `Path` e dos algoritmos de correspondência de caminho foram implementados conforme definido na [seção 5.1.4](https://tools.ietf.org/html/rfc6265#section-5.1.4) do RFC 6265.

#### <a name="recommended-action"></a>Ação recomendada

Na maioria dos casos, você não precisará realizar nenhuma ação. No entanto, se o seu código depender da `Path` validação, você precisaria implementar a validação necessária em seu código; ou se o seu código fosse dependente `Path` do cálculo do valor padrão, talvez você queira fornecer o `Path` valor manualmente em vez de usar o valor padrão.

#### <a name="category"></a>Categoria

Rede

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Net.Cookie?displayProperty=fullName>
- <xref:System.Net.CookieContainer?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Net.Cookie`
- `T:System.Net.CookieContainer`

-->
