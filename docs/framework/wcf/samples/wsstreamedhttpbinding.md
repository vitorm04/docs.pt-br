---
title: WSStreamedHttpBinding
ms.date: 03/30/2017
ms.assetid: 97ce4d3d-ca6f-45fa-b33b-2429bb84e65b
ms.openlocfilehash: aad89924b371d9d5032f32f29aac83fae445f253
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959772"
---
# <a name="wsstreamedhttpbinding"></a>WSStreamedHttpBinding
O exemplo demonstra como criar uma associação que é projetada para dar suporte a cenários de streaming quando o transporte HTTP é usado.  
  
> [!NOTE]
> O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Binding\WSStreamedHttpBinding`  
  
 As etapas para criar e configurar uma nova associação padrão são as seguintes.  
  
1. Criar uma nova associação padrão  
  
     As associações padrão no Windows Communication Foundation (WCF), como basicHttpBinding, e netTcpbinding, configuram os transportes subjacentes e a pilha de canal para requisitos específicos. Neste exemplo, `WSStreamedHttpBinding` configura a pilha de canais para dar suporte ao streaming. Por padrão, o WS-Security e o sistema de mensagens confiável não são adicionados à pilha de canais porque não há suporte para os dois recursos pelo streaming. A nova associação é implementada na classe `WSStreamedHttpBinding` derivada de. <xref:System.ServiceModel.Channels.Binding> O `WSStreamedHttpBinding` contém os seguintes elementos de associação <xref:System.ServiceModel.Channels.HttpTransportBindingElement>: <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, e <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>. A classe fornece um `CreateBindingElements()` método para configurar a pilha de associação resultante, conforme mostrado no código de exemplo a seguir.  
  
    ```  
    public override BindingElementCollection CreateBindingElements()  
    {  
         // return collection of BindingElements  
         BindingElementCollection bindingElements = new BindingElementCollection();  
  
        // the order of binding elements within the collection is important: layered channels are applied in the order included, followed by  
        // the message encoder, and finally the transport at the end  
        if (flowTransactions)  
        {  
            bindingElements.Add(transactionFlow);  
        }  
        bindingElements.Add(textEncoding);  
  
        // add transport (http or https)  
        bindingElements.Add(transport);  
        return bindingElements.Clone();  
    }  
    ```  
  
2. Adicionar suporte à configuração  
  
     Para expor o transporte por meio da configuração, o exemplo implementa mais`WSStreamedHttpBindingConfigurationElement` duas `WSStreamedHttpBindingSection`classes — e. A classe `WSStreamedHttpBindingSection` é um <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> que expõe `WSStreamedHttpBinding` para o sistema de configuração do WCF. A maior parte da implementação é delegada para `WSStreamedHttpBindingConfigurationElement`, que deriva de. <xref:System.ServiceModel.Configuration.StandardBindingElement> A classe `WSStreamedHttpBindingConfigurationElement` tem propriedades que correspondem às propriedades de `WSStreamedHttpBinding`e às funções para mapear cada elemento de configuração para uma associação.  
  
     Registre o manipulador com o sistema de configuração, adicionando a seção a seguir ao arquivo de configuração do serviço.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <extensions>  
          <bindingExtensions>  
            <add name="wsStreamedHttpBinding" type="Microsoft.ServiceModel.Samples.WSStreamedHttpBindingCollectionElement, WSStreamedHttpBinding, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
          </bindingExtensions>  
        </extensions>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     O manipulador pode ser referenciado na seção de configuração de serviceModel.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint  
                    address="https://localhost/servicemodelsamples/service.svc"  
                    bindingConfiguration="Binding"  
                    binding="wsStreamedHttpBinding"  
                    contract="Microsoft.ServiceModel.Samples.IStreamedEchoService"/>  
        </client>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Instale o ASP.NET 4,0 usando o comando a seguir.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Verifique se você executou as etapas listadas no [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Verifique se você executou as [instruções de instalação do certificado do servidor serviços de informações da Internet (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).  
  
4. Para compilar a solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5. Para executar o exemplo em uma configuração entre computadores, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
6. Quando a janela do cliente for exibida, digite "Sample. txt". Você deve encontrar uma "cópia de Sample. txt" em seu diretório.  
  
## <a name="the-wsstreamedhttpbinding-sample-service"></a>O serviço de exemplo WSStreamedHttpBinding  
 O serviço de exemplo que `WSStreamedHttpBinding` o usa está localizado no subdiretório de serviço. A implementação de `OperationContract` `MemoryStream` usa a para recuperar primeiro todos os dados do fluxo de entrada antes de `MemoryStream`retornar o. O serviço de exemplo é hospedado pelo Serviços de Informações da Internet (IIS).  
  
```  
[ServiceContract]  
public interface IStreamedEchoService  
{  
    [OperationContract]  
    Stream Echo(Stream data);  
}  
  
public class StreamedEchoService : IStreamedEchoService  
{  
    public Stream Echo(Stream data)  
    {  
        MemoryStream dataStorage = new MemoryStream();  
        byte[] byteArray = new byte[8192];  
        int bytesRead = data.Read(byteArray, 0, 8192);  
        while (bytesRead > 0)  
        {  
            dataStorage.Write(byteArray, 0, bytesRead);  
            bytesRead = data.Read(byteArray, 0, 8192);  
        }  
        data.Close();  
        dataStorage.Seek(0, SeekOrigin.Begin);  
  
        return dataStorage;  
    }  
}  
```  
  
## <a name="the-wsstreamedhttpbinding-sample-client"></a>O cliente de exemplo WSStreamedHttpBinding  
 O cliente usado para interagir com o serviço usando `WSStreamedHttpBinding` o está localizado no subdiretório do cliente. Como o certificado usado neste exemplo é um certificado de teste criado com MakeCert. exe, um alerta de segurança é exibido quando você tenta acessar um endereço HTTPS em seu navegador, https://localhost/servicemodelsamples/service.svc como. Para permitir que o cliente WCF trabalhe com um certificado de teste em vigor, algum código adicional foi adicionado ao cliente para suprimir o alerta de segurança. O código e a classe que o acompanha não são necessários ao usar certificados de produção.  
  
```  
// WARNING: This code is only required for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
