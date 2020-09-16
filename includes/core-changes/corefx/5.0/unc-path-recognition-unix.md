---
ms.openlocfilehash: 0246f325a6274082b7fb0d5590cec7c80687ae85
ms.sourcegitcommit: ef86c24c418439b8bb5e3e7d64bbdbe5e11c3e9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2020
ms.locfileid: "88720170"
---
### <a name="uri-recognition-of-unc-paths-on-unix"></a>Reconhecimento de URI de caminhos UNC no UNIX

A <xref:System.Uri> classe agora reconhece cadeias de caracteres que começam com duas barras ( `//` ) como caminhos UNC (Convenção de nomenclatura universal) em sistemas operacionais UNIX. Essa alteração torna o comportamento de tais cadeias de caracteres consistentes em todas as plataformas.

#### <a name="change-description"></a>Descrição das alterações

Nas versões anteriores do .NET, a <xref:System.Uri> classe reconhece cadeias de caracteres que começam com com duas barras, por exemplo, `//contoso` como caminhos de arquivo absolutos em sistemas operacionais UNIX. No entanto, no Windows, essas cadeias de caracteres são reconhecidas como caminhos UNC.

A partir do .NET 5,0, a <xref:System.Uri> classe reconhece cadeias de caracteres que começam com com duas barras para frente como caminhos UNC em todas as plataformas, incluindo UNIX. Além disso, as propriedades se comportam de acordo com a semântica UNC:

- <xref:System.Uri.IsUnc?displayProperty=nameWithType> retorna `true`.
- As barras invertidas no caminho são substituídas por barras "/". Por exemplo, `//first\second` torna-se `//first/second`.
- <xref:System.Uri.LocalPath?displayProperty=nameWithType> Não codificar caracteres por porcentagem. Por exemplo, `//first/\uFFF0` *não* é convertido em `//first/%EF%BF%B0` .

#### <a name="version-introduced"></a>Versão introduzida

5,0

#### <a name="recommended-action"></a>Ação recomendada

Nenhuma ação é necessária na parte do desenvolvedor.

#### <a name="category"></a>Categoria

Bibliotecas principais do .NET

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Uri?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Uri`

-->
