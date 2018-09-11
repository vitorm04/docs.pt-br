---
title: Perfil seguro confiável
ms.date: 03/30/2017
ms.assetid: 921edc41-e91b-40f9-bde9-b6148b633e61
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: dfdafbcdc461c80192e310a86d5bff50f0885283
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44354061"
---
# <a name="reliable-secure-profile"></a>Perfil seguro confiável
Este exemplo demonstra como compor o WCF e [perfil seguro confiável](https://go.microsoft.com/fwlink/?LinkId=178140) (RSP). Este exemplo demonstra a implementação de um [fazer Conexão](https://go.microsoft.com/fwlink/?LinkId=178141) canal que pode ser composto em conjunto com o sistema de mensagens confiável e, opcionalmente, um canal seguro para criar uma associação segura confiável com base na especificação RSP.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ReliableSecureProfile`  
  
## <a name="discussion"></a>Discussão  
 Este exemplo demonstra um cenário de troca confiável de mensagens bidirecional assíncrona. O serviço tem um contrato duplex e o cliente implementa o contrato de retorno de chamada duplex. O cliente inicia uma solicitação para um serviço, para o qual uma resposta é esperada em uma conexão separada. A mensagem de solicitação é enviada de forma confiável. O cliente não deseja abrir um ponto de extremidade de escutando no final. Portanto, ele sonda o serviço com solicitações de 'Fazer Conexão' para o serviço para enviar a resposta de volta no canal de retorno dessa solicitação de 'Fazer Conexão'. Este exemplo demonstra como fazer uma comunicação duplex confiável segura via HTTP sem o cliente expondo um ponto de extremidade de escutando (e a criação de uma exceção de firewall).  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Abra o **ReliableSecureProfile** solução.  
  
2.  Clique com botão direito do **Service** project no **Gerenciador de soluções**, selecione **depurar**, **iniciar nova instância** no menu de contexto. Isso inicia o host de serviço.  
  
3.  Clique com botão direito do **Client** project no **Gerenciador de soluções**, selecione **depurar**, **iniciar nova instância** no menu de contexto. Isso inicia o cliente.  
  
4.  Digite qualquer cadeia de caracteres no prompt na janela do console de cliente e clique em ENTER. Isso envia a cadeia de caracteres de entrada para o serviço, que calcula um hash da cadeia de caracteres.  
  
5.  Exiba o resultado no cliente windows quando o serviço chama de volta a operação de contrato de retorno de chamada duplex para exibir o resultado na janela do console do cliente. Há um atraso intencional no serviço para simular uma operação de longa execução do processamento de dados.  
  
6.  Monitorar o tráfego HTTP (por qualquer uma das ferramentas como o Monitor de rede, Fiddler e assim por diante de monitoramento de rede online) mostra que uma sequência para a comunicação é estabelecida entre o cliente e o serviço como colocados pelo perfil seguro confiável e como o cliente sonda o serviço com solicitações de 'Fazer Conexão'. Quando o serviço obtém pronto para enviar de volta a resposta processada, ele usa o canal de retorno da última solicitação de 'Fazer Conexão' para enviar de volta os resultados.  
  
7.  Pressione ENTER na janela do console de serviço para fechar o serviço. Pressione ENTER na janela do console de cliente para fechar o cliente.
