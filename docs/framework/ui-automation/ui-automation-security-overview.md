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
# <a name="ui-automation-security-overview"></a>Visão geral de segurança da automação de interface do usuário

> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.

Esta visão geral descreve o modelo de [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] segurança [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)]para o no.

<a name="User_Account_Control"></a>

## <a name="user-account-control"></a>Controle de Conta de Usuário

A segurança é um foco [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] principal e, entre as inovações, é a capacidade dos usuários de executar como usuários padrão (não administradores), sem necessariamente ser impedido de executar aplicativos e serviços que exigem privilégios mais altos.

No [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)], a maioria dos aplicativos é fornecida com um token padrão ou um de administrador. Se um aplicativo não puder ser identificado como um aplicativo administrativo, ele será iniciado como um aplicativo padrão por padrão. Antes que um aplicativo identificado como administrativo possa ser iniciado [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] , o solicita ao usuário o consentimento para executar o aplicativo como elevado. A solicitação de consentimento é exibida por padrão, mesmo que o usuário seja membro do grupo Administradores local, pois os administradores são executados como usuários padrão até que um aplicativo ou componente do sistema que exige permissão de solicitações de credenciais administrativas seja executado.

<a name="Tasks_Requiring_Higher_Privileges"></a>

## <a name="tasks-requiring-higher-privileges"></a>Tarefas que exigem privilégios mais altos

Quando um usuário tenta executar uma tarefa que requer privilégios administrativos, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] o apresenta uma caixa de diálogo solicitando que o usuário tenha consentimento para continuar. Essa caixa de diálogo é protegida da comunicação entre processos, para que o software mal-intencionado não possa simular a entrada do usuário. Da mesma forma, a tela de logon da área de trabalho normalmente não pode ser acessada por outros processos.

Os clientes de automação da interface do usuário devem se comunicar com outros processos, alguns deles talvez sendo executados em um nível de privilégio mais alto. Os clientes também podem precisar acessar as caixas de diálogo do sistema que normalmente não são visíveis para outros processos. Portanto, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] os clientes devem ser confiáveis pelo sistema e devem ser executados com privilégios especiais.

Para ser confiável para se comunicar com aplicativos executados em um nível de privilégio mais alto, os aplicativos devem ser assinados.

<a name="Manifest_Files"></a>

## <a name="manifest-files"></a>Arquivos de manifesto

Para obter acesso à interface do usuário do sistema protegido, os aplicativos devem ser criados com um arquivo de `uiAccess` manifesto que inclui `requestedExecutionLevel` o atributo na marca, da seguinte maneira:

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

O valor do `level` atributo neste código é apenas um exemplo.

`uiAccess`é "false" por padrão; ou seja, se o atributo for omitido ou se não houver nenhum manifesto para o assembly, o aplicativo não será capaz de obter acesso à interface do usuário protegida.
