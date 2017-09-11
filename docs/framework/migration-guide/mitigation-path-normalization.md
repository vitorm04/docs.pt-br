---
title: "Mitigação: normalização do caminho"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
caps.latest.revision: 6
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e30099e315f88bd051dca2e1f6c83d1bccc49569
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-path-normalization"></a><span data-ttu-id="7e386-102">Mitigação: normalização do caminho</span><span class="sxs-lookup"><span data-stu-id="7e386-102">Mitigation: Path Normalization</span></span>
<span data-ttu-id="7e386-103">Começando com os aplicativos direcionados ao [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], a normalização do caminho no .NET Framework foi alterada.</span><span class="sxs-lookup"><span data-stu-id="7e386-103">Starting with apps the target  the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], path normalization in the .NET Framework has changed.</span></span>  
  
## <a name="what-is-path-normalization"></a><span data-ttu-id="7e386-104">O que é normalização do caminho?</span><span class="sxs-lookup"><span data-stu-id="7e386-104">What is path normalization?</span></span>  
 <span data-ttu-id="7e386-105">Normalizar um caminho envolve modificar a cadeia de caracteres que identifica um caminho ou arquivo para que ele esteja em conformidade com um caminho válido no sistema operacional de destino.</span><span class="sxs-lookup"><span data-stu-id="7e386-105">Normalizing a path involves modifying the string that identifies a path or file so that it conforms to a valid path on the target operating system.</span></span> <span data-ttu-id="7e386-106">Normalmente, a normalização envolve:</span><span class="sxs-lookup"><span data-stu-id="7e386-106">Normalization typically involves:</span></span>  
  
-   <span data-ttu-id="7e386-107">Padronização de separadores de diretório e componente.</span><span class="sxs-lookup"><span data-stu-id="7e386-107">Canonicalizing component and directory separators.</span></span>  
  
-   <span data-ttu-id="7e386-108">Aplicação do diretório atual a um caminho relativo.</span><span class="sxs-lookup"><span data-stu-id="7e386-108">Applying the current directory to a relative path.</span></span>  
  
-   <span data-ttu-id="7e386-109">Avaliação do diretório relativo (`.`) ou do diretório pai (`..`) em um caminho.</span><span class="sxs-lookup"><span data-stu-id="7e386-109">Evaluating the relative directory (`.`) or the parent directory (`..`) in a path.</span></span>  
  
-   <span data-ttu-id="7e386-110">Remoção de determinados caracteres.</span><span class="sxs-lookup"><span data-stu-id="7e386-110">Trimming specified characters.</span></span>  
  
## <a name="the-changes"></a><span data-ttu-id="7e386-111">As alterações</span><span class="sxs-lookup"><span data-stu-id="7e386-111">The changes</span></span>  
 <span data-ttu-id="7e386-112">Começando com os aplicativos direcionados ao [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], a normalização do caminho foi alterada nos seguintes aspectos:</span><span class="sxs-lookup"><span data-stu-id="7e386-112">Starting with apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], path normalization has changed in the following ways:</span></span>  
  
-   <span data-ttu-id="7e386-113">O tempo de execução atende à função [GetFullPathName](https://msdn.microsoft.com/library/windows/desktop/aa364963\(v=vs.85\).aspx) do sistema operacional para normalizar caminhos.</span><span class="sxs-lookup"><span data-stu-id="7e386-113">The runtime defers to the operating system's [GetFullPathName](https://msdn.microsoft.com/library/windows/desktop/aa364963\(v=vs.85\).aspx) function to normalize paths.</span></span>  
  
-   <span data-ttu-id="7e386-114">A normalização não envolve mais a remoção do fim dos segmentos do diretório (como um espaço no fim do nome de um diretório).</span><span class="sxs-lookup"><span data-stu-id="7e386-114">Normalization no longer involves trimming the end of directory segments (such as a space at the end of a directory name).</span></span>  
  
-   <span data-ttu-id="7e386-115">Suporte à sintaxe do caminho do dispositivo em confiança total, incluindo `\\.\` e, para APIs de E/S de arquivo em mscorlib.dll, `\\?\`.</span><span class="sxs-lookup"><span data-stu-id="7e386-115">Support for device path syntax in full trust, including  `\\.\` and, for file I/O APIs   in mscorlib.dll, `\\?\`.</span></span>  
  
-   <span data-ttu-id="7e386-116">O tempo de execução não valida caminhos de sintaxe do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7e386-116">The runtime does not validate device syntax paths.</span></span>  
  
-   <span data-ttu-id="7e386-117">Há suporte ao uso da sintaxe de dispositivo para acessar fluxos de dados alternados.</span><span class="sxs-lookup"><span data-stu-id="7e386-117">The use of device syntax to access alternate data streams is supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="7e386-118">Impacto</span><span class="sxs-lookup"><span data-stu-id="7e386-118">Impact</span></span>  
 <span data-ttu-id="7e386-119">Para os aplicativos direcionados ao [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] ou posteriores, essas alterações estão ativadas por padrão.</span><span class="sxs-lookup"><span data-stu-id="7e386-119">For apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later, these changes are on  by default.</span></span> <span data-ttu-id="7e386-120">Elas devem melhorar o desempenho e ao mesmo tempo permitir que os métodos acessem caminhos anteriormente inacessíveis.</span><span class="sxs-lookup"><span data-stu-id="7e386-120">They should improve performance while allowing methods to access previously inaccessible paths.</span></span>  
  
 <span data-ttu-id="7e386-121">Os aplicativos direcionados ao [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] e versões anteriores, mas que são executados no [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] ou posteriores, não são afetados por essa alteração.</span><span class="sxs-lookup"><span data-stu-id="7e386-121">Apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and earlier versions but are running under the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later are unaffected by this change.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="7e386-122">Redução</span><span class="sxs-lookup"><span data-stu-id="7e386-122">Mitigation</span></span>  
 <span data-ttu-id="7e386-123">Os aplicativos direcionados ao [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] ou posteriores podem recusar essa alteração e usar a normalização herdada adicionando o seguinte à seção [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) do arquivo de configuração de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="7e386-123">Apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later can opt out of this change and use legacy normalization by adding the following to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
</runtime>  
```  
  
 <span data-ttu-id="7e386-124">Os aplicativos direcionados ao [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] ou anteriores, mas que são executados no [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] ou posteriores, podem habilitar essas alterações para normalização do caminho adicionando a seguinte linha à seção [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) do arquivo de configuração de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="7e386-124">Apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] or earlier but are running on the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later can enable the changes to path normalization by adding the following line to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application .configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />    
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7e386-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e386-125">See Also</span></span>  
 [<span data-ttu-id="7e386-126">Alterações de redirecionamento</span><span class="sxs-lookup"><span data-stu-id="7e386-126">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)

