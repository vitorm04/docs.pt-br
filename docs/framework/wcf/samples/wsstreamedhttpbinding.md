---
title: WSStreamedHttpBinding
ms.date: 03/30/2017
ms.assetid: 97ce4d3d-ca6f-45fa-b33b-2429bb84e65b
ms.openlocfilehash: 96dccbc971c9ef5a59557100adb6df24a745ea5d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58828011"
---
# <a name="wsstreamedhttpbinding"></a>WSStreamedHttpBinding
O exemplo demonstra como criar uma associação que é projetada para dar suporte a cenários de transmissão quando o transporte HTTP é usado.  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Binding\WSStreamedHttpBinding`  
  
 As etapas para criar e configurar uma nova associação padrão são da seguinte maneira.  
  
1.  Criar uma nova associação padrão  
  
     As ligações padrão no Windows Communication Foundation (WCF), como basicHttpBinding e netTcpBinding configurar os transportes subjacentes e a pilha de canais para requisitos específicos. Neste exemplo, `WSStreamedHttpBinding` configura a pilha de canais para dar suporte a streaming. Por padrão, WS-Security e o sistema de mensagens confiável não são adicionados à pilha de canal porque os dois recursos não têm suporte de streaming. A nova associação é implementada na classe `WSStreamedHttpBinding` que deriva de <xref:System.ServiceModel.Channels.Binding>. O `WSStreamedHttpBinding` contém os seguintes elementos de associação: <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, e <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>. A classe fornece um `CreateBindingElements()` método para configurar a pilha de associação resultante, conforme mostrado no código de exemplo a seguir.  
  
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
  
2.  Adicionar suporte de configuração  
  
     Para expor o transporte por meio da configuração, a amostra implementa duas classes mais —`WSStreamedHttpBindingConfigurationElement` e `WSStreamedHttpBindingSection`. A classe `WSStreamedHttpBindingSection` é um <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> que expõe `WSStreamedHttpBinding` para o sistema de configuração do WCF. A maior parte da implementação é delegada ao `WSStreamedHttpBindingConfigurationElement`, que é derivada de <xref:System.ServiceModel.Configuration.StandardBindingElement>. A classe `WSStreamedHttpBindingConfigurationElement` tem propriedades que correspondem às propriedades de `WSStreamedHttpBinding`e as funções para mapear cada elemento de configuração para uma associação.  
  
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
  
     O manipulador pode ser referenciado da seção de configuração de serviceModel.  
  
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
  
1.  Instalar [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 usando o comando a seguir.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Certifique-se de que você executou as etapas listadas em [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Certifique-se de que você tenha executado o [instruções de instalação do certificado de servidor de serviços de informações da Internet (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).  
  
4.  Para criar a solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5.  Para executar o exemplo em uma configuração de várias máquinas, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
6.  Quando a janela do cliente for exibida, digite "Txt". Você deve encontrar um "cópia de exemplo. txt" no seu diretório.  
  
## <a name="the-wsstreamedhttpbinding-sample-service"></a>O serviço de exemplo WSStreamedHttpBinding  
 O serviço de exemplo que usa `WSStreamedHttpBinding` está localizado no subdiretório do serviço. A implementação de `OperationContract` usa um `MemoryStream` primeiro recuperar todos os dados do fluxo de entrada antes de retornar o `MemoryStream`. O serviço de exemplo é hospedado pelo Internet Information Services (IIS).  
  
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
 O cliente que é usado para interagir com o serviço usando `WSStreamedHttpBinding` está localizado no subdiretório do cliente. Como o certificado usado neste exemplo é um certificado de teste criado com Makecert.exe, um alerta de segurança exibe quando você tenta acessar um endereço HTTPS em seu navegador, como https://localhost/servicemodelsamples/service.svc. Para permitir que o cliente do WCF para trabalhar com um certificado de teste em vigor, o código adicional foi adicionado ao cliente para suprimir o alerta de segurança. O código e a classe que acompanha este artigo não são necessários ao usar certificados de produção.  
  
```  
// WARNING: This code is only required for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
