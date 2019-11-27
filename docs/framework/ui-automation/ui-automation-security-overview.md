---
title: Visão geral de segurança da automação de interface do usuário
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, security model
- security model, UI Automation
ms.assetid: 1d853695-973c-48ae-b382-4132ae702805
ms.openlocfilehash: 70d24c3dcc531abcec6d4dce75b5f0b31757e0c0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448775"
---
# <a name="ui-automation-security-overview"></a>Visão geral de segurança da automação de interface do usuário

> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).

Esta visão geral descreve o modelo de segurança para [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] no Windows Vista.

<a name="User_Account_Control"></a>

## <a name="user-account-control"></a>Controle da conta de usuário

A segurança é um dos principais focos do Windows Vista e entre as inovações é a capacidade para os usuários executarem como usuários padrão (não administradores) sem necessariamente ser impedidos de executar aplicativos e serviços que exigem privilégios mais altos.

No Windows Vista, a maioria dos aplicativos é fornecida com um token padrão ou um de administrador. Se um aplicativo não puder ser identificado como um aplicativo administrativo, ele será iniciado como um aplicativo padrão por padrão. Antes que um aplicativo identificado como administrativo possa ser iniciado, o Windows Vista solicita ao usuário o consentimento para executar o aplicativo como elevado. A solicitação de consentimento é exibida por padrão, mesmo que o usuário seja membro do grupo Administradores local, pois os administradores são executados como usuários padrão até que um aplicativo ou componente do sistema que exige permissão de solicitações de credenciais administrativas seja executado.

<a name="Tasks_Requiring_Higher_Privileges"></a>

## <a name="tasks-requiring-higher-privileges"></a>Tarefas que exigem privilégios mais altos

Quando um usuário tenta executar uma tarefa que exige privilégios administrativos, o Windows Vista apresenta uma caixa de diálogo solicitando que o usuário tenha consentimento para continuar. Essa caixa de diálogo é protegida da comunicação entre processos, para que o software mal-intencionado não possa simular a entrada do usuário. Da mesma forma, a tela de logon da área de trabalho normalmente não pode ser acessada por outros processos.

Os clientes de automação da interface do usuário devem se comunicar com outros processos, alguns deles talvez sendo executados em um nível de privilégio mais alto. Os clientes também podem precisar acessar as caixas de diálogo do sistema que normalmente não são visíveis para outros processos. Portanto, os clientes do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] devem ser confiáveis pelo sistema e devem ser executados com privilégios especiais.

Para ser confiável para se comunicar com aplicativos executados em um nível de privilégio mais alto, os aplicativos devem ser assinados.

<a name="Manifest_Files"></a>

## <a name="manifest-files"></a>Arquivos de manifesto

Para obter acesso à interface do usuário do sistema protegido, os aplicativos devem ser criados com um arquivo de manifesto que inclui o atributo `uiAccess` na marca `requestedExecutionLevel`, da seguinte maneira:

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

O valor do atributo `level` neste código é apenas um exemplo.

o `uiAccess` é "false" por padrão; ou seja, se o atributo for omitido ou se não houver nenhum manifesto para o assembly, o aplicativo não será capaz de obter acesso à interface do usuário protegida.
