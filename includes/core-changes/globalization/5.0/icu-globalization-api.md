---
ms.openlocfilehash: 18718ebc934e0175c20411055b8c0a90ef6b175f
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539432"
---
### <a name="globalization-apis-use-icu-libraries-on-windows"></a>APIs de globalização usam bibliotecas ICU no Windows

O .NET 5,0 e versões posteriores usam bibliotecas [internacionais para](http://site.icu-project.org/home) a funcionalidade de globalização na execução no Windows 10 pode ser 2019 atualização ou posterior.

#### <a name="change-description"></a>Descrição das alterações

Anteriormente, as bibliotecas do .NET usavam APIs [NLS (suporte a idioma nacional)](/windows/win32/intl/national-language-support) para a funcionalidade de globalização. Por exemplo, as funções NLS foram usadas para obter dados de cultura, como padrões de formato de data e hora, comparar cadeias de caracteres e executar maiúsculas e minúsculas na cultura apropriada.

A partir do .NET 5,0, se um aplicativo estiver em execução no Windows 10 pode ser 2019 Update ou posterior, as bibliotecas do .NET usarão APIs de globalização [ICU](http://site.icu-project.org/home) . O Windows 10 pode 2019 atualização e versões posteriores são fornecidas com a biblioteca nativa do ICU. Se o tempo de execução do .NET não puder carregar o ICU, ele usará o NLS.

Essa alteração foi introduzida por dois motivos:

- Os aplicativos têm o mesmo comportamento de globalização entre as plataformas, incluindo Linux, macOS e Windows.
- Os aplicativos podem controlar o comportamento de globalização usando bibliotecas ICU personalizadas.

#### <a name="version-introduced"></a>Versão introduzida

.NET 5,0 Preview 4

#### <a name="recommended-action"></a>Ação recomendada

Nenhuma ação é necessária na parte do desenvolvedor. No entanto, se você quiser continuar usando as APIs de globalização NLS, poderá definir uma [opção de tempo de execução](../../../../docs/core/run-time-config/globalization.md#nls) para reverter para esse comportamento. Para obter mais informações sobre as opções disponíveis, consulte o artigo [globalização .net e ICU](../../../../docs/standard/globalization-localization/globalization-icu.md) .

#### <a name="category"></a>Categoria

Globalização

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Span%601?displayProperty=fullName>
- <xref:System.String?displayProperty=fullName>
- Maioria dos tipos no <xref:System.Globalization?displayProperty=fullName> namespace

<!--

#### Affected APIs

- ``T:System.Span`1``
- `T:System.String`
- `N:System.Globalization`

-->
