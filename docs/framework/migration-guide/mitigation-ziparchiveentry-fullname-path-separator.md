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
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a><span data-ttu-id="6b122-102">Mitigação: separador de caminho ZipArchiveEntry.FullName</span><span class="sxs-lookup"><span data-stu-id="6b122-102">Mitigation: ZipArchiveEntry.FullName Path Separator</span></span>

<span data-ttu-id="6b122-103">Começando com aplicativos que visam o .NET Framework 4.6.1, o separador de caminho usado na <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> propriedade mudou da barra invertida ("\\"") usada nas versões anteriores do .NET Framework para uma barra para frente ("/").</span><span class="sxs-lookup"><span data-stu-id="6b122-103">Starting with apps that target the .NET Framework 4.6.1, the path separator used in the <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> property has changed from the backslash ("\\") used in previous versions of .NET Framework to a forward slash ("/").</span></span> <span data-ttu-id="6b122-104">Os objetos <xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> são criados chamando uma das sobrecargas do método <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6b122-104"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> objects are created by calling one of the overloads of the <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="6b122-105">Impacto</span><span class="sxs-lookup"><span data-stu-id="6b122-105">Impact</span></span>  
 <span data-ttu-id="6b122-106">A alteração traz a implementação do .NET em conformidade com a seção 4.4.17.1 da [Especificação de formato de arquivo .ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) e permite que arquivamentos .ZIP sejam descompactados em sistemas não Windows.</span><span class="sxs-lookup"><span data-stu-id="6b122-106">The change brings the .NET implementation into conformity with section 4.4.17.1 of the [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) and allows .ZIP archives to be decompressed on non-Windows systems.</span></span>  
  
 <span data-ttu-id="6b122-107">Descompactação de um arquivo zip criado por um aplicativo que tem como alvo uma versão anterior do .NET Framework em sistemas operacionais não-Windows, como o MacOS, não consegue preservar a estrutura do diretório.</span><span class="sxs-lookup"><span data-stu-id="6b122-107">Decompressing a zip file created by an app that targets a previous version of .NET Framework on non-Windows operating systems such as MacOS fails to preserve the directory structure.</span></span> <span data-ttu-id="6b122-108">Por exemplo, no MacOS, ele cria um conjunto de arquivos cujo nome do arquivo\\concatena o caminho do diretório, qualquer caractere sem corte (" ") e o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="6b122-108">For example, on MacOS, it creates a set of files whose file name concatenates the directory path, any backslash ("\\") characters, and the filename.</span></span> <span data-ttu-id="6b122-109">Consequentemente, a estrutura do diretório de arquivos descompactados não é preservada.</span><span class="sxs-lookup"><span data-stu-id="6b122-109">As a result, the directory structure of decompressed files is not preserved.</span></span>  
  
 <span data-ttu-id="6b122-110">O impacto dessa mudança em . Os arquivos ZIP que são descompactados no sistema <xref:System.IO> operacional Windows por APIs no namespace do .NET Framework devem ser mínimos, uma vez que essas APIs podem lidar perfeitamente com uma barra ("/") ou uma barra invertida ("\\") como o caractere separador de caminho.</span><span class="sxs-lookup"><span data-stu-id="6b122-110">The impact of this change on .ZIP files that are decompressed on the Windows operating system by APIs in .NET Framework <xref:System.IO> namespace should be minimal, since these APIs can seamlessly handle either a slash ("/") or a backslash ("\\") as the path separator character.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="6b122-111">Atenuação</span><span class="sxs-lookup"><span data-stu-id="6b122-111">Mitigation</span></span>  
 <span data-ttu-id="6b122-112">Se esse comportamento for indesejável, você pode desativar adicionando uma configuração à seção de>em [ \<tempo de execução](../configure-apps/file-schema/runtime/runtime-element.md) do arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6b122-112">If this behavior is undesirable, you can opt out of by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="6b122-113">Veja a seguir a seção `<runtime>` e a opção de recusa.</span><span class="sxs-lookup"><span data-stu-id="6b122-113">The following shows both the `<runtime>` section and the opt-out switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 <span data-ttu-id="6b122-114">Além disso, aplicativos que têm como alvo versões anteriores do .NET Framework, mas estão sendo executados no .NET Framework 4.6.1 e versões posteriores podem optar por esse comportamento adicionando uma configuração à seção [ \<de>de tempo de execução](../configure-apps/file-schema/runtime/runtime-element.md) do arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6b122-114">In addition, apps that target previous versions of .NET Framework but are running on .NET Framework 4.6.1 and later versions can opt in to this behavior by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file.</span></span> <span data-ttu-id="6b122-115">Veja a seguir a seção `<runtime>` e a opção de aceitação.</span><span class="sxs-lookup"><span data-stu-id="6b122-115">The following shows both the `<runtime>` section and the opt-in switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6b122-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="6b122-116">See also</span></span>

- [<span data-ttu-id="6b122-117">Compatibilidade de aplicativos</span><span class="sxs-lookup"><span data-stu-id="6b122-117">Application compatibility</span></span>](application-compatibility.md)
