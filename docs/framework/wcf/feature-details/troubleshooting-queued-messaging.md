---
title: Mensagens em fila da solução de problemas
ms.date: 03/30/2017
ms.assetid: a5f2836f-018d-42f5-a571-1e97e64ea5b0
ms.openlocfilehash: 45a3bf82662fcc01b732428d1ca351e4ae8ddca0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="troubleshooting-queued-messaging"></a>Mensagens em fila da solução de problemas
Esta seção contém perguntas comuns e resolução de problemas para usar filas no Windows Communication Foundation (WCF).  
  
## <a name="common-questions"></a>Perguntas comuns  
 **P:** usei WCF Beta 1 e instalei o hotfix do MSMQ. É necessário remover o hotfix?  
  
 **R:** Sim. Esse hotfix não é mais suportado. WCF agora funciona em MSMQ sem um requisito de hotfix.  
  
 **P:** há duas associações para o MSMQ: <xref:System.ServiceModel.NetMsmqBinding> e <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>. O que devo usar e quando?  
  
 **R:** usar o <xref:System.ServiceModel.NetMsmqBinding> quando você quiser usar o MSMQ como um transporte para comunicação em fila entre dois aplicativos WCF. Use o <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> quando quiser usar os aplicativos existentes do MSMQ para se comunicar com os novos aplicativos do WCF.  
  
 **P:** é necessário atualizar o MSMQ para usar o <xref:System.ServiceModel.NetMsmqBinding> e `MsmqIntegration` associações?  
  
 **R:** não. Ambas as associações de trabalhar com MSMQ 3.0 em [!INCLUDE[wxp](../../../../includes/wxp-md.md)] e [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]. Determinados recursos de associação ficam disponíveis quando você atualizar para o MSMQ 4.0 em [!INCLUDE[wv](../../../../includes/wv-md.md)].  
  
 **P:** quais recursos do <xref:System.ServiceModel.NetMsmqBinding> e <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> associações estão disponíveis no MSMQ 4.0, mas não no MSMQ 3.0?  
  
 **R:** os recursos a seguir estão disponíveis no MSMQ 4.0, mas não no MSMQ 3.0:  
  
-   Fila de mensagens mortas personalizada é suportada somente no MSMQ 4.0.  
  
-   MSMQ 3.0 e 4.0 tratar mensagens suspeitas de maneira diferente.  
  
-   Somente o MSMQ 4.0 oferece suporte à leitura transacionada remota.  
  
 Para obter mais informações, consulte [diferenças nos recursos de enfileiramento de mensagens no Windows Vista, Windows Server 2003 e Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md).  
  
 **P:** possível usar o MSMQ 3.0 em um lado de uma comunicação em fila e MSMQ 4.0 no outro lado?  
  
 **R:** Sim.  
  
 **P:** deseja integrar os aplicativos existentes do MSMQ com servidores de novos clientes do WCF. É necessário atualizar os dois lados da minha infra-estrutura MSMQ?  
  
 **R:** não. Você não precisa atualizar para o MSMQ 4.0 em ambos os lados.  
  
## <a name="troubleshooting"></a>Solução de problemas  
 Esta seção contém as respostas para os problemas mais comuns. Alguns problemas conhecidos limitações também estão descritos nas notas de versão.  
  
 **P:** estou tentando usar uma fila particular e recebo a seguinte exceção: `System.InvalidOperationException`: A URL é inválida. A URL para a fila não pode conter o caractere '$'. Use a sintaxe no MSMQ: //machine/private/queueName para endereçar uma fila particular.  
  
 **R:** Verifique se a fila de identificador de recurso uniforme (URI) em sua configuração e seu código. Não use o caractere "$" no URI. Por exemplo, para atender a uma fila particular chamada OrdersQueue, especifique o URI como net.msmq://localhost/private/ordersQueue.  
  
 **P:** chamando `ServiceHost.Open()` em meu aplicativo enfileirado gera a seguinte exceção: `System.ArgumentException`: um endereço base não pode conter uma cadeia de caracteres de consulta URI. Por quê?  
  
 **R:** Verifique a fila de URI em seu arquivo de configuração em seu código. Enquanto as filas do MSMQ suportam o uso do '?' caractere, URIs interpretar esse caractere como o início de uma consulta de cadeia de caracteres. Para evitar esse problema, use nomes de filas que não contêm '?' caracteres.  
  
 **P:** meu envio foi bem-sucedida, mas nenhuma operação de serviço é invocada no receptor. Por quê?  
  
 **R:** para determinar a resposta, examine a lista de verificação a seguir:  
  
