---
title: 'Mitigação: separador de caminho ZipArchiveEntry.FullName'
description: Saiba como o separador de caminho para a propriedade ZipArchiveEntry. FullName foi alterado começando com aplicativos direcionados .NET Framework 4.6.1.
ms.date: 03/30/2017
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
ms.openlocfilehash: 8cd6362038ce0548681f3d3b44724f3ef9ff62cb
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475288"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a><span data-ttu-id="605a2-103">Mitigação: separador de caminho ZipArchiveEntry.FullName</span><span class="sxs-lookup"><span data-stu-id="605a2-103">Mitigation: ZipArchiveEntry.FullName Path Separator</span></span>

<span data-ttu-id="605a2-104">A partir de aplicativos direcionados ao .NET Framework 4.6.1, o separador de caminho usado na <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> propriedade foi alterado da barra invertida (" \\ ") usada em versões anteriores do .NET Framework para uma barra ("/").</span><span class="sxs-lookup"><span data-stu-id="605a2-104">Starting with apps that target the .NET Framework 4.6.1, the path separator used in the <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> property has changed from the backslash ("\\") used in previous versions of .NET Framework to a forward slash ("/").</span></span> <span data-ttu-id="605a2-105">Os objetos <xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> são criados chamando uma das sobrecargas do método <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="605a2-105"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> objects are created by calling one of the overloads of the <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="605a2-106">Impacto</span><span class="sxs-lookup"><span data-stu-id="605a2-106">Impact</span></span>  
 <span data-ttu-id="605a2-107">A alteração traz a implementação do .NET em conformidade com a seção 4.4.17.1 da [Especificação de formato de arquivo .ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) e permite que arquivamentos .ZIP sejam descompactados em sistemas não Windows.</span><span class="sxs-lookup"><span data-stu-id="605a2-107">The change brings the .NET implementation into conformity with section 4.4.17.1 of the [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) and allows .ZIP archives to be decompressed on non-Windows systems.</span></span>  
  
 <span data-ttu-id="605a2-108">A descompactação de um arquivo zip criado por um aplicativo direcionado a uma versão anterior do .NET Framework em sistemas operacionais não Windows, como o MacOS, falha ao preservar a estrutura do diretório.</span><span class="sxs-lookup"><span data-stu-id="605a2-108">Decompressing a zip file created by an app that targets a previous version of .NET Framework on non-Windows operating systems such as MacOS fails to preserve the directory structure.</span></span> <span data-ttu-id="605a2-109">Por exemplo, no MacOS, ele cria um conjunto de arquivos cujo nome de arquivo concatena o caminho do diretório, qualquer barra invertida (" \\ ") caracteres e o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="605a2-109">For example, on MacOS, it creates a set of files whose file name concatenates the directory path, any backslash ("\\") characters, and the filename.</span></span> <span data-ttu-id="605a2-110">Consequentemente, a estrutura do diretório de arquivos descompactados não é preservada.</span><span class="sxs-lookup"><span data-stu-id="605a2-110">As a result, the directory structure of decompressed files is not preserved.</span></span>  
  
 <span data-ttu-id="605a2-111">O impacto dessa alteração em. Os arquivos ZIP que são descompactados no sistema operacional Windows por APIs no <xref:System.IO> namespace .NET Framework devem ser mínimos, uma vez que essas APIs podem lidar diretamente com uma barra ("/") ou uma barra invertida (" \\ ") como o caractere separador de caminho.</span><span class="sxs-lookup"><span data-stu-id="605a2-111">The impact of this change on .ZIP files that are decompressed on the Windows operating system by APIs in .NET Framework <xref:System.IO> namespace should be minimal, since these APIs can seamlessly handle either a slash ("/") or a backslash ("\\") as the path separator character.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="605a2-112">Atenuação</span><span class="sxs-lookup"><span data-stu-id="605a2-112">Mitigation</span></span>  
 <span data-ttu-id="605a2-113">Se esse comportamento for indesejável, você poderá recusar adicionando um parâmetro de configuração à [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) seção do arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="605a2-113">If this behavior is undesirable, you can opt out of by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="605a2-114">Veja a seguir a seção `<runtime>` e a opção de recusa.</span><span class="sxs-lookup"><span data-stu-id="605a2-114">The following shows both the `<runtime>` section and the opt-out switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 <span data-ttu-id="605a2-115">Além disso, os aplicativos destinados a versões anteriores do .NET Framework, mas que estão em execução no .NET Framework 4.6.1 e versões posteriores podem aceitar esse comportamento, adicionando uma configuração à [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) seção do arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="605a2-115">In addition, apps that target previous versions of .NET Framework but are running on .NET Framework 4.6.1 and later versions can opt in to this behavior by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file.</span></span> <span data-ttu-id="605a2-116">Veja a seguir a seção `<runtime>` e a opção de aceitação.</span><span class="sxs-lookup"><span data-stu-id="605a2-116">The following shows both the `<runtime>` section and the opt-in switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="605a2-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="605a2-117">See also</span></span>

- [<span data-ttu-id="605a2-118">Compatibilidade de aplicativos</span><span class="sxs-lookup"><span data-stu-id="605a2-118">Application compatibility</span></span>](application-compatibility.md)
