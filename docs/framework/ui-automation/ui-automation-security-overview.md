---
title: Visão geral de segurança da automação de interface do usuário
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, security model
- security model, UI Automation
ms.assetid: 1d853695-973c-48ae-b382-4132ae702805
ms.openlocfilehash: 8b798aef528cccdedb1fcaa53c1782632037600d
ms.sourcegitcommit: 77e33b682db39955e331b8e8eda4ef1925a24e78
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70133780"
---
# <a name="ui-automation-security-overview"></a><span data-ttu-id="a1f52-102">Visão geral de segurança da automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="a1f52-102">UI Automation Security Overview</span></span>

> [!NOTE]
> <span data-ttu-id="a1f52-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="a1f52-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="a1f52-104">Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="a1f52-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>

<span data-ttu-id="a1f52-105">Esta visão geral descreve o modelo de [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] segurança [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)]para o no.</span><span class="sxs-lookup"><span data-stu-id="a1f52-105">This overview describes the security model for [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] in [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)].</span></span>

<a name="User_Account_Control"></a>

## <a name="user-account-control"></a><span data-ttu-id="a1f52-106">Controle de Conta de Usuário</span><span class="sxs-lookup"><span data-stu-id="a1f52-106">User Account Control</span></span>

<span data-ttu-id="a1f52-107">A segurança é um foco [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] principal e, entre as inovações, é a capacidade dos usuários de executar como usuários padrão (não administradores), sem necessariamente ser impedido de executar aplicativos e serviços que exigem privilégios mais altos.</span><span class="sxs-lookup"><span data-stu-id="a1f52-107">Security is a major focus of [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] and among the innovations is the ability for users to run as standard (non-administrator) users without necessarily being blocked from running applications and services that require higher privileges.</span></span>

<span data-ttu-id="a1f52-108">No [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)], a maioria dos aplicativos é fornecida com um token padrão ou um de administrador.</span><span class="sxs-lookup"><span data-stu-id="a1f52-108">In [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)], most applications are supplied with either a standard or an administrative token.</span></span> <span data-ttu-id="a1f52-109">Se um aplicativo não puder ser identificado como um aplicativo administrativo, ele será iniciado como um aplicativo padrão por padrão.</span><span class="sxs-lookup"><span data-stu-id="a1f52-109">If an application cannot be identified as an administrative application, it is launched as a standard application by default.</span></span> <span data-ttu-id="a1f52-110">Antes que um aplicativo identificado como administrativo possa ser iniciado [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] , o solicita ao usuário o consentimento para executar o aplicativo como elevado.</span><span class="sxs-lookup"><span data-stu-id="a1f52-110">Before an application identified as administrative can be launched, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] prompts the user for consent to run the application as elevated.</span></span> <span data-ttu-id="a1f52-111">A solicitação de consentimento é exibida por padrão, mesmo que o usuário seja membro do grupo Administradores local, pois os administradores são executados como usuários padrão até que um aplicativo ou componente do sistema que exige permissão de solicitações de credenciais administrativas seja executado.</span><span class="sxs-lookup"><span data-stu-id="a1f52-111">The consent prompt is displayed by default, even if the user is a member of the local Administrators group, because administrators run as standard users until an application or system component that requires administrative credentials requests permission to run.</span></span>

<a name="Tasks_Requiring_Higher_Privileges"></a>

## <a name="tasks-requiring-higher-privileges"></a><span data-ttu-id="a1f52-112">Tarefas que exigem privilégios mais altos</span><span class="sxs-lookup"><span data-stu-id="a1f52-112">Tasks Requiring Higher Privileges</span></span>

<span data-ttu-id="a1f52-113">Quando um usuário tenta executar uma tarefa que requer privilégios administrativos, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] o apresenta uma caixa de diálogo solicitando que o usuário tenha consentimento para continuar.</span><span class="sxs-lookup"><span data-stu-id="a1f52-113">When a user attempts to perform a task that requires administrative privileges, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] presents a dialog box asking the user for consent to continue.</span></span> <span data-ttu-id="a1f52-114">Essa caixa de diálogo é protegida da comunicação entre processos, para que o software mal-intencionado não possa simular a entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="a1f52-114">This dialog box is protected from cross-process communication, so that malicious software cannot simulate user input.</span></span> <span data-ttu-id="a1f52-115">Da mesma forma, a tela de logon da área de trabalho normalmente não pode ser acessada por outros processos.</span><span class="sxs-lookup"><span data-stu-id="a1f52-115">Similarly, the desktop logon screen cannot normally be accessed by other processes.</span></span>

<span data-ttu-id="a1f52-116">Os clientes de automação da interface do usuário devem se comunicar com outros processos, alguns deles talvez sendo executados em um nível de privilégio mais alto.</span><span class="sxs-lookup"><span data-stu-id="a1f52-116">UI Automation clients must communicate with other processes, some of them perhaps running at a higher privilege level.</span></span> <span data-ttu-id="a1f52-117">Os clientes também podem precisar acessar as caixas de diálogo do sistema que normalmente não são visíveis para outros processos.</span><span class="sxs-lookup"><span data-stu-id="a1f52-117">Clients also might need access to the system dialog boxes that are not normally visible to other processes.</span></span> <span data-ttu-id="a1f52-118">Portanto, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] os clientes devem ser confiáveis pelo sistema e devem ser executados com privilégios especiais.</span><span class="sxs-lookup"><span data-stu-id="a1f52-118">Therefore, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] clients must be trusted by the system, and must run with special privileges.</span></span>

<span data-ttu-id="a1f52-119">Para ser confiável para se comunicar com aplicativos executados em um nível de privilégio mais alto, os aplicativos devem ser assinados.</span><span class="sxs-lookup"><span data-stu-id="a1f52-119">To be trusted to communicate with applications running at a higher privilege level, applications must be signed.</span></span>

<a name="Manifest_Files"></a>

## <a name="manifest-files"></a><span data-ttu-id="a1f52-120">Arquivos de manifesto</span><span class="sxs-lookup"><span data-stu-id="a1f52-120">Manifest Files</span></span>

<span data-ttu-id="a1f52-121">Para obter acesso à interface do usuário do sistema protegido, os aplicativos devem ser criados com um arquivo de `uiAccess` manifesto que inclui `requestedExecutionLevel` o atributo na marca, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="a1f52-121">To gain access to the protected system UI, applications must be built with a manifest file that includes the `uiAccess` attribute in the `requestedExecutionLevel` tag, as follows:</span></span>

```xml
<trustInfo xmlns="urn:schemas-microsoft-com:asm.v3">
  <security>
    <requestedPrivileges>
      <requestedExecutionLevel
        level="highestAvailable"
        uiAccess="true" />
    </requestedPrivileges>
  </security>
</trustInfo>
```

<span data-ttu-id="a1f52-122">O valor do `level` atributo neste código é apenas um exemplo.</span><span class="sxs-lookup"><span data-stu-id="a1f52-122">The value of the `level` attribute in this code is an example only.</span></span>

<span data-ttu-id="a1f52-123">`uiAccess`é "false" por padrão; ou seja, se o atributo for omitido ou se não houver nenhum manifesto para o assembly, o aplicativo não será capaz de obter acesso à interface do usuário protegida.</span><span class="sxs-lookup"><span data-stu-id="a1f52-123">`uiAccess` is "false" by default; that is, if the attribute is omitted, or if there is no manifest for the assembly, the application will not be able to gain access to protected UI.</span></span>
