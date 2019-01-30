---
title: 'Mitigação: Separador de caminho ZipArchiveEntry.FullName'
ms.date: 03/30/2017
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 81da6f785394312dea92fffdbb00ce9d13f1bd6c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555642"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a><span data-ttu-id="e8a13-102">Mitigação: Separador de caminho ZipArchiveEntry.FullName</span><span class="sxs-lookup"><span data-stu-id="e8a13-102">Mitigation: ZipArchiveEntry.FullName Path Separator</span></span>
<span data-ttu-id="e8a13-103">A partir dos aplicativos direcionados ao [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], o separador de caminho usado na propriedade <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> foi alterado da barra invertida ("\\") usada nas versões anteriores do .NET Framework para uma barra ("/").</span><span class="sxs-lookup"><span data-stu-id="e8a13-103">Starting with apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], the path separator used in the <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> property has changed from the backslash ("\\") used in previous versions of the .NET Framework to a forward slash ("/").</span></span>   <span data-ttu-id="e8a13-104">Os objetos <xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> são criados chamando uma das sobrecargas do método <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e8a13-104"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> objects are created by calling one of the overloads of the <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="e8a13-105">Impacto</span><span class="sxs-lookup"><span data-stu-id="e8a13-105">Impact</span></span>  
 <span data-ttu-id="e8a13-106">A alteração traz a implementação do .NET em conformidade com a seção 4.4.17.1 da [Especificação de formato de arquivo .ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) e permite que arquivamentos .ZIP sejam descompactados em sistemas não Windows.</span><span class="sxs-lookup"><span data-stu-id="e8a13-106">The change brings the .NET implementation into conformity with section 4.4.17.1 of the [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) and allows .ZIP archives to be decompressed on non-Windows systems.</span></span>  
  
 <span data-ttu-id="e8a13-107">A descompactação de um arquivo zip criado por um aplicativo que se destina a uma versão anterior do .NET Framework em sistemas operacionais não Windows, como o Macintosh, falha na preservação da estrutura de diretório.</span><span class="sxs-lookup"><span data-stu-id="e8a13-107">Decompressing a zip file created  by an app that targets a previous version of the .NET Framework on non-Windows operating systems such as the Macintosh fails to preserve the directory structure.</span></span> <span data-ttu-id="e8a13-108">Por exemplo, no Macintosh, ela cria um conjunto de arquivos cujo nome de arquivo concatena o caminho do diretório com qualquer caractere de barra invertida ("\\") e o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="e8a13-108">For example, on the Macintosh, it creates a set of files whose filename concatenates the directory path, along with any backslash ("\\") characters, and the filename.</span></span> <span data-ttu-id="e8a13-109">Consequentemente, a estrutura do diretório de arquivos descompactados não é preservada.</span><span class="sxs-lookup"><span data-stu-id="e8a13-109">As a result, the directory structure of decompressed files is not preserved.</span></span>  
  
 <span data-ttu-id="e8a13-110">O impacto dessa alteração em arquivos .ZIP que são descompactados no sistema operacional Windows por APIs no namespace <xref:System.IO> do .NET Framework deve ser mínimo, uma vez que as APIs podem lidar perfeitamente com uma barra ("/") ou uma barra invertida ("\\") como o caractere separador de caminho.</span><span class="sxs-lookup"><span data-stu-id="e8a13-110">The impact of this change on .ZIP files that are decompressed on the Windows operating system by APIs in the .NET Framework <xref:System.IO> namespace should be minimal, since these APIs can seamlessly handle either a slash ("/") or a backslash ("\\") as the path separator character.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="e8a13-111">Redução</span><span class="sxs-lookup"><span data-stu-id="e8a13-111">Mitigation</span></span>  
 <span data-ttu-id="e8a13-112">Se esse comportamento for indesejável, você poderá recusar adicionando uma definição de configuração à seção [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) do seu arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e8a13-112">If this behavior is undesirable, you can opt out of by adding a configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="e8a13-113">Veja a seguir a seção `<runtime>` e a opção de recusa.</span><span class="sxs-lookup"><span data-stu-id="e8a13-113">The following shows both the `<runtime>` section and the opt-out switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 <span data-ttu-id="e8a13-114">Além disso, os aplicativos destinados a versões anteriores do .NET Framework, mas estão sendo executados no [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] e versões posteriores, podem aceitar esse comportamento adicionando uma definição de configuração à seção [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) do arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e8a13-114">In addition, apps that target previous versions of the .NET Framework but are running on the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and later versions can opt in to this behavior by adding a configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file.</span></span> <span data-ttu-id="e8a13-115">Veja a seguir a seção `<runtime>` e a opção de aceitação.</span><span class="sxs-lookup"><span data-stu-id="e8a13-115">The following shows both the `<runtime>` section and the opt-in switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e8a13-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e8a13-116">See also</span></span>
- [<span data-ttu-id="e8a13-117">Alterações de redirecionamento</span><span class="sxs-lookup"><span data-stu-id="e8a13-117">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
- [<span data-ttu-id="e8a13-118">Compatibilidade de aplicativos na versão 4.6.1</span><span class="sxs-lookup"><span data-stu-id="e8a13-118">Application Compatibility in 4.6.1</span></span>](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)
