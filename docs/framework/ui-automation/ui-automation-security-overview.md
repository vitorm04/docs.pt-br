---
title: Visão geral de segurança da automação de interface do usuário
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, security model
- security model, UI Automation
ms.assetid: 1d853695-973c-48ae-b382-4132ae702805
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: b35014993f10c3a60c16f784e7dd11b9a20f4f4c
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47071928"
---
# <a name="ui-automation-security-overview"></a><span data-ttu-id="09f35-102">Visão geral de segurança da automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="09f35-102">UI Automation Security Overview</span></span>
> [!NOTE]
>  <span data-ttu-id="09f35-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="09f35-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="09f35-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="09f35-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="09f35-105">Esta visão geral descreve o modelo de segurança para [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] em [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)].</span><span class="sxs-lookup"><span data-stu-id="09f35-105">This overview describes the security model for [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] in [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)].</span></span>  
  
<a name="User_Account_Control"></a>   
## <a name="user-account-control"></a><span data-ttu-id="09f35-106">Controle de Conta de Usuário</span><span class="sxs-lookup"><span data-stu-id="09f35-106">User Account Control</span></span>  
 <span data-ttu-id="09f35-107">A segurança é dos principais focos do [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] e entre as inovações é a capacidade dos usuários executem como usuários padrão de (não-administrador) sem necessariamente ser impedidos de executar aplicativos e serviços que exigem privilégios mais altos.</span><span class="sxs-lookup"><span data-stu-id="09f35-107">Security is a major focus of [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] and among the innovations is the ability for users to run as standard (non-administrator) users without necessarily being blocked from running applications and services that require higher privileges.</span></span>  
  
 <span data-ttu-id="09f35-108">No [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)], a maioria dos aplicativos são fornecidos com um padrão ou um token administrativo.</span><span class="sxs-lookup"><span data-stu-id="09f35-108">In [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)], most applications are supplied with either a standard or an administrative token.</span></span> <span data-ttu-id="09f35-109">Se um aplicativo não pode ser identificado como um aplicativo administrativo, ele é iniciado como um aplicativo padrão por padrão.</span><span class="sxs-lookup"><span data-stu-id="09f35-109">If an application cannot be identified as an administrative application, it is launched as a standard application by default.</span></span> <span data-ttu-id="09f35-110">Antes de um aplicativo identificado como administrativo pode ser inicializado, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] solicita ao usuário permissão executar o aplicativo com privilégios elevados.</span><span class="sxs-lookup"><span data-stu-id="09f35-110">Before an application identified as administrative can be launched, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] prompts the user for consent to run the application as elevated.</span></span> <span data-ttu-id="09f35-111">A solicitação de consentimento é exibida por padrão, mesmo se o usuário é membro do grupo de administradores local, porque os administradores executem como usuários padrão até que um aplicativo ou componente do sistema que requer credenciais administrativas solicita permissão para executar.</span><span class="sxs-lookup"><span data-stu-id="09f35-111">The consent prompt is displayed by default, even if the user is a member of the local Administrators group, because administrators run as standard users until an application or system component that requires administrative credentials requests permission to run.</span></span>  
  
