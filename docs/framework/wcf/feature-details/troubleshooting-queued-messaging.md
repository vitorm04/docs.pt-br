---
title: Mensagens em fila da solução de problemas
ms.date: 03/30/2017
ms.assetid: a5f2836f-018d-42f5-a571-1e97e64ea5b0
ms.openlocfilehash: c85b0701c870fe2b4a3c11dc384e890e1ed001dd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59977282"
---
# <a name="troubleshooting-queued-messaging"></a>Mensagens em fila da solução de problemas
Esta seção contém perguntas comuns e solução de problemas de ajuda para usar as filas no Windows Communication Foundation (WCF).  
  
## <a name="common-questions"></a>Perguntas comuns  
 **P:** Eu usei a versão Beta 1 do WCF e instalei o hotfix do MSMQ. É necessário remover o hotfix?  
  
 **R:** Sim. Esse hotfix não é mais suportado. O WCF agora funciona em MSMQ sem um requisito de hotfix.  
  
 **P:** Há duas associações para o MSMQ: <xref:System.ServiceModel.NetMsmqBinding> e <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>. O que devo usar e quando?  
  
 **R:** Use o <xref:System.ServiceModel.NetMsmqBinding> quando você quiser usar o MSMQ como um transporte para comunicação em fila entre dois aplicativos do WCF. Use o <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> quando você quiser usar aplicativos existentes do MSMQ para se comunicar com os novos aplicativos do WCF.  
  
 **P:** É necessário atualizar o MSMQ para usar o <xref:System.ServiceModel.NetMsmqBinding> e `MsmqIntegration` associações?  
  
 **R:** Nº Ambas as associações de trabalhar com o MSMQ 3.0 em [!INCLUDE[wxp](../../../../includes/wxp-md.md)] e [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]. Determinados recursos das associações são disponibilizados quando você atualiza para o MSMQ 4.0 em [!INCLUDE[wv](../../../../includes/wv-md.md)].  
  
 **P:** Quais recursos do <xref:System.ServiceModel.NetMsmqBinding> e <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> associações estão disponíveis no MSMQ 4.0, mas não no MSMQ 3.0?  
  
 **R:** Os seguintes recursos estão disponíveis no MSMQ 4.0, mas não no MSMQ 3.0:  
  
-   Fila de mensagens mortas personalizada tem suporte apenas no MSMQ 4.0.  
  
-   O MSMQ 3.0 e 4.0 tratar mensagens suspeitas de maneira diferente.  
  
-   Somente o MSMQ 4.0 oferece suporte à leitura transacionada remota.  
  
 Para obter mais informações, consulte [diferenças nos recursos de enfileiramento de mensagens no Windows Vista, Windows Server 2003 e Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md).  
  
 **P:** Pode usar o MSMQ 3.0 em um lado de uma comunicação em fila e MSMQ 4.0 no outro lado?  
  
 **R:** Sim.  
  
 **P:** Eu quero integrar aplicativos existentes do MSMQ com novos clientes do WCF ou servidores. É necessário atualizar os dois lados da minha infraestrutura MSMQ?  
  
 **R:** Nº Não é necessário atualizar para o MSMQ 4.0 em ambos os lados.  
  
