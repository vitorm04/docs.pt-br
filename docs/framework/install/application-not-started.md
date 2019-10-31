---
title: Solução de problemas ' este aplicativo não pôde ser iniciado '
description: Saiba o que fazer se você vir uma caixa de diálogo ' este aplicativo não pôde ser iniciado '.
ms.date: 09/05/2019
ms.openlocfilehash: 2140ab38c29d610634f71305c4337c324e0550d8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092045"
---
# <a name="troubleshooting-a-this-application-could-not-be-started-error-message"></a>Solução de problemas de uma mensagem de erro "este aplicativo não pôde ser iniciado"

Os aplicativos desenvolvidos para o .NET Framework normalmente exigem que uma versão específica do .NET Framework seja instalada em seu sistema. Em alguns casos, você pode tentar executar um aplicativo sem uma versão instalada ou a versão esperada do .NET Framework presente. Isso geralmente produz uma caixa de diálogo de erro semelhante à seguinte:

![Não foi possível iniciar o aplicativo](media/application-not-started/app-could-not-be-started.png)

Isso normalmente indica uma das seguintes condições:

- Uma instalação do .NET Framework no sistema foi corrompida.

- A versão do .NET Framework necessário para seu aplicativo não pode ser detectada.

Para resolver esse problema para que você possa executar o aplicativo, faça o seguinte:

1. Baixe a [ferramenta de reparo de .NET Framework (NetFxRepairTool. exe)](https://www.microsoft.com/download/details.aspx?id=30135). A ferramenta é executada automaticamente quando o download é concluído.

1. Se a ferramenta de reparo de .NET Framework recomendar qualquer ação adicional, como as mostradas na figura a seguir, selecione **Avançar**.

   ![Alterações recomendadas](media/application-not-started/repair-tool-recommended-changes.png)

1. O .NET Framework reparar ferramentas exibe uma caixa de diálogo mostrada na figura a seguir para indicar que as alterações foram concluídas. Deixe a caixa de diálogo aberta enquanto você tenta executar novamente o aplicativo. Isso deverá ter sucesso se a ferramenta de reparo de .NET Framework tiver identificado e corrigido uma instalação de .NET Framework corrompida.

   ![Alterações recomendadas](media/application-not-started/repair-tool-changes-complete.png)

1. Se o aplicativo for executado com êxito, selecione o botão **concluir** . Caso contrário, selecione o botão **Avançar** .

1. Se você selecionou o botão **Avançar** , a ferramenta de reparo de .NET Framework exibirá uma caixa de diálogo semelhante à seguinte. Selecione o botão **concluir** para enviar informações de diagnóstico à Microsoft.

   ![Não é possível resolver o problema](media/application-not-started/repair-tool-no-resolution.png)

1. Se você ainda não puder executar o aplicativo, instale a versão mais recente do .NET Framework com suporte na sua versão do Windows, conforme mostrado na tabela a seguir.

   |Versão do Windows|Instalação do .NET Framework|
   |---|---|
   |Atualização de aniversário do Windows 10 e versões posteriores|[Tempo de execução do .NET Framework 4,8](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows 10, atualização de novembro do Windows 10|[.NET Framework 4.6.2](https://www.microsoft.com/download/details.aspx?id=53345)|
   |Windows 8.1|[Tempo de execução do .NET Framework 4,8](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows 8|[.NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981)|
   |Windows 7 SP1|[Tempo de execução do .NET Framework 4,8](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows Vista SP2|[.NET Framework 4,6](https://www.microsoft.com/download/details.aspx?id=48130)|

   > [!NOTE]
   > .NET Framework 4,8 é pré-instalado no Windows 10 pode ser 2019 atualização.

1. Tentativa de iniciar o aplicativo.

1. Em alguns casos, você pode ver uma caixa de diálogo semelhante à seguinte, que solicita que você instale o .NET Framework 3,5. Selecione **baixar e instalar este recurso** para instalar o .NET Framework 3,5 e, em seguida, inicie o aplicativo novamente.

   ![Não é possível resolver o problema](media/application-not-started/install-3-5.png)

## <a name="see-also"></a>Consulte também

- [Requisitos do sistema do .NET Framework](../get-started/system-requirements.md)
- [Guia de instalação do .NET Framework](index.md)
- [Solução de problemas de instalações e desinstalações bloqueadas do .NET Framework](troubleshoot-blocked-installations-and-uninstallations.md)
