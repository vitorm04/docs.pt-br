---
title: "Mitigação: cultura e operações de dispatcher em aplicativos WPF"
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
ms.assetid: 455c1452-8ce0-45ae-a092-21fb8edf1cac
caps.latest.revision: 3
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 41fc52679884d547809f1c1e9f47e29eb668cb8e
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-culture-and-dispatcher-operations-in-wpf-apps"></a><span data-ttu-id="fd080-102">Mitigação: cultura e operações de dispatcher em aplicativos WPF</span><span class="sxs-lookup"><span data-stu-id="fd080-102">Mitigation: Culture and Dispatcher Operations in WPF Apps</span></span>
<span data-ttu-id="fd080-103">Em aplicativos direcionados ao .NET Framework 4.6 e ao .NET Framework 4.6.1, alterações nas propriedades <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> ou <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> feitas dentro de um <xref:System.Windows.Threading.Dispatcher> são perdidas ao final da operação de dispatcher.</span><span class="sxs-lookup"><span data-stu-id="fd080-103">In apps that target the .NET Framework 4.6 and the .NET Framework 4.6.1, changes to the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> or <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> properties that are made within a <xref:System.Windows.Threading.Dispatcher> are lost at the end of that dispatcher operation.</span></span> <span data-ttu-id="fd080-104">Da mesma forma, as alterações em <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> ou <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> feitas fora de uma operação de dispatcher podem não ser refletidas quando operação é executada.</span><span class="sxs-lookup"><span data-stu-id="fd080-104">Similarly, changes to <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> or <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> made outside of a dispatcher operation may not be reflected when that operation executes.</span></span>  
  
 <span data-ttu-id="fd080-105">Isso ocorre devido a uma alteração em <xref:System.Threading.ExecutionContext> que faz com que a <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> e a <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> sejam armazenadas no contexto de execução.</span><span class="sxs-lookup"><span data-stu-id="fd080-105">This is due to a change in <xref:System.Threading.ExecutionContext> that causes the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> and <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> to be stored in the execution context.</span></span> <span data-ttu-id="fd080-106">As operações de dispatcher do WPF armazenam o contexto de execução usado para começar a operação e restaurar o contexto anterior quando a operação é concluída.</span><span class="sxs-lookup"><span data-stu-id="fd080-106">WPF dispatcher operations store the execution context used to begin the operation and restore the previous context when the operation is completed.</span></span> <span data-ttu-id="fd080-107">Como <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> e <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> agora fazem parte desse contexto, alterações nelas em uma operação de dispatcher não são persistidas fora da operação.</span><span class="sxs-lookup"><span data-stu-id="fd080-107">Because <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> and <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> are now part of that context, changes to them within a dispatcher operation are not persisted outside of the operation.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="fd080-108">Impacto</span><span class="sxs-lookup"><span data-stu-id="fd080-108">Impact</span></span>  
 <span data-ttu-id="fd080-109">De modo prático, isso significa que alterações nas propriedades <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> e <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> podem não fluir entre os retornos de chamada da interface de usuário do WPF e outro código em um aplicativo WPF.</span><span class="sxs-lookup"><span data-stu-id="fd080-109">Practically, this means that changes to the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> and  <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> properties may not flow between WPF UI callbacks and other code in a WPF application.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="fd080-110">Redução</span><span class="sxs-lookup"><span data-stu-id="fd080-110">Mitigation</span></span>  
 <span data-ttu-id="fd080-111">Os aplicativos afetados por essa alteração podem contorná-la de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="fd080-111">Apps affected by this change may work around it in either of two ways:</span></span>  
  
-   <span data-ttu-id="fd080-112">Armazenando a <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> ou <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> desejada em um campo e verificando em todos os corpos de operação de <xref:System.Windows.Threading.Dispatcher> (incluindo manipuladores de retorno de chamada de eventos da interface do usuário) se a <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> ou <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> correta está definida.</span><span class="sxs-lookup"><span data-stu-id="fd080-112">By storing the desired <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> or  <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> in a field and checking in all <xref:System.Windows.Threading.Dispatcher> operation bodies (including UI event callback handlers) that the correct <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> or  <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> is set.</span></span>  
  
-   <span data-ttu-id="fd080-113">Como a alteração em <xref:System.Threading.ExecutionContext> afeta apenas aplicativos WPF direcionados ao .NET Framework 4.6 ou ao .NET Framework 4.6.1, essa alteração pode ser evitada direcionando ao .NET Framework 4.5.2 ou a uma versão do .NET Framework a partir da 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="fd080-113">Because the change to <xref:System.Threading.ExecutionContext> only affects WPF apps that target the .NET Framework 4.6 or the .NET Framework 4.6.1, this change can be avoided by targeting the .NET Framework 4.5.2 or by targeting a version of the .NET Framework starting with 4.6.2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd080-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fd080-114">See Also</span></span>  
 [<span data-ttu-id="fd080-115">Alterações de redirecionamento</span><span class="sxs-lookup"><span data-stu-id="fd080-115">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)

