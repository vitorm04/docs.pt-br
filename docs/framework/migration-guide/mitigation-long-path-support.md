---
title: "Mitigação: suporte ao caminho longo"
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
ms.assetid: 3cbe2d77-6e2c-4665-a6c5-7000b9ad6890
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 138e96c3d45b79ccf30f6a3d39f0af26a48c0117
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-long-path-support"></a><span data-ttu-id="60740-102">Mitigação: suporte ao caminho longo</span><span class="sxs-lookup"><span data-stu-id="60740-102">Mitigation: Long Path Support</span></span>
<span data-ttu-id="60740-103">A partir dos aplicativos destinados ao [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], os métodos de E/S do sistema de arquivos não gera mais automaticamente um <xref:System.IO.PathTooLongException> se um caminho ou nome de arquivo totalmente qualificado ultrapassar 260 (ou `MAX_PATH`) caracteres.</span><span class="sxs-lookup"><span data-stu-id="60740-103">Starting with apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)],  file system I/O methods not longer automatically throw a <xref:System.IO.PathTooLongException> if a path or fully qualified file name exceeds 260 (or `MAX_PATH`) characters.</span></span> <span data-ttu-id="60740-104">Em vez disso, há suporte para caminhos de até 32 mil caracteres.</span><span class="sxs-lookup"><span data-stu-id="60740-104">Instead, long paths of up to 32K characters are supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="60740-105">Impacto</span><span class="sxs-lookup"><span data-stu-id="60740-105">Impact</span></span>  
 <span data-ttu-id="60740-106">Os aplicativos recompilados para o [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] e que geravam anteriormente um <xref:System.IO.PathTooLongException> automaticamente porque um caminho tinha excedido 260 caracteres agora só gerarão uma <xref:System.IO.PathTooLongException> sob as seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="60740-106">Apps recompiled to target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] and that previously threw a <xref:System.IO.PathTooLongException> automatically because a path exceeded 260 characters will now throw a <xref:System.IO.PathTooLongException> only under the following conditions:</span></span>  
  
-   <span data-ttu-id="60740-107">O tamanho do caminho é superior a <xref:System.Int16.MaxValue?displayProperty=fullName> (32.767) caracteres.</span><span class="sxs-lookup"><span data-stu-id="60740-107">The length of the path is greater than  <xref:System.Int16.MaxValue?displayProperty=fullName> (32,767) characters.</span></span>  
  
-   <span data-ttu-id="60740-108">O sistema operacional retorna `COR_E_PATHTOOLONG` ou seu equivalente.</span><span class="sxs-lookup"><span data-stu-id="60740-108">The operating system returns `COR_E_PATHTOOLONG` or its equivalent.</span></span>  
  
 <span data-ttu-id="60740-109">O comportamento herdado de aplicativos destinados ao [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] e versões anteriores é que o tempo de execução gera automaticamente um <xref:System.IO.PathTooLongException> sempre que um caminho excede 260 caracteres.</span><span class="sxs-lookup"><span data-stu-id="60740-109">The legacy behavior for apps that target the[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and earlier is that the runtime automatically throws a <xref:System.IO.PathTooLongException> whenever a path exceeds 260 characters.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="60740-110">Redução</span><span class="sxs-lookup"><span data-stu-id="60740-110">Mitigation</span></span>  
 <span data-ttu-id="60740-111">Para aplicativos destinados ao [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], você pode recusar o suporte ao caminho longo, se ele não for desejável, adicionando o seguinte à seção [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) do arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="60740-111">For apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], you can opt out of long path support if it is not desirable by adding the following to    to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
```xml  
<runtime>   
   <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=true" />   
</runtime>  
```  
  
 <span data-ttu-id="60740-112">Para aplicativos destinados a versões anteriores do .NET Framework mas executados no [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] ou versão posterior, você pode aceitar o suporte ao caminho longo adicionando o seguinte à seção [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) do arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="60740-112">For apps that target earlier versions of the .NET Framework but run on the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later., you can opt in to long path support by adding the following to    to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
```xml  
<runtime>   
   <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=false" />   
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="60740-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="60740-113">See Also</span></span>  
 [<span data-ttu-id="60740-114">Alterações de redirecionamento</span><span class="sxs-lookup"><span data-stu-id="60740-114">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)

