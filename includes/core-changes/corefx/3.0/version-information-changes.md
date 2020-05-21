---
ms.openlocfilehash: bb264e406c6604c3606e564d99018eda0f9e8d89
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721028"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a>As APIs que relatam versão agora relatam produto e não versão de arquivo

Muitas das APIs que retornam versões no .NET Core agora retornam a versão do produto em vez da versão do arquivo.

#### <a name="change-description"></a>Descrição da alteração

No .NET Core 2,2 e em versões anteriores, métodos como <xref:System.Environment.Version?displayProperty=nameWithType> , <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> e a caixa de diálogo Propriedades do arquivo para assemblies do .NET Core refletem a versão do arquivo. A partir do .NET Core 3,0, eles refletem a versão do produto.

A figura a seguir ilustra a diferença nas informações de versão do assembly *System. Runtime. dll* para .net Core 2,2 (à esquerda) e do .net Core 3,0 (à direita), conforme exibido pela caixa de diálogo Propriedades de arquivo do **Windows Explorer** .

![Diferença nas informações de versão do produto](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="recommended-action"></a>Ação recomendada

Nenhum. Essa alteração deve tornar a detecção de versão intuitiva, em vez de obtuso.

#### <a name="category"></a>Categoria

Bibliotecas principais do .NET

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Environment.Version?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Environment.Version`
- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
