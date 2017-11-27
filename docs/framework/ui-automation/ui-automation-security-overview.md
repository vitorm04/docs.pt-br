---
title: "Visão geral de segurança da automação de interface do usuário"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, security model
- security model, UI Automation
ms.assetid: 1d853695-973c-48ae-b382-4132ae702805
caps.latest.revision: "23"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: ee3847164ecdc9b9868d806b5a1394ffca0bbd31
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ui-automation-security-overview"></a>Visão geral de segurança da automação de interface do usuário
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Esta visão geral descreve o modelo de segurança para [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] em [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)].  
  
<a name="User_Account_Control"></a>   
## <a name="user-account-control"></a>Controle de Conta de Usuário  
 A segurança é um foco principal de [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] e entre as inovações é a capacidade dos usuários executar como usuários padrão de (não administrador) sem necessariamente ser impedidos de executar aplicativos e serviços que exigem privilégios mais altos.  
  
 Em [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)], a maioria dos aplicativos são fornecidos com um padrão ou um token administrativo. Se um aplicativo não pode ser identificado como um aplicativo administrativo é iniciado como um aplicativo por padrão. Pode ser iniciado antes que um aplicativo identificado como administrativo, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] solicita ao usuário permissão executar o aplicativo com privilégios elevados. A solicitação de consentimento é exibida por padrão, mesmo se o usuário for um membro do grupo de administradores local, como os administradores são executados como usuários padrão até que um aplicativo ou componente do sistema que requer credenciais administrativas solicite permissão para executar.  
  
<a name="Tasks_Requiring_Higher_Privileges"></a>   
## <a name="tasks-requiring-higher-privileges"></a>Tarefas que requerem privilégios superiores  
 Quando um usuário tenta executar uma tarefa que requer privilégios administrativos, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] apresenta uma caixa de diálogo perguntando ao usuário permissão continuar. Essa caixa de diálogo é protegida da comunicação entre processos, para que o software mal-intencionado não pode simular a entrada do usuário. Da mesma forma, a tela de logon da área de trabalho normalmente não pode ser acessada por outros processos.  
  
 Clientes de automação de interface do usuário devem se comunicar com outros processos, alguns deles talvez sendo executados em um nível de privilégio mais alto. Os clientes também podem precisam acessar as caixas de diálogo do sistema que não são normalmente visíveis para outros processos. Portanto, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] clientes devem ser confiáveis pelo sistema e devem executar com privilégios especiais.  
  
 Para serem confiáveis para se comunicar com aplicativos executados em um nível de privilégio mais alto, os aplicativos devem ser assinados.  
  
<a name="Manifest_Files"></a>   
## <a name="manifest-files"></a>Arquivos de manifesto  
 Para obter acesso ao sistema protegido [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], aplicativos devem ser criados com um arquivo de manifesto que inclui um atributo especial no arquivo de manifesto. Isso `uiAccess` atributo está incluído no `requestedExecutionLevel` marca, da seguinte maneira:  
  
 `<trustInfo xmlns="urn:0073chemas-microsoft-com:asm.v3">`  
  
 `<security>`  
  
 `<requestedPrivileges>`  
  
 `<requestedExecutionLevel`  
  
 `level="highestAvailable"`  
  
 `UIAccess="true" />`  
  
 `</requestedPrivileges>`  
  
 `</security>`  
  
 `</trustInfo>`  
  
 O valor de `level` atributo nesse código é apenas um exemplo.  
  
 `UIAccess`é "falso" por padrão. ou seja, se o atributo for omitido ou se não houver nenhum manifesto do assembly, o aplicativo não será capaz de obter acesso protegido [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
 Para obter mais informações sobre [!INCLUDE[TLA#tla_longhorn2](../../../includes/tlasharptla-longhorn2-md.md)] segurança, sobre assinatura de aplicativos e sobre como criar manifestos de assembly, consulte "Desenvolvedor melhores práticas recomendadas e diretrizes para aplicativos em um ambiente menos privilegiado" em [MSDN](http://msdn.microsoft.com/library/default.asp?url=/library/dnlong/html/AccProtVista.asp).
