---
ms.openlocfilehash: 5bed2d1d4eda4a4c577f05f614a71aa9180998a7
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182004"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a>As APIs que relatam versão agora relatam produto e não versão de arquivo

Muitas das APIs que retornam versões no .NET Core agora retornavam a versão do produto em vez da versão do arquivo.

#### <a name="change-description"></a>Alterar descrição

No .NET Core 2,2 e em versões anteriores, métodos como <xref:System.Environment.Version?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>e a caixa de diálogo Propriedades do arquivo para assemblies do .NET Core refletem a versão do arquivo. A partir do .NET Core 3,0, eles refletem a versão do produto. 

A figura a seguir ilustra a diferença nas informações de versão do assembly *System. Runtime. dll* para .net Core 2,2 (à esquerda) e do .net Core 3,0 (à direita), conforme exibido pela caixa de diálogo Propriedades de arquivo do **Windows Explorer** .

![Diferença nas informações de versão do produto](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="recommended-action"></a>Ação recomendada

nenhuma. Essa alteração deve tornar a detecção de versão intuitiva, em vez de obtuso.

#### <a name="category"></a>Categoria

CoreFx

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Environment.Version?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `P:System.Environment.Version`
- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`


-->