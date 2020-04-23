---
title: 'Mitigação: separador de caminho ZipArchiveEntry.FullName'
ms.date: 03/30/2017
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
ms.openlocfilehash: 3f6c7f258fd5dbf01db4d79b73b88ddd7484f9b2
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102613"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a>Mitigação: separador de caminho ZipArchiveEntry.FullName

Começando com aplicativos que visam o .NET Framework 4.6.1, o separador de caminho usado na <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> propriedade mudou da barra invertida ("\\"") usada nas versões anteriores do .NET Framework para uma barra para frente ("/"). Os objetos <xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> são criados chamando uma das sobrecargas do método <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType>.  
  
## <a name="impact"></a>Impacto  
 A alteração traz a implementação do .NET em conformidade com a seção 4.4.17.1 da [Especificação de formato de arquivo .ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) e permite que arquivamentos .ZIP sejam descompactados em sistemas não Windows.  
  
 Descompactação de um arquivo zip criado por um aplicativo que tem como alvo uma versão anterior do .NET Framework em sistemas operacionais não-Windows, como o MacOS, não consegue preservar a estrutura do diretório. Por exemplo, no MacOS, ele cria um conjunto de arquivos cujo nome do arquivo\\concatena o caminho do diretório, qualquer caractere sem corte (" ") e o nome do arquivo. Consequentemente, a estrutura do diretório de arquivos descompactados não é preservada.  
  
 O impacto dessa mudança em . Os arquivos ZIP que são descompactados no sistema <xref:System.IO> operacional Windows por APIs no namespace do .NET Framework devem ser mínimos, uma vez que essas APIs podem lidar perfeitamente com uma barra ("/") ou uma barra invertida ("\\") como o caractere separador de caminho.  
  
## <a name="mitigation"></a>Atenuação  
 Se esse comportamento for indesejável, você pode desativar adicionando uma configuração à seção de>em [ \<tempo de execução](../configure-apps/file-schema/runtime/runtime-element.md) do arquivo de configuração do aplicativo. Veja a seguir a seção `<runtime>` e a opção de recusa.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 Além disso, aplicativos que têm como alvo versões anteriores do .NET Framework, mas estão sendo executados no .NET Framework 4.6.1 e versões posteriores podem optar por esse comportamento adicionando uma configuração à seção [ \<de>de tempo de execução](../configure-apps/file-schema/runtime/runtime-element.md) do arquivo de configuração do aplicativo. Veja a seguir a seção `<runtime>` e a opção de aceitação.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a>Confira também

- [Compatibilidade de aplicativos](application-compatibility.md)
