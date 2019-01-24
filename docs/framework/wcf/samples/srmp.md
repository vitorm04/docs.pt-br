---
title: SRMP
ms.date: 03/30/2017
ms.assetid: cf37078c-dcb4-45e0-acaf-2f196521b226
ms.openlocfilehash: 2f42db91db4983c80ebb42168cf7bf1ddb3e5023
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54649655"
---
# <a name="srmp"></a>SRMP
Este exemplo demonstra como executar transacionada comunicação em fila usando o serviço de enfileiramento de mensagens (MSMQ) em HTTP.  
  
 Comunicação em fila, o cliente se comunica com o serviço usando uma fila. Mais precisamente, o cliente envia mensagens a uma fila. O serviço recebe mensagens da fila. O serviço e o cliente, portanto, não precisa estar em execução ao mesmo tempo para se comunicar usando uma fila.  
  
 MSMQ permite o uso de HTTP (incluindo o uso de HTTPS) para enviar mensagens para uma fila. Neste exemplo, vamos demonstrar o usar o Windows Communication Foundation (WCF) na fila para a comunicação e como enviar mensagens via HTTP. MSMQ usa um protocolo chamado SRMP, que é um protocolo baseado em SOAP para a comunicação por HTTP.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
4.  Antes de executar a amostra **Adicionar/remover componentes do Windows**, certifique-se de que o MSMQ está instalado com o suporte a HTTP. Instalando o suporte a HTTP automaticamente instala os serviços de informações da Internet (IIS) e adiciona o suporte de protocolo no IIS para o MSMQ.  
  
5.  Se você quiser ter certeza de que o HTTP é usado para comunicação, você pode habilitar o MSMQ seja executado no modo protegido. Isso garante que nenhuma mensagem para qualquer fila hospedada na máquina pode chegar usando qualquer transporte não HTTP.  
  
6.  Depois que você tiver selecionado o MSMQ seja executado no modo protegido, o computador requer a reinicialização do computador em [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].  
  
7.  Execute o serviço.  
  
8.  Execute o cliente. Certifique-se de que você altere o endereço do ponto de extremidade para apontar para o nome do computador ou endereço IP em vez do localhost. O cliente envia uma mensagem e sai.  
  
## <a name="requirements"></a>Requisitos  
 Para executar este exemplo, o IIS deve ser instalado sobre o serviço e os computadores cliente, além de MSMQ.  
  
## <a name="demonstrates"></a>Demonstra  
 O exemplo demonstra como enviar WCF usando o MSMQ em HTTP de mensagens na fila. Isso também é chamado de mensagens SRMP. Quando uma mensagem na fila foi enviada, MSMQ em transferências de máquina as mensagens de envio para o Gerenciador de fila de recebimento pelo transporte TCP ou HTTP. Escolhendo SRMP, o usuário indica a escolha de HTTP como um transporte para a transferência da fila. Proteger SRMP permite o uso de HTTPS.  
  
## <a name="example"></a>Exemplo  
 O código de exemplo se baseia na amostra transacionada. Como você pode envia uma mensagem à fila e recebe uma mensagem da fila usando SRMP equivale a enviar e receber mensagens usando um protocolo nativo.  
  
 A configuração para o cliente é alterada para indicar que a opção de protocolo de transferência de fila. O protocolo de transferência de fila pode ser um dos nativo, SRMP ou SrmpSecure. Por padrão, o protocolo de transferência é nativo. O cliente e o serviço especificam na configuração para usar SRMP neste exemplo.  
  
 Há limitações para SRMP em relação à segurança de transporte. A segurança do transporte MSMQ padrão requer o Active Directory que exige que o Gerenciador de fila de envio e o Gerenciador de fila de recebimento residam no mesmo domínio do Windows. Isso não é possível quando o envio de mensagens por limites HTTP. Como tal, a segurança de transporte padrão não funciona. A segurança de transporte deve ser definida para o certificado se segurança de transporte é desejada. Segurança de mensagem também pode ser usada para proteger a mensagem. Neste exemplo, segurança de transporte e de mensagem é desativada para ilustrar SRMP de mensagens.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  
  <system.serviceModel>  
  
    <client>  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint name="OrderProcessorEndpoint"  
           address=  
          "net.msmq://localhost/private/ServiceModelSamplesSrmp"   
           bindingConfiguration="srmpBinding"   
           binding="netMsmqBinding"   
           contract="IOrderProcessor" />  
    </client>  
    <bindings>  
      <netMsmqBinding>  
        <binding name="srmpBinding"  
                 queueTransferProtocol="Srmp">  
          <security mode="None" />  
        </binding>  
      </netMsmqBinding>  
    </bindings>  
  </system.serviceModel>  
  
</configuration>  
```  
  
 Executar o exemplo produz a saída a seguir.  
  
```  
Processing Purchase Order: 556b70be-31ee-4a3b-8df4-ed5e538015a4   
Customer: somecustomer.com   
OrderDetails   
    Order LineItem: 54 of Blue Widget @unit price: $29.99   
    Order LineItem: 890 of Red Widget @unit price: $45.89   
    Total cost of this order: $42461.56   
    Order status: Pending  
```  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\SRMP`  
  
## <a name="see-also"></a>Consulte também
