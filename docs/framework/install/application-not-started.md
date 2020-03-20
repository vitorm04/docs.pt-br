---
title: Solução de problemas 'Este aplicativo não pôde ser iniciado'
description: Saiba o que fazer se você ver uma caixa de diálogo 'Este aplicativo não pode ser iniciado'.
ms.date: 09/05/2019
ms.openlocfilehash: 864c6ea23e9a048f060eee39d904bd4377be5084
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76965900"
---
# <a name="troubleshooting-a-this-application-could-not-be-started-error-message"></a>Solução de problemas uma mensagem de erro 'Este aplicativo não poderia ser iniciado'

Os aplicativos desenvolvidos para o .NET Framework normalmente exigem que uma versão específica do .NET Framework seja instalada no seu sistema. Em alguns casos, você pode tentar executar um aplicativo sem uma versão instalada ou a versão esperada do Quadro .NET presente. Isso muitas vezes produz uma caixa de diálogo de erro como a seguinte:

![Não foi possível iniciar o aplicativo](media/application-not-started/app-could-not-be-started.png)

Isso normalmente indica uma das seguintes condições:

- Uma instalação do .NET Framework no seu sistema ficou corrompida.

- A versão do .NET Framework necessário pelo seu aplicativo não pode ser detectada.

Para resolver esse problema para que você possa executar sua aplicação, faça o seguinte:

1. Baixe a [ferramenta de reparo do framework .NET (NetFxRepairTool.exe)](https://www.microsoft.com/download/details.aspx?id=30135). A ferramenta é executada automaticamente quando o download é concluído.

1. Se a ferramenta de reparo do framework .NET recomendar qualquer ação adicional, como as mostradas na figura a seguir, selecione **Next**.

   ![Alterações recomendadas](media/application-not-started/repair-tool-recommended-changes.png)

1. As ferramentas de reparo do framework .NET exibem uma caixa de diálogo mostrada na figura a seguir para indicar que as alterações estão concluídas. Deixe a caixa de diálogo aberta enquanto tenta executar novamente sua aplicação. Isso deve ser bem-sucedido se a ferramenta de reparo do framework .NET tiver identificado e corrigido uma instalação corrompida do .NET Framework.

   ![Alterações recomendadas](media/application-not-started/repair-tool-changes-complete.png)

1. Se o aplicativo for executado com sucesso, selecione o botão **Concluir.** Caso contrário, selecione o botão **Seguinte.**

1. Se você selecionou o botão **Seguinte,** a Ferramenta de Reparo do Quadro .NET exibirá uma caixa de diálogo como a seguinte. Selecione o botão **Concluir** para enviar informações de diagnóstico para a Microsoft.

   ![Incapaz de resolver o problema](media/application-not-started/repair-tool-no-resolution.png)

1. Se você ainda não puder executar o aplicativo, instale a versão mais recente do .NET Framework suportado pela sua versão do Windows, como mostrado na tabela a seguir.

   |Versão do Windows|Instalação do .NET Framework|
   |---|---|
   |Atualização de aniversário do Windows 10 e versões posteriores|[.NET Framework 4.8 Tempo de execução](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows 10, Windows 10 Atualização de Novembro|[.NET Framework 4.6.2](https://dotnet.microsoft.com/download/dotnet-framework/net462)|
   |Windows 8.1|[.NET Framework 4.8 Tempo de execução](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows 8|[.NET Framework 4.6.1](https://dotnet.microsoft.com/download/dotnet-framework/net461)|
   |Windows 7 SP1|[.NET Framework 4.8 Tempo de execução](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows Vista SP2|[.NET Framework 4.6](https://dotnet.microsoft.com/download/dotnet-framework/net46)|

   > [!NOTE]
   > .NET Framework 4.8 está pré-instalado no Windows 10 May 2019 Update.

1. Tente iniciar o aplicativo.

1. Em alguns casos, você pode ver uma caixa de diálogo como a seguinte, que pede que você instale o .NET Framework 3.5. Selecione **Baixar e instalar esse recurso** para instalar o .NET Framework 3.5 e, em seguida, inicie o aplicativo novamente.

   ![Incapaz de resolver o problema](media/application-not-started/install-3-5.png)

## <a name="see-also"></a>Confira também

- [Requisitos do sistema do .NET Framework](../get-started/system-requirements.md)
- [Guia de instalação do .NET Framework](index.md)
- [Solução de problemas de instalações e desinstalações bloqueadas do .NET Framework](troubleshoot-blocked-installations-and-uninstallations.md)
