---
title: Visão geral de segurança da automação de interface do usuário
description: Leia uma visão geral do modelo de segurança para automação da interface do usuário da Microsoft. Entenda o controle de conta de usuário, as tarefas que exigem privilégios mais altos e arquivos de manifesto.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, security model
- security model, UI Automation
ms.assetid: 1d853695-973c-48ae-b382-4132ae702805
ms.openlocfilehash: d483f282db8ce8e5653d6d83361fa44df05f63f5
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163145"
---
# <a name="ui-automation-security-overview"></a><span data-ttu-id="73c46-104">Visão geral de segurança da automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="73c46-104">UI Automation Security Overview</span></span>

> [!NOTE]
> <span data-ttu-id="73c46-105">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="73c46-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="73c46-106">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="73c46-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>

<span data-ttu-id="73c46-107">Esta visão geral descreve o modelo de segurança para o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] no Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="73c46-107">This overview describes the security model for [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] in Windows Vista.</span></span>

<a name="User_Account_Control"></a>

## <a name="user-account-control"></a><span data-ttu-id="73c46-108">Controle de Conta de Usuário</span><span class="sxs-lookup"><span data-stu-id="73c46-108">User Account Control</span></span>

<span data-ttu-id="73c46-109">A segurança é um dos principais focos do Windows Vista e entre as inovações é a capacidade para os usuários executarem como usuários padrão (não administradores) sem necessariamente ser impedidos de executar aplicativos e serviços que exigem privilégios mais altos.</span><span class="sxs-lookup"><span data-stu-id="73c46-109">Security is a major focus of Windows Vista and among the innovations is the ability for users to run as standard (non-administrator) users without necessarily being blocked from running applications and services that require higher privileges.</span></span>

<span data-ttu-id="73c46-110">No Windows Vista, a maioria dos aplicativos é fornecida com um token padrão ou um de administrador.</span><span class="sxs-lookup"><span data-stu-id="73c46-110">In Windows Vista, most applications are supplied with either a standard or an administrative token.</span></span> <span data-ttu-id="73c46-111">Se um aplicativo não puder ser identificado como um aplicativo administrativo, ele será iniciado como um aplicativo padrão por padrão.</span><span class="sxs-lookup"><span data-stu-id="73c46-111">If an application cannot be identified as an administrative application, it is launched as a standard application by default.</span></span> <span data-ttu-id="73c46-112">Antes que um aplicativo identificado como administrativo possa ser iniciado, o Windows Vista solicita ao usuário o consentimento para executar o aplicativo como elevado.</span><span class="sxs-lookup"><span data-stu-id="73c46-112">Before an application identified as administrative can be launched, Windows Vista prompts the user for consent to run the application as elevated.</span></span> <span data-ttu-id="73c46-113">A solicitação de consentimento é exibida por padrão, mesmo que o usuário seja membro do grupo Administradores local, pois os administradores são executados como usuários padrão até que um aplicativo ou componente do sistema que exige permissão de solicitações de credenciais administrativas seja executado.</span><span class="sxs-lookup"><span data-stu-id="73c46-113">The consent prompt is displayed by default, even if the user is a member of the local Administrators group, because administrators run as standard users until an application or system component that requires administrative credentials requests permission to run.</span></span>

<a name="Tasks_Requiring_Higher_Privileges"></a>

## <a name="tasks-requiring-higher-privileges"></a><span data-ttu-id="73c46-114">Tarefas que exigem privilégios mais altos</span><span class="sxs-lookup"><span data-stu-id="73c46-114">Tasks Requiring Higher Privileges</span></span>

<span data-ttu-id="73c46-115">Quando um usuário tenta executar uma tarefa que exige privilégios administrativos, o Windows Vista apresenta uma caixa de diálogo solicitando que o usuário tenha consentimento para continuar.</span><span class="sxs-lookup"><span data-stu-id="73c46-115">When a user attempts to perform a task that requires administrative privileges, Windows Vista presents a dialog box asking the user for consent to continue.</span></span> <span data-ttu-id="73c46-116">Essa caixa de diálogo é protegida da comunicação entre processos, para que o software mal-intencionado não possa simular a entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="73c46-116">This dialog box is protected from cross-process communication, so that malicious software cannot simulate user input.</span></span> <span data-ttu-id="73c46-117">Da mesma forma, a tela de logon da área de trabalho normalmente não pode ser acessada por outros processos.</span><span class="sxs-lookup"><span data-stu-id="73c46-117">Similarly, the desktop logon screen cannot normally be accessed by other processes.</span></span>

<span data-ttu-id="73c46-118">Os clientes de automação da interface do usuário devem se comunicar com outros processos, alguns deles talvez sendo executados em um nível de privilégio mais alto.</span><span class="sxs-lookup"><span data-stu-id="73c46-118">UI Automation clients must communicate with other processes, some of them perhaps running at a higher privilege level.</span></span> <span data-ttu-id="73c46-119">Os clientes também podem precisar acessar as caixas de diálogo do sistema que normalmente não são visíveis para outros processos.</span><span class="sxs-lookup"><span data-stu-id="73c46-119">Clients also might need access to the system dialog boxes that are not normally visible to other processes.</span></span> <span data-ttu-id="73c46-120">Portanto, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] os clientes devem ser confiáveis pelo sistema e devem ser executados com privilégios especiais.</span><span class="sxs-lookup"><span data-stu-id="73c46-120">Therefore, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] clients must be trusted by the system, and must run with special privileges.</span></span>

<span data-ttu-id="73c46-121">Para ser confiável para se comunicar com aplicativos executados em um nível de privilégio mais alto, os aplicativos devem ser assinados.</span><span class="sxs-lookup"><span data-stu-id="73c46-121">To be trusted to communicate with applications running at a higher privilege level, applications must be signed.</span></span>

<a name="Manifest_Files"></a>

## <a name="manifest-files"></a><span data-ttu-id="73c46-122">Arquivos de manifesto</span><span class="sxs-lookup"><span data-stu-id="73c46-122">Manifest Files</span></span>

<span data-ttu-id="73c46-123">Para obter acesso à interface do usuário do sistema protegido, os aplicativos devem ser criados com um arquivo de manifesto que inclui o `uiAccess` atributo na `requestedExecutionLevel` marca, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="73c46-123">To gain access to the protected system UI, applications must be built with a manifest file that includes the `uiAccess` attribute in the `requestedExecutionLevel` tag, as follows:</span></span>

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

<span data-ttu-id="73c46-124">O valor do `level` atributo neste código é apenas um exemplo.</span><span class="sxs-lookup"><span data-stu-id="73c46-124">The value of the `level` attribute in this code is an example only.</span></span>

<span data-ttu-id="73c46-125">`uiAccess`é "false" por padrão; ou seja, se o atributo for omitido ou se não houver nenhum manifesto para o assembly, o aplicativo não será capaz de obter acesso à interface do usuário protegida.</span><span class="sxs-lookup"><span data-stu-id="73c46-125">`uiAccess` is "false" by default; that is, if the attribute is omitted, or if there is no manifest for the assembly, the application will not be able to gain access to protected UI.</span></span>