<a name="Tasks_Requiring_Higher_Privileges"></a>   
## <a name="tasks-requiring-higher-privileges"></a><span data-ttu-id="09f35-112">Tarefas que requerem privilégios mais altos</span><span class="sxs-lookup"><span data-stu-id="09f35-112">Tasks Requiring Higher Privileges</span></span>  
 <span data-ttu-id="09f35-113">Quando um usuário tenta executar uma tarefa que requer privilégios administrativos, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] apresenta uma caixa de diálogo perguntando ao usuário consentimento continuar.</span><span class="sxs-lookup"><span data-stu-id="09f35-113">When a user attempts to perform a task that requires administrative privileges, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] presents a dialog box asking the user for consent to continue.</span></span> <span data-ttu-id="09f35-114">Essa caixa de diálogo está protegida contra a comunicação entre processos, para que o software mal-intencionado não pode simular a entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="09f35-114">This dialog box is protected from cross-process communication, so that malicious software cannot simulate user input.</span></span> <span data-ttu-id="09f35-115">Da mesma forma, a tela de logon da área de trabalho normalmente não pode ser acessada por outros processos.</span><span class="sxs-lookup"><span data-stu-id="09f35-115">Similarly, the desktop logon screen cannot normally be accessed by other processes.</span></span>  
  
 <span data-ttu-id="09f35-116">Clientes de automação de interface do usuário devem se comunicar com outros processos, alguns deles talvez sendo executados em um nível de privilégio mais alto.</span><span class="sxs-lookup"><span data-stu-id="09f35-116">UI Automation clients must communicate with other processes, some of them perhaps running at a higher privilege level.</span></span> <span data-ttu-id="09f35-117">Os clientes também podem precisam acessar as caixas de diálogo do sistema que não são normalmente visíveis para outros processos.</span><span class="sxs-lookup"><span data-stu-id="09f35-117">Clients also might need access to the system dialog boxes that are not normally visible to other processes.</span></span> <span data-ttu-id="09f35-118">Portanto, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] clientes deve ser confiável pelo sistema e devem executar com privilégios especiais.</span><span class="sxs-lookup"><span data-stu-id="09f35-118">Therefore, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] clients must be trusted by the system, and must run with special privileges.</span></span>  
  
 <span data-ttu-id="09f35-119">Para ser confiável para se comunicar com aplicativos em execução em um nível de privilégio mais alto, os aplicativos devem ser assinados.</span><span class="sxs-lookup"><span data-stu-id="09f35-119">To be trusted to communicate with applications running at a higher privilege level, applications must be signed.</span></span>  
  
<a name="Manifest_Files"></a>   
## <a name="manifest-files"></a><span data-ttu-id="09f35-120">Arquivos de manifesto</span><span class="sxs-lookup"><span data-stu-id="09f35-120">Manifest Files</span></span>  
 <span data-ttu-id="09f35-121">Para obter acesso ao sistema protegido [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], aplicativos devem ser criados com um arquivo de manifesto que inclui um atributo especial no arquivo de manifesto.</span><span class="sxs-lookup"><span data-stu-id="09f35-121">To gain access to the protected system [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], applications must be built with a manifest file that includes a special attribute in the manifest file.</span></span> <span data-ttu-id="09f35-122">Isso `uiAccess` atributo está incluído no `requestedExecutionLevel` marcar, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="09f35-122">This `uiAccess` attribute is included in the `requestedExecutionLevel` tag, as follows:</span></span>  
  
 `<trustInfo xmlns="urn:0073chemas-microsoft-com:asm.v3">`  
  
 `<security>`  
  
 `<requestedPrivileges>`  
  
 `<requestedExecutionLevel`  
  
 `level="highestAvailable"`  
  
 `UIAccess="true" />`  
  
 `</requestedPrivileges>`  
  
 `</security>`  
  
 `</trustInfo>`  
  
 <span data-ttu-id="09f35-123">O valor da `level` atributo nesse código é apenas um exemplo.</span><span class="sxs-lookup"><span data-stu-id="09f35-123">The value of the `level` attribute in this code is an example only.</span></span>  
  
 <span data-ttu-id="09f35-124">`UIAccess` é "false" por padrão. ou seja, se o atributo for omitido ou se não houver nenhum manifesto do assembly, o aplicativo não será capaz de obter acesso protegido [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="09f35-124">`UIAccess` is "false" by default; that is, if the attribute is omitted, or if there is no manifest for the assembly, the application will not be able to gain access to protected [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].</span></span>  
  
 <span data-ttu-id="09f35-125">Para obter mais informações sobre [!INCLUDE[TLA#tla_longhorn2](../../../includes/tlasharptla-longhorn2-md.md)] segurança, na assinatura de aplicativos e sobre como criar manifestos de assembly, consulte "Desenvolvedor práticas recomendadas e diretrizes para aplicativos em um ambiente menos privilegiado" em [MSDN](https://msdn.microsoft.com/library/default.asp?url=/library/dnlong/html/AccProtVista.asp).</span><span class="sxs-lookup"><span data-stu-id="09f35-125">For more information on [!INCLUDE[TLA#tla_longhorn2](../../../includes/tlasharptla-longhorn2-md.md)] security, on signing applications, and on creating assembly manifests, see "Developer Best Practices and Guidelines for Applications in a Least Privileged Environment" on  [MSDN](https://msdn.microsoft.com/library/default.asp?url=/library/dnlong/html/AccProtVista.asp).</span></span>
