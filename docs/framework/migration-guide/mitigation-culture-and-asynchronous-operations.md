---
title: "Para saber mais, confira Mitigação: cultura e operações assíncronas"
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
ms.assetid: d2cdb578-9923-47df-9ffd-5865333ac1a4
caps.latest.revision: 4
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: debcae8281c832d2815e1b9896fbbcb725c8ffc3
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-culture-and-asynchronous-operations"></a><span data-ttu-id="902fb-102">Para saber mais, confira Mitigação: cultura e operações assíncronas</span><span class="sxs-lookup"><span data-stu-id="902fb-102">Mitigation: Culture and Asynchronous Operations</span></span>
<span data-ttu-id="902fb-103">Em aplicativos direcionados ao [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] e versões posteriores, <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> e <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> são armazenados no <xref:System.Threading.ExecutionContext> de um thread, que flui por operações assíncronas.</span><span class="sxs-lookup"><span data-stu-id="902fb-103">For apps that target the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] and later versions, <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> and <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> are stored in a thread's <xref:System.Threading.ExecutionContext>, which flows across asynchronous operations.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="902fb-104">Impacto</span><span class="sxs-lookup"><span data-stu-id="902fb-104">Impact</span></span>  
 <span data-ttu-id="902fb-105">Como resultado dessa alteração, alterações no <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> ou <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> são refletidas nas tarefas que são executadas posteriormente de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="902fb-105">As a result of this change, changes to the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> or <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> are reflected in tasks which are later run asynchronously.</span></span> <span data-ttu-id="902fb-106">Isso é diferente do comportamento das versões anteriores do .NET Framework, que redefiniria <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> e <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> para o padrão do sistema em todas as tarefas assíncronas.</span><span class="sxs-lookup"><span data-stu-id="902fb-106">This differs from the behavior of previous .NET Framework versions, which would reset <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> and <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> to the system default  in all asynchronous tasks.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="902fb-107">Redução</span><span class="sxs-lookup"><span data-stu-id="902fb-107">Mitigation</span></span>  
 <span data-ttu-id="902fb-108">Os aplicativos afetados por essa alteração podem contorná-la de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="902fb-108">Apps affected by this change can work around it in either of two ways:</span></span>  
  
-   <span data-ttu-id="902fb-109">Definindo explicitamente a propriedade <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> ou <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> desejada como a primeira operação em uma tarefa assíncrona.</span><span class="sxs-lookup"><span data-stu-id="902fb-109">By explicitly setting the desired <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> or <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> property as the first operation in an asynchronous task.</span></span>  
  
-   <span data-ttu-id="902fb-110">Aceitando o comportamento antigo de não fluir <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> e <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> adicionando o seguinte elemento `AppContextSwitchOverrides` ao arquivo de configuração do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="902fb-110">By opting into the old behavior of not flowing <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> and <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> by adding the following `AppContextSwitchOverrides` element to the application's configuration file:</span></span>  
  
    ```xml  
    <configuration>  
        <runtime>  
            <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />  
        </runtime>  
    </configuration>  
    ```  
  
-   <span data-ttu-id="902fb-111">Aceitando o comportamento antigo de não fluir <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> e <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> definindo a seguinte opção de compatibilidade de maneira programática:</span><span class="sxs-lookup"><span data-stu-id="902fb-111">By opting into the old behavior of not flowing <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> and <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> by setting the following compatibility switch programatically:</span></span>  
  
    ```csharp  
    AppContext.SetSwitch("Switch.System.Globalization.NoAsyncCurrentCulture", true);  
    ```  
  
    ```vb  
    AppContext.SetSwitch("Switch.System.Globalization.NoAsyncCurrentCulture", true)  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="902fb-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="902fb-112">See Also</span></span>  
 [<span data-ttu-id="902fb-113">Alterações de redirecionamento</span><span class="sxs-lookup"><span data-stu-id="902fb-113">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)

