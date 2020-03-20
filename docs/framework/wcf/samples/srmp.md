---
title: SRMP
ms.date: 03/30/2017
ms.assetid: cf37078c-dcb4-45e0-acaf-2f196521b226
ms.openlocfilehash: b1b61c18c801059e95cd0b13a3135132a583882f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183336"
---
# <a name="srmp"></a>SRMP
Esta amostra demonstra como executar a comunicação transacionada enfileirada usando a Fila de Mensagens (MSMQ) em HTTP.  
  
 Na comunicação enfileirada, o cliente se comunica com o serviço usando uma fila. Mais precisamente, o cliente envia mensagens para uma fila. O serviço recebe mensagens da fila. O serviço e o cliente, portanto, não precisa estar funcionando ao mesmo tempo para se comunicar usando uma fila.  
  
 O MSMQ permite o uso de HTTP (incluindo o uso de HTTPS) para enviar mensagens para uma fila. Neste exemplo, demonstramos usando a comunicação enfileirada da Windows Communication Foundation (WCF) e como enviar mensagens através de HTTP. O MSMQ usa um protocolo chamado SRMP, que é um protocolo baseado em SOAP para comunicação via HTTP.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
4. Antes de executar a amostra em **Adicionar/Remover Componentes do Windows,** certifique-se de que o MSMQ esteja instalado com suporte http. A instalação do suporte HTTP instala automaticamente o IIS (Internet Information Services, serviços de informação da Internet) e adiciona o suporte ao protocolo no IIS para MSMQ.  
  
5. Se você quiser ter certeza de que http é usado para comunicação, você pode habilitar o MSMQ para executar no modo endurecido. Isso garante que nenhuma mensagem para qualquer fila hospedada na máquina possa chegar usando qualquer transporte não-HTTP.  
  
6. Depois de ter selecionado o MSMQ para ser executado no modo endurecido, a máquina requer uma reinicialização no Windows Server 2003.  
  
7. Executar o serviço.  
  
8. Corra com o cliente. Certifique-se de alterar o endereço do ponto final para apontar para o nome da máquina ou endereço IP em vez de localhost. O cliente envia uma mensagem e sai.  
  
## <a name="requirements"></a>Requisitos  
 Para executar esta amostra, o IIS deve ser instalado tanto no serviço quanto nas máquinas clientes, além do MSMQ.  
  
## <a name="demonstrates"></a>Demonstra  
 A amostra demonstra o envio de mensagens enfileiradas wcf usando MSMQ em HTTP. Isso também é chamado de mensagens SRMP. Quando uma mensagem enfileirada é enviada, o MSMQ na máquina de envio transfere as mensagens para o gerenciador de fila saudosista sobre transporte TCP ou HTTP. Ao escolher o SRMP, o usuário indica a escolha do HTTP como um transporte para transferência de fila. O SRMP Secure permite o uso de HTTPS.  
  
## <a name="example"></a>Exemplo  
 O código amostral é baseado na amostra transacionada. Como você envia uma mensagem para a fila e recebe uma mensagem da fila usando srmp é o mesmo que enviar e receber mensagens usando um protocolo Nativo.  
  
 A configuração para o cliente é alterada para indicar a escolha do protocolo de transferência de fila. O protocolo de transferência de fila saem de nativo, SRMP ou SrmpSecure. Por padrão, o protocolo de transferência é nativo. O cliente e o serviço especificam na configuração para usar o SRMP neste exemplo.  
  
 Existem limitações ao SRMP em relação à segurança do transporte. O segurança de transporte MSMQ padrão requer o Active Directory que requer que o gerenciador de fila de envio e o gerenciador de fila socérea residam no mesmo domínio do Windows. Isso não é possível ao enviar mensagens através do limite HTTP. Como tal, a segurança padrão do transporte não funciona. A segurança do transporte deve ser definida como Certificado se a segurança do transporte for desejada. A segurança das mensagens também pode ser usada para proteger a mensagem. Nesta amostra, tanto o transporte quanto a segurança de mensagens são desligados para ilustrar as mensagens SRMP.  
  
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
  
 A execução da amostra produz a seguinte saída.  
  
```console  
Processing Purchase Order: 556b70be-31ee-4a3b-8df4-ed5e538015a4
Customer: somecustomer.com
OrderDetails
    Order LineItem: 54 of Blue Widget @unit price: $29.99
    Order LineItem: 890 of Red Widget @unit price: $45.89
    Total cost of this order: $42461.56
    Order status: Pending  
```  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\SRMP`  
