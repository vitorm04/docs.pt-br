---
title: Perfil seguro confiável
ms.date: 03/30/2017
ms.assetid: 921edc41-e91b-40f9-bde9-b6148b633e61
ms.openlocfilehash: 9ddd0d78396bba6712650620e6b46c62f13337e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144208"
---
# <a name="reliable-secure-profile"></a>Perfil seguro confiável

Esta amostra demonstra como compor O WCF e [o Perfil Seguro Confiável (RSP).](http://www.ws-i.org/Profiles/ReliableSecureProfile-1.0.html) Esta amostra demonstra a implementação de um canal [Make Connection,](http://docs.oasis-open.org/ws-rx/wsmc/200702/wsmc-1.0-spec-cs-01.pdf) que pode ser composto em conjunto com mensagens confiáveis e, opcionalmente, um canal seguro para criar uma vinculação segura confiável com base na especificação RSP.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ReliableSecureProfile`  
  
## <a name="discussion"></a>Discussão  
 Esta amostra demonstra um cenário de troca de mensagens assíncrona confiável. O serviço tem um contrato duplex e o cliente implementa o contrato de retorno de chamada duplex. O cliente inicia uma solicitação a um serviço, para a qual uma resposta é esperada em uma conexão separada. A mensagem de solicitação é enviada de forma confiável. O cliente não quer abrir um ponto final de escuta no final. Assim, ele pesquisa o serviço com pedidos de 'Fazer conexão' para que o serviço envie de volta a resposta no canal de trás desta solicitação 'Fazer conexão'. Esta amostra demonstra como ter uma comunicação duplex confiável e segura sobre HTTP sem que o cliente exponha um ponto final de escuta (e crie uma exceção de firewall).  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Abra a solução **ReliableSecureProfile.**  
  
2. Clique com o botão direito do mouse no projeto **Serviço** no **Solution Explorer**, selecione **Depuração,** **Inicie nova instância** no menu de contexto. Isso inicia o host de serviço.  
  
3. Clique com o botão direito do mouse no projeto **Cliente** no **Solution Explorer**, selecione **Depuração**, Inicie nova **instância** no menu de contexto. Isso começa o cliente.  
  
4. Digite qualquer seqüência de string no prompt na janela do console do cliente e clique em ENTER. Isso envia a seqüência de entrada para o serviço, que calcula um hash desta string.  
  
5. Exibir o resultado nas janelas do cliente quando o serviço chamar de volta a operação do contrato de retorno de chamada duplex para exibir o resultado na janela do console do cliente. Há um atraso intencional no serviço para simular uma longa operação de processamento dos dados.  
  
6. O monitoramento do tráfego HTTP (por qualquer uma das ferramentas de monitoramento de rede on-line como Monitor de Rede, Fiddler e assim por diante) mostra que uma seqüência de comunicação é estabelecida entre o cliente e o serviço conforme estabelecido pelo Perfil Seguro Confiável e como o cliente pesquisa o serviço com pedidos 'Fazer conexão'. Quando o serviço se prepara para enviar de volta a resposta processada, ele usa o canal de trás da última solicitação 'Fazer conexão' para enviar de volta os resultados.  
  
7. Pressione ENTER na janela do console de serviço para fechar o serviço. Pressione ENTER na janela do console do cliente para fechar o cliente.
