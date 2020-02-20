---
ms.openlocfilehash: 4091bdcf7d9ed8872aed5faa6e6d3ed143903787
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449383"
---
### <a name="unauthorizedaccessexception-thrown-by-filesysteminfoattributes"></a>UnauthorizedAccessException gerado por FileSystemInfo. Attributes

No .NET Core, um <xref:System.UnauthorizedAccessException> é gerado quando o chamador tenta definir um valor de atributo de arquivo, mas não tem permissão de gravação.

#### <a name="change-description"></a>Alterar descrição

No .NET Framework, um <xref:System.ArgumentException> é gerado quando o chamador tenta definir um valor de atributo de arquivo em <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>, mas não tem permissão de gravação. No .NET Core, um <xref:System.UnauthorizedAccessException> é lançado em vez disso. (No .NET Core, um <xref:System.ArgumentException> ainda será gerado se o chamador tentar definir um atributo de arquivo inválido.)

#### <a name="version-introduced"></a>Versão introduzida

1.0

#### <a name="recommended-action"></a>Ação recomendada

Modifique quaisquer `catch` instruções para capturar um <xref:System.UnauthorizedAccessException> em vez de, ou além de, um <xref:System.ArgumentException>, conforme necessário.

#### <a name="category"></a>Categoria

CoreFx

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
