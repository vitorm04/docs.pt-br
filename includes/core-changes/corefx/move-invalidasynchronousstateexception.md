---
ms.openlocfilehash: 4b41e5fcb6da638457ca8029a635f391b6a7b8ec
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182045"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a>InvalidAsynchronousStateException movido para outro assembly

A <xref:System.ComponentModel.InvalidAsynchronousStateException> classe foi movida.

#### <a name="change-description"></a>Alterar descrição

No .NET Core 2,2 e versões anteriores, a <xref:System.ComponentModel.InvalidAsynchronousStateException> classe é encontrada no assembly *System. ComponentModel. TypeConverter* .

A partir do .NET Core 3,0, ele é encontrado no assembly *System. ComponentModel. primitivas* .

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="recommended-action"></a>Ação recomendada

Essa alteração afeta apenas os aplicativos que usam a reflexão para <xref:System.ComponentModel.InvalidAsynchronousStateException> carregar o chamando um método <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> como ou uma sobrecarga de <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> que assume que o tipo está em um assembly específico. Se esse for o caso, o assembly ao qual o assembly referenciado na chamada do método deve ser atualizado para refletir o novo local do assembly do tipo.

#### <a name="category"></a>Categoria

CoreFx

#### <a name="affected-apis"></a>APIs afetadas

- Nenhum

<!-- 

### Affected APIs

- Not detectable via API analysis

-->