## <a name="troubleshooting"></a>Solução de problemas  
 Esta seção contém as respostas para problemas mais comuns de solução de problemas. Alguns problemas que são limitações conhecidos também são descritos nas notas de versão.  
  
 **P:** Estou tentando usar uma fila particular e recebo a seguinte exceção: `System.InvalidOperationException`: A URL é inválida. A URL para a fila não pode conter o caractere '$'. Use a sintaxe MSMQ://machine/private/queueName para identificar uma fila particular.  
  
 **R:** Verifique se a fila de identificador de recurso uniforme (URI) em sua configuração e código. Não use o caractere "$" no URI. Por exemplo, para lidar com uma fila particular chamada OrdersQueue, especifique o URI como net.msmq://localhost/private/ordersQueue.  
  
 **P:** Chamando `ServiceHost.Open()` em meu aplicativo enfileirado gera a seguinte exceção: `System.ArgumentException`: Um endereço base não pode conter uma cadeia de caracteres de consulta do URI. Por quê?  
  
 **R:** Verifique a fila de URI em seu arquivo de configuração em seu código. Embora o uso de suportam a filas MSMQ o '?' caractere, URIs interpretar esse caractere como o início de uma consulta de cadeia de caracteres. Para evitar esse problema, use nomes de fila que não contêm '?' caracteres.  
  
 **P:** Meu envio foi bem-sucedida, mas nenhuma operação de serviço é invocada no receptor. Por quê?  
  
 **R:** Para determinar a resposta, trabalhe com a lista de verificação a seguir:  
  
-   Verifique se os requisitos de fila transacional são compatíveis com as garantias especificadas. Observe os seguintes princípios:  
  
    -   Você pode enviar mensagens duráveis (datagramas e sessões) com "exatamente uma vez" garantias (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `true`) apenas para uma fila transacional.  
  
    -   Você pode enviar sessões somente com garantias de "exatamente uma vez".  
  
    -   Uma transação é necessária para receber mensagens em uma sessão de uma fila transacional.  
  
    -   Você pode enviar ou receber duráveis ou voláteis mensagens (datagramas) com nenhuma garantia (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `false`) somente a uma fila não transacional.  
  
-   Verificar a fila de inatividade. Se você achar que as mensagens de lá, determine por que eles não foram entregues.  
  
-   Verifique se as filas de saída para resolver problemas ou de conectividade.  
  
 **P:** Eu especifiquei uma fila de inatividade personalizada, mas quando eu iniciar o aplicativo de remetente, obtenho uma exceção que a fila de inatividade não for encontrada ou o aplicativo de envio não tem permissão para a fila de inatividade. Por que isso está acontecendo?  
  
 **R:** O URI da fila mortas personalizada deve incluir "localhost" ou o nome do computador no primeiro segmento, por exemplo, net.msmq://localhost/private/myAppdead-letter fila.  
  
 **P:** Ele sempre é necessário definir uma fila de inatividade personalizada ou há uma fila de inatividade padrão?  
  
 **R:** Se as garantias são "exatamente uma vez" (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `true`), e se você não especificar uma fila de inatividade personalizada, o padrão é uma fila de inatividade em todo o sistema transacional.  
  
 Se as garantias são none (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `false`), em seguida, o padrão não é nenhuma funcionalidade de fila de inatividade.  
  
 **P:** Meu serviço lança em SvcHost.Open com uma mensagem "EndpointListener requisitos não podem ser atendidos, o ListenerFactory". Por quê?  
  
 R. Verifique seu contrato de serviço. Você pode ter esquecido de colocar "IsOneWay =`true`" em todas as operações de serviço. As filas oferecem suporte apenas a operações de serviço unidirecional.  
  
 **P:** Há mensagens na fila, mas nenhuma operação de serviço é invocada. O que é o problema?  
  
 **R:** Determine se o seu host de serviço está com defeito. Você pode verificar examinar o rastreamento ou implementando `IErrorHandler`. Falhas de host de serviço, por padrão, se uma mensagem suspeita é detectada.  
  
 **P:** Há mensagens na fila, mas meu na fila de serviço hospedado na Web não está obtendo ativado. Por quê?  
  
 **R:** O motivo mais comum é que as permissões.  
  
1. Certifique-se de que o `NetMsmqActivator` processo está em execução e a identidade do `NetMsmqActivator` processo é dada a leitura e busca de permissão na fila.  
  
