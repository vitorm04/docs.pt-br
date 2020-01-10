---
ms.openlocfilehash: 5612ebce67946e22aaeeba861115ce4f8967e1f5
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344446"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a>As APIs que relatam versão agora relatam produto e não versão de arquivo

Muitas das APIs que retornam versões no .NET Core agora retornam a versão do produto em vez da versão do arquivo.

#### <a name="change-description"></a>Descrição das alterações

No .NET Core 2,2 e em versões anteriores, métodos como <xref:System.Environment.Version?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>e a caixa de diálogo Propriedades do arquivo para assemblies do .NET Core refletem a versão do arquivo. A partir do .NET Core 3,0, eles refletem a versão do produto.

A figura a seguir ilustra a diferença nas informações de versão do assembly *System. Runtime. dll* para .net Core 2,2 (à esquerda) e do .net Core 3,0 (à direita), conforme exibido pela caixa de diálogo Propriedades de arquivo do **Windows Explorer** .

![Diferença nas informações de versão do produto](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="recommended-action"></a>Ação recomendada

Nenhuma. Essa alteração deve tornar a detecção de versão intuitiva, em vez de obtuso.

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
