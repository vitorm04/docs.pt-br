---
title: Instalando o Enfileiramento de Mensagens (MSMQ)
ms.date: 03/30/2017
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
ms.openlocfilehash: 118143f2d434e9f4399c3e9141743fc0254b61ab
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039618"
---
# <a name="installing-message-queuing-msmq"></a>Instalando o Enfileiramento de Mensagens (MSMQ)
Os procedimentos a seguir mostram como instalar o Enfileiramento de Mensagens 4.0 e o Enfileiramento de Mensagens 3.0.  
  
> [!NOTE]
> O Enfileiramento de Mensagens 4.0 não está disponível no [!INCLUDE[wxp](../../../../includes/wxp-md.md)] nem no [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].  
  
#### <a name="to-install-message-queuing-40-on-windows-server-2008-or-windows-server-2008-r2"></a>Para instalar o Enfileiramento de Mensagens 4.0 no Windows Server 2008 ou no Windows Server 2008 R2  
  
1. Em Gerenciador do Servidor, clique em **recursos**.  
  
2. No painel direito, em resumo de **recursos**, clique em **Adicionar recursos**.  
  
3. Na janela resultante, expanda enfileiramento de **mensagens**.  
  
4. Expanda Serviços de enfileiramento de **mensagens**.  
  
5. Clique em **integração de serviços de diretório** (para computadores ingressados em um domínio) e clique em **suporte http**.  
  
6. Clique em **Avançar**e em **instalar**.  
  
#### <a name="to-install-message-queuing-40-on-windows-7-or-windows-vista"></a>Para instalar o Enfileiramento de Mensagens 4.0 no Windows 7 ou no Windows Vista  
  
1. Abra **Painel de Controle**.  
  
2. Clique em **programas** e, em **programas e recursos**, clique em **ativar e desativar recursos do Windows**.  
  
3. Expanda o Servidor Fila MSMQ, expanda o Server Core Fila MSMQ e marque as caixas de seleção dos seguintes recursos do Enfileiramento de Mensagens a serem instalados:  
  
    - Integração de MSMQ com os Serviços de Domínio Active Directory (para computadores ingressos em um Domínio).  
  
    - Suporte a HTTP do MSMQ.  
  
4. Clique em **OK**.  
  
5. Se for solicitado que você reinicie o computador, clique em **OK** para concluir a instalação.  
  
#### <a name="to-install-message-queuing-30-on-windows-xp-and-windows-server-2003"></a>Para instalar o Enfileiramento de Mensagens 3.0 no Windows XP e no Windows Server 2003  
  
1. Abra **Painel de Controle**.  
  
2. Clique em **Adicionar remover programas** e, em seguida, clique em **adicionar componentes do Windows**.  
  
3. Selecione enfileiramento de mensagens e clique em **detalhes**.  
  
    > [!NOTE]
    > Se você estiver executando o [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], selecione Servidor de Aplicativos para acessar o Enfileiramento de Mensagens.  
  
4. Verifique se a opção Suporte a HTTP do MSMQ está selecionada na página de detalhes.  
  
5. Clique em **OK** para sair da página de detalhes e clique em **Avançar**. Conclua a instalação.  
  
6. Se for solicitado que você reinicie o computador, clique em **OK** para concluir a instalação.  
  
## <a name="see-also"></a>Consulte também

- [Instruções de configuração](../../../../docs/framework/wcf/samples/set-up-instructions.md)
