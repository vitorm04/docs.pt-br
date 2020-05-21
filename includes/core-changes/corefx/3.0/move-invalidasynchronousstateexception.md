---
ms.openlocfilehash: 78678b4b352bb063d1521e9aee3492c0cee059b8
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720975"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a>InvalidAsynchronousStateException movido para outro assembly

A <xref:System.ComponentModel.InvalidAsynchronousStateException> classe foi movida.

#### <a name="change-description"></a>Descrição da alteração

No .NET Core 2,2 e versões anteriores, a <xref:System.ComponentModel.InvalidAsynchronousStateException> classe é encontrada no assembly *System. ComponentModel. TypeConverter* .

A partir do .NET Core 3,0, ele é encontrado no assembly *System. ComponentModel. primitivas* .

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="recommended-action"></a>Ação recomendada

Essa alteração afeta apenas os aplicativos que usam a reflexão para carregar o <xref:System.ComponentModel.InvalidAsynchronousStateException> chamando um método como <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> ou uma sobrecarga de <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> que assume que o tipo está em um assembly específico. Se esse for o caso, atualize o assembly referenciado na chamada de método para refletir o novo local do assembly do tipo.

#### <a name="category"></a>Categoria

Bibliotecas principais do .NET

#### <a name="affected-apis"></a>APIs afetadas

Nenhum.

<!--

#### Affected APIs

- Not detectable via API analysis

-->
