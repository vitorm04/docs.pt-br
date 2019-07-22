---
ms.openlocfilehash: 824d75585efd40937c1a48376ec7862cba1a8fa3
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68235581"
---
### <a name="nullreferenceexception-in-exception-handling-code-from-imagesourceconverterconvertfrom"></a>NullReferenceException no código de tratamento de exceções de ImageSourceConverter.ConvertFrom

|   |   |
|---|---|
|Detalhes|Um erro no código de manipulação de exceções para <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> fez um <xref:System.NullReferenceException?displayProperty=name> incorreto ser gerado, em vez da exceção pretendida (<xref:System.IO.DirectoryNotFoundException?displayProperty=name> ou <xref:System.IO.FileNotFoundException?displayProperty=name>). Essa alteração corrige esse erro, de modo que o método agora gera a exceção certa. <p/>Por padrão todos os aplicativos direcionados ao .NET Framework 4.6.2 e anteriores continuam a gerar <xref:System.NullReferenceException?displayProperty=name> para manter a compatibilidade. Os desenvolvedores que direcionarem ao .NET Framework 4.7 e superiores, observação as exceções certas.|
|Sugestão|Os desenvolvedores que desejam reverter para receber <xref:System.NullReferenceException?displayProperty=name> quando tiverem o .NET Framework 4.7 ou mais recentes como destino podem adicionar/mesclar o seguinte ao arquivo App.config do aplicativo:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Media.ImageSourceConverter.OverrideExceptionWithNullReferenceException=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Escopo|Microsoft Edge|
|Versão|4.7|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)?displayProperty=nameWithType></li></ul>|
