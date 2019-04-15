---
ms.openlocfilehash: b4e062fe3a00b76da144e706841f87b2a95888e5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234593"
---
### <a name="encoderparameter-ctor-is-obsolete"></a>O construtor EncoderParameter está obsoleto

|   |   |
|---|---|
|Detalhes|O construtor <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> agora está obsoleto e introduzirá novos avisos de compilação se for usado.|
|Sugestão|Embora o construtor <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> continue funcionando, o seguinte construtor deverá ser usado em seu lugar para evitar o aviso de build obsoleto durante a recompilação de código com as ferramentas do .NET Framework 4.5: <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)>.|
|Escopo|Secundário|
|Versão|4.5|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|
