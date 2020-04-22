---
ms.openlocfilehash: 1580c8c8b7bdad91656f494537230293dbaaf93b
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021609"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a>APIs que relatam versão agora relatam produto e não versão de arquivo

Muitas das APIs que retornam versões no .NET Core agora retornam a versão do produto em vez da versão do arquivo.

#### <a name="change-description"></a>Descrição da alteração

Em .NET Core 2.2 e versões anteriores, métodos como <xref:System.Environment.Version?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>e a caixa de diálogo propriedades de arquivo para conjuntos .NET Core refletem a versão do arquivo. A partir do .NET Core 3.0, eles refletem a versão do produto.

A figura a seguir ilustra a diferença nas informações da versão para o conjunto *System.Runtime.dll* para .NET Core 2.2 (à esquerda) e .NET Core 3.0 (à direita) como exibido pela caixa de diálogo propriedades do arquivo **Windows Explorer.**

![Diferença nas informações da versão do produto](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="recommended-action"></a>Ação recomendada

Nenhum. Essa mudança deve tornar a detecção de versão intuitiva em vez de obtusa.

#### <a name="category"></a>Categoria

Bibliotecas Core .NET

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Environment.Version?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>

<!--

### Affected APIs

- `P:System.Environment.Version`
- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
