---
ms.openlocfilehash: ace0a4a60ad4d3f3a13cf4bdb2431e61d04ad8e7
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021619"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a>InvalidAsynchronousStateException mudou-se para outro conjunto

A <xref:System.ComponentModel.InvalidAsynchronousStateException> classe foi movida.

#### <a name="change-description"></a>Descrição da alteração

Nas versões .NET Core 2.2 e anteriores, a <xref:System.ComponentModel.InvalidAsynchronousStateException> classe é encontrada no conjunto *System.ComponentModel.TypeConverter.*

A partir do .NET Core 3.0, ele é encontrado no conjunto *System.ComponentModel.Primitives.*

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="recommended-action"></a>Ação recomendada

Essa alteração afeta apenas aplicativos que usam <xref:System.ComponentModel.InvalidAsynchronousStateException> reflexão para <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> carregar o <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> chamado de um método como ou uma sobrecarga que pressupõe que o tipo esteja em um conjunto específico. Se esse for o caso, a montagem da montagem referenciada na chamada do método deve ser atualizada para refletir o novo local de montagem do tipo.

#### <a name="category"></a>Categoria

Bibliotecas Core .NET

#### <a name="affected-apis"></a>APIs afetadas

Nenhum.

<!--

### Affected APIs

- Not detectable via API analysis

-->
