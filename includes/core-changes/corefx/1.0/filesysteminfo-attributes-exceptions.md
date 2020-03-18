---
ms.openlocfilehash: 4091bdcf7d9ed8872aed5faa6e6d3ed143903787
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449383"
---
### <a name="unauthorizedaccessexception-thrown-by-filesysteminfoattributes"></a>Não autorizadoAccessException lançado por FileSystemInfo.Attributes

No .NET Core, um <xref:System.UnauthorizedAccessException> é jogado quando o chamador tenta definir um valor de atributo de arquivo, mas não tem permissão de gravação.

#### <a name="change-description"></a>Descrição da alteração

No .NET Framework, um <xref:System.ArgumentException> é jogado quando o chamador tenta definir um valor de atributo de arquivo, <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> mas não tem permissão de gravação. Em .NET Core, um <xref:System.UnauthorizedAccessException> é jogado em seu lugar. (Em .NET Core, um <xref:System.ArgumentException> ainda é jogado se o chamador tentar definir um atributo de arquivo inválido.)

#### <a name="version-introduced"></a>Versão introduzida

1.0

#### <a name="recommended-action"></a>Ação recomendada

Modifique `catch` quaisquer instruções para pegar um <xref:System.UnauthorizedAccessException> em <xref:System.ArgumentException>vez de, ou, além de, um , conforme necessário.

#### <a name="category"></a>Categoria

CoreFx

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