-   Verifique se os requisitos de fila transacional são compatíveis com as garantias especificadas. Observe os seguintes princípios:  
  
    -   Você pode enviar mensagens duráveis (datagramas e sessões) com "exatamente uma vez" garantias (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `true`) apenas para uma fila transacional.  
  
    -   Você pode enviar sessões somente com garantia "exatamente uma vez".  
  
    -   Uma transação é necessária para receber mensagens em uma sessão de uma fila transacional.  
  
    -   Você pode enviar ou receber duráveis ou voláteis mensagens (datagramas) com nenhuma garantia (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `false`) somente a uma fila não transacional.  
  
-   Verificar a fila de mensagens mortas. Se você encontrar mensagens lá, determine por que eles não foram entregues.  
  
-   Verifique se as filas de saída para tratar de problemas ou de conectividade.  
  
 **P:** especificou uma fila de mensagens mortas personalizada, mas ao iniciar o aplicativo de remetente, obtenho uma exceção de que a fila de mensagens mortas não foi encontrada ou o aplicativo de envio não tem permissão para a fila de mensagens mortas. Por que é isso estiver acontecendo?  
  
 **R:** a fila de mensagens mortas personalizada URI deve incluir "localhost" ou o nome do computador no primeiro segmento, por exemplo, net.msmq://localhost/private/myAppdead-letter fila.  
  
 **P:** é sempre necessário definir uma fila de mensagens mortas personalizada, ou há uma fila de mensagens mortas padrão?  
  
 **R:** se garantias são "exatamente uma vez" (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `true`), e se você não especificar uma fila de mensagens mortas personalizada, o padrão é uma fila de mensagens mortas transacional de todo o sistema.  
  
 Se garantias são none (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `false`), em seguida, o padrão não é nenhuma funcionalidade de fila de mensagens mortas.  
  
 **P:** meu lança serviço em SvcHost.Open com uma mensagem "EndpointListener requisitos não podem ser atendidos pelo ListenerFactory". Por quê?  
  
 R. Verifique seu contrato de serviço. Você pode ter esquecido de colocar "IsOneWay =`true`" em todas as operações de serviço. As filas oferecem suporte somente a operações de serviço unidirecional.  
  
 **P:** há mensagens na fila, mas nenhuma operação de serviço é invocada. Qual é o problema?  
  
 **R:** determinar se o host de serviço está com defeito. Você pode verificar, olhando para o rastreamento de ou implementar `IErrorHandler`. Falhas de host de serviço, por padrão, se uma mensagem suspeita é detectada.  
  
 **P:** há mensagens na fila, mas não está obtendo habilitado meu serviço na fila hospedado na Web. Por quê?  
  
 **R:** o motivo mais comum é permissões.  
  
1.  Certifique-se de que o `NetMsmqActivator` processo está sendo executado e a identidade do `NetMsmqActivator` processo recebe leitura e busca de permissão na fila.  
  