2. Se o `NetMsmqActivator` é o monitoramento de filas em um computador remoto, certifique-se de que `NetMsmqActivator` não é executado em um token restrito. Para executar o `NetMsmqActivator` com um token sem restrições:  
  
    ```  
    sc sidtype NetMsmqActivator unrestricted  
    ```  
  
 Para problemas de host da Web relacionados não são de segurança, consulte: [Um aplicativo na fila de hospedagem na Web](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md).  
  
 **P:** O que é a maneira mais fácil para as sessões de acesso?  
  
 **R:** Definir o preenchimento automático =`true` na operação que corresponde à última mensagem na sessão e defina o preenchimento automático =`false` em todas as operações restantes do serviço.  
  
 **P:** Onde posso encontrar respostas para perguntas comuns sobre o MSMQ  
  
 **R:** Para obter mais informações sobre o MSMQ, consulte [Microsoft Message Queuing](https://go.microsoft.com/fwlink/?LinkId=87810).  
  
 **P:** Por que meu serviço lançar uma `ProtocolException` quando ler de uma fila que contém ambos na fila de mensagens da sessão e mensagens do datagrama na fila?  
  
 **R:** Há uma diferença fundamental nas mensagens de sessão na forma de fila e mensagens do datagrama na fila são compostas. Por isso, um serviço que está esperando para ler uma mensagem na fila de sessão não pode receber uma mensagem de datagrama na fila e um serviço que espera ler uma mensagem de datagrama na fila não pode receber uma mensagem da sessão. Ao tentar ler os dois tipos de mensagens da mesma fila gera a seguinte exceção:  
  
```  
System.ServiceModel.MsmqPoisonMessageException: The transport channel detected a poison message. This occurred because the message exceeded the maximum number of delivery attempts or because the channel detected a fundamental problem with the message. The inner exception may contain additional information.   
---> System.ServiceModel.ProtocolException: An incoming MSMQ message contained invalid or unexpected .NET Message Framing information in its body. The message cannot be received. Ensure that the sender is using a compatible service contract with a matching SessionMode.  
```  
  
 A fila de inatividade do sistema, bem como qualquer fila mortas personalizada, é especialmente suscetíveis a esse problema se um aplicativo envia ambos na fila de mensagens da sessão e na fila de mensagens do datagrama do mesmo computador. Se uma mensagem não pode ser enviada com êxito, ele é movido para a fila de inatividade. Sob essas circunstâncias, é possível ter mensagens de sessão e o datagrama na fila de inatividade. Não há nenhuma maneira de separar os dois tipos de mensagens em tempo de execução durante a leitura de uma fila, portanto, aplicativos não devem enviar ambos na fila de mensagens da sessão e na fila de mensagens do datagrama do mesmo computador.  
  
### <a name="msmq-integration-specific-troubleshooting"></a>Integração de MSMQ com: Solução de problemas específicos  
 **P:** Quando eu enviar uma mensagem, ou quando eu abro o host de serviço, recebo um erro que indica que o esquema está errado. Por quê?  
  
 **R:** Quando você usa a associação de integração de MSMQ, você deve usar o esquema FormatName. Por exemplo, msmq.formatname:DIRECT=OS:.\private$\OrdersQueue. Mas quando você especifica a fila de inatividade personalizada, você deve usar o esquema de NET. MSMQ.  
  
 **P:** Quando posso usar um nome de formato público ou privado e abrir o host de serviço no [!INCLUDE[wv](../../../../includes/wv-md.md)], recebo um erro. Por quê?  
  
 **R:** O canal de integração do WCF no [!INCLUDE[wv](../../../../includes/wv-md.md)] verifica se uma subfila poderá ser aberta para a fila principal do aplicativo para tratar mensagens suspeitas. O nome de subfila deriva um FormatName que URI passado para o ouvinte. O nome de subfila no MSMQ só pode ser um nome de formato direto. Portanto, você verá o erro. Altere o URI da fila para um nome de formato direto.  
  
 **P:** Ao receber uma mensagem de um aplicativo do MSMQ, a mensagem se encontra na fila e não é lido pelo aplicativo de recebimento de WCF. Por quê?  
  
 **R:** Verifique se a mensagem tem um corpo. Se a mensagem não tem nenhum corpo, o canal de integração de MSMQ ignora a mensagem. Implemente `IErrorHandler` para ser notificado sobre exceções e verificar os rastreamentos.  
  
### <a name="security-related-troubleshooting"></a>Solução de problemas relacionados à segurança  
 **P:** Quando executo a amostra que usa uma associação padrão no modo de grupo de trabalho, as mensagens parecem sejam enviados, mas nunca são recebidas pelo destinatário.  
  
 **R:** Por padrão, as mensagens são assinadas usando um certificado interno do MSMQ que exige que o serviço de diretório do Active Directory. No modo de grupo de trabalho, porque o Active Directory não estiver disponível, a mensagem de assinatura falhará. Portanto, a mensagem chega à fila de inatividade e causa da falha, como "Assinatura incorreta", é indicada.  
  
 A solução é desativar a segurança. Isso é feito definindo <xref:System.ServiceModel.NetMsmqSecurity.Mode%2A>  =  <xref:System.ServiceModel.NetMsmqSecurityMode.None> fazê-lo funcionar no modo de grupo de trabalho.  
  
 Outra solução alternativa é obter o <xref:System.ServiceModel.MsmqTransportSecurity> do <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A> propriedade e defini-lo como <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate>e defina o certificado do cliente.  
  
 Outra solução alternativa é instalar o MSMQ com integração do Active Directory.  
  
 **P:** Quando eu enviar uma mensagem com a associação padrão (ativada de segurança de transporte) no Active Directory para uma fila, receber uma mensagem de "certificado interno não encontrado". Como corrigir isso?  
  
 **R:** Isso significa que o certificado no Active Directory para o remetente deve ser renovado. Para fazer isso, abra **painel de controle**, **ferramentas administrativas**, **gerenciamento do computador**, clique com botão direito **MSMQ**e selecione **Propriedades**. Selecione o **certificado de usuário** guia e clique no **Renew** botão.  
  
 **P:** Quando eu enviar uma mensagem usando <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> e especificar o certificado a ser usado, recebo uma mensagem de "Certificado inválido". Como corrigir isso?  
  
 **R:** Você não pode usar um repositório de certificados do computador local com o modo de certificado. Você precisa copiar o certificado do repositório de certificados de computador para o armazenamento do usuário atual usando o snap-in de certificado. Para obter o certificado do snap-in:  
  
1. Clique em **inicie**, selecione **execute**, digite `mmc`e clique em **Okey**.  
  
2. No **Console de gerenciamento Microsoft**, abra o **arquivo** menu e selecione **Adicionar/Remover Snap-in**.  
  
3. No **Adicionar/Remover Snap-in** caixa de diálogo, clique o **Add** botão.  
  
4. No **Adicionar Snap-in Standalone** caixa de diálogo, selecione certificados e clique em **Add**.  
  
5. No **certificados** caixa de diálogo snap-in, selecione **minha conta de usuário** e clique em **concluir**.  
  
6. Em seguida, adicione um segundo certificados snap-in usando as etapas anteriores, mas desta vez selecione **conta de computador** e clique em **próxima**.  
  
7. Selecione **computador Local** e clique em **concluir**. Agora você pode arrastar e soltar certificados do repositório de certificados de computador para o armazenamento do usuário atual.  
  
 **P:** Quando meu serviço lê uma fila em outro computador no modo de grupo de trabalho, eu obtenho uma exceção "acesso negado".  
  
 **R:** No modo de grupo de trabalho, para um aplicativo remoto obter acesso à fila, o aplicativo deve ter permissão para acessar a fila. Adicionar "Logon anônimo" à lista de controle de acesso (ACL) da fila e dê a ele a permissão de leitura.  
  
 **P:** Quando um cliente do serviço de rede (ou qualquer cliente que não tem uma conta de domínio) envia uma mensagem na fila, o envio falha com um certificado inválido. Como corrigir isso?  
  
 **R:** Verifique a configuração de associação. A associação padrão tem a segurança do transporte MSMQ ativada para assinar a mensagem. Para desativá-lo.  
  
### <a name="remote-transacted-receives"></a>Recebe remoto transacionado  
 **P:** Quando há uma fila em um e um serviço WCF que lê mensagens de uma fila no computador B (cenário de recebimento remoto transacionado) da máquina, mensagens não lidas da fila. As informações de rastreamento indica o recebimento falhou com a mensagem "transação não pode ser importado." O que pode fazer para corrigir isso?  
  
 **R:** Há três possíveis razões para isso:  
  
-   Se você estiver no modo de domínio, remoto transacionado receber requer acesso de rede Microsoft Distributed Transaction coordenador (MSDTC). Você pode habilitá-lo usando **Adicionar/remover componentes**.  
  
     ![Captura de tela que mostra a habilitação de DTC de rede acesso.](./media/troubleshooting-queued-messaging/enable-distributed-transaction-coordinator-access.jpg)  
  
-   Verifique o modo de autenticação para se comunicar com o Gerenciador de transações. Se você estiver no modo de grupo de trabalho, "Nenhuma autenticação necessária" deve ser selecionada. Se você estiver no modo de domínio, em seguida, "Autenticação mútua necessária" deve ser selecionada.  
  
     ![Habilitando transações XA](../../../../docs/framework/wcf/feature-details/media/4f3695e0-fb0b-4c5b-afac-75f8860d2bb0.jpg "4f3695e0-fb0b-4c5b-afac-75f8860d2bb0")  
  
-   Certifique-se de que o MSDTC está na lista de exceções na **Firewall de Conexão com a Internet** configurações.  
  
-   Certifique-se de que você está usando [!INCLUDE[wv](../../../../includes/wv-md.md)]. MSMQ em [!INCLUDE[wv](../../../../includes/wv-md.md)] dá suporte à leitura transacionada remota. O MSMQ em versões anteriores do Windows não oferece suporte a leitura transacionada remota.  
  
 **P:** Quando a leitura da fila de serviço é um serviço de rede, por exemplo, em uma Web host, por que obtenho uma exceção de acesso negado é gerado durante a leitura da fila?  
  
 **R:** Acesso de leitura do serviço de rede deve ser adicionado à fila de ACL para garantir que um serviço de rede possa ler da fila.  
  
 **P:** Pode usar o serviço de ativação MSMQ para ativar aplicativos com base em mensagens em uma fila em um computador remoto?  
  
 **R:** Sim. Para fazer isso, você deve configurar o serviço de ativação MSMQ para ser executado como um serviço de rede e adicionar o acesso ao serviço de rede para a fila no computador remoto.  
  
## <a name="using-custom-msmq-bindings-with-receivecontext-enabled"></a>Usando associações personalizadas de MSMQ com ReceiveContext habilitado  
 Ao usar uma ligação personalizada de MSMQ com <xref:System.ServiceModel.Channels.ReceiveContext> habilitada para processar uma mensagem de entrada usará um pool de threads porque MSMQ nativo não oferece suporte a conclusão de e/s para assíncrona <xref:System.ServiceModel.Channels.ReceiveContext> recebe. Isso ocorre porque o processamento dessa mensagem usa transações internas para <xref:System.ServiceModel.Channels.ReceiveContext> e MSMQ não oferece suporte para processamento assíncrono. Para contornar esse problema, você pode adicionar um <xref:System.ServiceModel.Description.SynchronousReceiveBehavior> ao ponto de extremidade para forçar síncrona de processamento ou defina <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.MaxPendingReceives%2A> como 1.
