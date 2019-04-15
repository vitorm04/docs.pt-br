---
ms.openlocfilehash: e4cf139d308a1c12425d966a84d59a0c3bb89712
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236335"
---
### <a name="nullreferenceexception-in-exception-handling-code-from-imagesourceconverterconvertfrom"></a>NullReferenceException no código de tratamento de exceções de ImageSourceConverter.ConvertFrom

|   |   |
|---|---|
|Detalhes|Um erro no código de tratamento de exceção de <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> fazia com que um <xref:System.NullReferenceException?displayProperty=name> incorreto fosse gerado, em vez da exceção pretendida (por exemplo, <xref:System.IO.DirectoryNotFoundException?displayProperty=name>, <xref:System.IO.FileNotFoundException?displayProperty=name>). Essa alteração corrige esse erro, de modo que o método agora gera a exceção certa. <p/>Por padrão todos os aplicativos direcionados ao .NET Framework 4.6.2 e anteriores continuam a gerar <xref:System.NullReferenceException?displayProperty=name> para manter a compatibilidade. Os desenvolvedores que direcionarem ao .NET Framework 4.7 e superiores, observação as exceções certas.|
|Sugestão|Os desenvolvedores que desejam reverter o recebimento de <xref:System.NullReferenceException?displayProperty=name> ao direcionar para o .NET Framework 4.7 podem adicionar/mesclar o seguinte ao arquivo App.config do aplicativo:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Media.ImageSourceConverter.OverrideExceptionWithNullReferenceException=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Escopo|Microsoft Edge|
|Versão|4.7|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)?displayProperty=nameWithType></li></ul>|
