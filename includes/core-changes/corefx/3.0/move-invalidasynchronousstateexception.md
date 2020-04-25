---
ms.openlocfilehash: d1562cb76f37b6cc2aeb6fe2f7c17c393e169e84
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158458"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a>InvalidAsynchronousStateException movido para outro assembly

A <xref:System.ComponentModel.InvalidAsynchronousStateException> classe foi movida.

#### <a name="change-description"></a>Descrição da alteração

No .NET Core 2,2 e versões anteriores, a <xref:System.ComponentModel.InvalidAsynchronousStateException> classe é encontrada no assembly *System. ComponentModel. TypeConverter* .

A partir do .NET Core 3,0, ele é encontrado no assembly *System. ComponentModel. primitivas* .

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="recommended-action"></a>Ação recomendada

Essa alteração afeta apenas os aplicativos que usam a reflexão para <xref:System.ComponentModel.InvalidAsynchronousStateException> carregar o chamando um método como <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> ou uma sobrecarga de <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> que assume que o tipo está em um assembly específico. Se esse for o caso, atualize o assembly referenciado na chamada de método para refletir o novo local do assembly do tipo.

#### <a name="category"></a>Categoria

Bibliotecas principais do .NET

#### <a name="affected-apis"></a>APIs afetadas

Nenhum.

<!--

### Affected APIs

- Not detectable via API analysis

-->