2.  Se o `NetMsmqActivator` está monitorando filas em um computador remoto, certifique-se de que `NetMsmqActivator` não é executado em um token restrito. Para executar o `NetMsmqActivator` com um token irrestrito:  
  
    ```  
    sc sidtype NetMsmqActivator unrestricted  
    ```  
  
 Para problemas de host da Web relacionados não são de segurança, consulte: [Web hospeda um aplicativo em fila](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md).  
  
 **P:** qual é a maneira mais fácil para sessões de acesso?  
  
 **R:** definir AutoCompletar =`true` a operação que corresponde à última mensagem na sessão e defina o preenchimento automático =`false` em todas as operações de serviço restantes.  
  
 **P:** onde posso encontrar respostas para perguntas comuns sobre o MSMQ?  
  
 **R:** para obter mais informações sobre o MSMQ, consulte [Microsoft Message Queuing](http://go.microsoft.com/fwlink/?LinkId=87810).  
  
 **P:** por que meu serviço lançar um `ProtocolException` quando ao ler de uma fila que contém mensagens de sessão em fila e datagrama mensagens em fila?  
  
 **R:** há uma diferença fundamental nas mensagens de sessão em forma de fila e mensagens na fila de datagrama são compostas. Por isso, um serviço que está esperando para ler uma mensagem na fila de sessão não pode receber uma mensagem de datagrama em fila e um serviço que espera ler uma mensagem de datagrama na fila não pode receber uma mensagem de sessão. Ao tentar ler os dois tipos de mensagens da mesma fila gera a seguinte exceção:  
  
```  
System.ServiceModel.MsmqPoisonMessageException: The transport channel detected a poison message. This occurred because the message exceeded the maximum number of delivery attempts or because the channel detected a fundamental problem with the message. The inner exception may contain additional information.   
---> System.ServiceModel.ProtocolException: An incoming MSMQ message contained invalid or unexpected .NET Message Framing information in its body. The message cannot be received. Ensure that the sender is using a compatible service contract with a matching SessionMode.  
```  
  
 A fila de mensagens mortas de sistema, bem como qualquer fila de mensagens mortas personalizada, é particularmente suscetível a esse problema se um aplicativo envia mensagens de sessão em fila tanto na fila de mensagens de datagrama do mesmo computador. Se uma mensagem não pode ser enviada com êxito, ele é movido para a fila de mensagens mortas. Sob essas circunstâncias, é possível ter sessão e datagrama mensagens na fila de mensagens mortas. Não é possível separar os dois tipos de mensagens em tempo de execução durante a leitura de uma fila, portanto, aplicativos não devem enviar mensagens de sessão em fila tanto na fila de mensagens de datagrama do mesmo computador.  
  
### <a name="msmq-integration-specific-troubleshooting"></a>Integração de MSMQ: Solução de problemas específicos  
 **P:** quando enviar uma mensagem, ou ao abrir o host de serviço, recebo um erro que indica o esquema está errado. Por quê?  
  
 **R:** quando você usa a associação de integração do MSMQ, você deve usar o esquema FormatName. Por exemplo, msmq.formatname:DIRECT=OS:.\private$\OrdersQueue. Mas quando você especifica a fila de mensagens mortas personalizada, você deve usar o esquema NET. MSMQ.  
  
 **P:** ao uso de um nome de formato público ou privado e abrir o host de serviço no [!INCLUDE[wv](../../../../includes/wv-md.md)], recebo um erro. Por quê?  
  
 **R:** canal de integração do WCF em [!INCLUDE[wv](../../../../includes/wv-md.md)] verifica se uma fila sub pode ser aberta para a fila principal do aplicativo para tratar mensagens suspeitas. O nome de subfila é derivado de um FormatName que URI passado para o ouvinte. O nome de subfila no MSMQ só pode ser um nome de formato direto. Portanto, você verá o erro. Altere o URI da fila para um nome de formato direto.  
  
 **P:** quando receber uma mensagem de um aplicativo do MSMQ, a mensagem se encontra na fila e não é lido pelo aplicativo de recebimento de WCF. Por quê?  
  
 **R:** Verifique se a mensagem tem um corpo. Se a mensagem não tem nenhum corpo, o canal de integração do MSMQ ignora a mensagem. Implementar `IErrorHandler` para ser notificado de exceções e verificar os rastreamentos.  
  
### <a name="security-related-troubleshooting"></a>Solução de problemas relacionados à segurança  
 **P:** ao executar o exemplo que usa uma associação padrão no modo de grupo de trabalho, mensagens parecerão sejam enviados, mas nunca são recebidas pelo destinatário.  
  
 **R:** por padrão, as mensagens são assinadas usando um certificado interno do MSMQ que requer que o serviço de diretório do Active Directory. No modo de grupo de trabalho, como o Active Directory não estiver disponível, a mensagem de assinatura falha. Portanto, a mensagem chega na fila de mensagens mortas e causa da falha, como "Assinatura incorreta", é indicada.  
  
 A solução é desativar a segurança. Isso é feito definindo <xref:System.ServiceModel.NetMsmqSecurity.Mode%2A>  =  <xref:System.ServiceModel.NetMsmqSecurityMode.None> para funcionar no modo de grupo de trabalho.  
  
 Outra solução alternativa é obter o <xref:System.ServiceModel.MsmqTransportSecurity> do <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A> propriedade e defina-a como <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate>e defina o certificado de cliente.  
  
 Outra solução alternativa é instalar o MSMQ com a integração do Active Directory.  
  
 **P:** quando enviar uma mensagem com associação padrão (ativada de segurança de transporte) no Active Directory para uma fila, recebo uma mensagem de "certificado interno não encontrado". Como corrigir isso?  
  
 **R:** isso significa que o certificado no Active Directory para o remetente deve ser renovado. Para fazer isso, abra **painel de controle**, **ferramentas administrativas**, **gerenciamento do computador**, clique com botão direito **MSMQ**e selecione **Propriedades**. Selecione o **certificado de usuário** guia e clique no **renovar** botão.  
  
 **P:** quando posso enviar uma mensagem usando <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> e especificar o certificado a ser usado, recebo uma mensagem de "Certificado inválido". Como corrigir isso?  
  
 **R:** não é possível usar um repositório de certificados do computador local com o modo de certificado. Você precisa copiar o certificado do repositório de certificados de máquina para o repositório do usuário atual usando o snap-in de certificado. Para obter o certificado de snap-in:  
  
1.  Clique em **iniciar**, selecione **executar**, tipo `mmc`e clique em **Okey**.  
  
2.  No **Console de gerenciamento Microsoft**, abra o **arquivo** menu e selecione **Adicionar/Remover Snap-in**.  
  
3.  No **Adicionar/Remover Snap-in** caixa de diálogo, clique o **adicionar** botão.  
  
4.  No **Adicionar Snap-in Standalone** caixa de diálogo, selecione certificados e clique em **adicionar**.  
  
5.  No **certificados** caixa de diálogo snap-in, selecione **minha conta de usuário,** e clique em **concluir**.  
  
6.  Em seguida, adicione um segundo certificados snap-in usando as etapas anteriores, mas desta vez selecione **conta de computador** e clique em **próximo**.  
  
7.  Selecione **computador Local** e clique em **concluir**. Agora você pode arrastar e soltar certificados do repositório de certificados de máquina para o armazenamento do usuário atual.  
  
 **P:** ao meu serviço lê uma fila em outro computador no modo de grupo de trabalho, obtenho uma exceção "acesso negado".  
  
 **R:** no modo de grupo de trabalho, para um aplicativo remoto acessar a fila, o aplicativo deve ter permissão para acessar a fila. Adicionar "Logon anônimo" à lista de controle de acesso (ACL) da fila e dê a ele a permissão de leitura.  
  
 **P:** quando um cliente de serviço de rede (ou qualquer cliente que não tem uma conta de domínio) envia uma mensagem na fila, o envio falhará com um certificado inválido. Como corrigir isso?  
  
 **R:** Verifique a configuração de associação. A associação padrão foi ativada para a segurança de transporte MSMQ assinou a mensagem. Desativá-lo.  
  
### <a name="remote-transacted-receives"></a>Recebe remoto transacionado  
 **P:** quando tenho uma fila em um computador e um serviço WCF que lê mensagens de uma fila no computador B (cenário de recebimento remoto transacionado), as mensagens não são lidas da fila. As informações de rastreamento indica o recebimento falhou com a mensagem "transação não pode ser importado." O que fazer para corrigir isso?  
  
 **R:** existem três possíveis razões para isso:  
  
-   Se você estiver no modo de domínio, receber remoto transacionado requer acesso de rede do coordenador de transações distribuídas da Microsoft (MSDTC). Você pode habilitar essa usando **Adicionar/remover componentes**.  
  
     ![Habilitar acesso DTC de rede](../../../../docs/framework/wcf/feature-details/media/applicationserveraddcomps.jpg "ApplicationServerAddComps")  
  
-   Verifique o modo de autenticação para se comunicar com o Gerenciador de transações. Se você estiver no modo de grupo de trabalho, "Nenhuma autenticação necessária" deve ser selecionada. Se você estiver no modo de domínio, "Autenticação mútua necessária" deve ser selecionada.  
  
     ![Habilitar transações XA](../../../../docs/framework/wcf/feature-details/media/4f3695e0-fb0b-4c5b-afac-75f8860d2bb0.jpg "4f3695e0-fb0b-4c5b-afac-75f8860d2bb0")  
  
-   Certifique-se de que o MSDTC está na lista de exceções de **Firewall de Conexão de Internet** configurações.  
  
-   Certifique-se de que você está usando [!INCLUDE[wv](../../../../includes/wv-md.md)]. MSMQ em [!INCLUDE[wv](../../../../includes/wv-md.md)] dá suporte à leitura transacionada remota. O MSMQ em versões anteriores do Windows não oferece suporte a leitura transacionada remota.  
  
 **P:** quando a leitura da fila do serviço é um serviço de rede, por exemplo, em uma Web host, por que recebo uma exceção de acesso negado é gerado durante a leitura da fila?  
  
 **R:** acesso de leitura do serviço de rede deve ser adicionado à fila de ACL para garantir que um serviço de rede pode ler da fila.  
  
 **P:** posso usar o serviço de ativação MSMQ para ativar aplicativos com base em mensagens em uma fila em um computador remoto?  
  
 **R:** Sim. Para fazer isso, você deve configurar o serviço de ativação MSMQ para ser executado como um serviço de rede e adicionar o acesso ao serviço de rede para a fila no computador remoto.  
  
## <a name="using-custom-msmq-bindings-with-receivecontext-enabled"></a>Usando associações de MSMQ personalizado com ReceiveContext habilitado  
 Ao usar uma associação personalizada do MSMQ com <xref:System.ServiceModel.Channels.ReceiveContext> habilitado para processamento de uma mensagem de entrada usará um pool de threads porque MSMQ nativo não oferece suporte a conclusão de e/s para assíncrona <xref:System.ServiceModel.Channels.ReceiveContext> recebe. Isso ocorre porque o processamento dessa mensagem usa transações internas para <xref:System.ServiceModel.Channels.ReceiveContext> e MSMQ não dá suporte ao processamento assíncrono. Para contornar esse problema, você pode adicionar uma <xref:System.ServiceModel.Description.SynchronousReceiveBehavior> para o ponto de extremidade para forçar síncrona de processamento ou defina <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.MaxPendingReceives%2A> como 1.
