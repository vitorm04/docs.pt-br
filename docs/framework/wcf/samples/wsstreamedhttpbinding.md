---
title: WSStreamedHttpBinding
ms.date: 03/30/2017
ms.assetid: 97ce4d3d-ca6f-45fa-b33b-2429bb84e65b
ms.openlocfilehash: f146e469a323dffa2cdb9b76b6956be97747b2de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="wsstreamedhttpbinding"></a>WSStreamedHttpBinding
O exemplo demonstra como criar uma associação que foi projetada para oferecer suporte a cenários de streaming quando o transporte HTTP é usado.  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Binding\WSStreamedHttpBinding`  
  
 As etapas para criar e configurar uma nova associação padrão são da seguinte maneira.  
  
1.  Criar uma nova associação padrão  
  
     As associações padrão no Windows Communication Foundation (WCF), como basicHttpBinding e netTcpBinding configurar transportes subjacentes e pilha de canais para requisitos específicos. Neste exemplo, `WSStreamedHttpBinding` configura a pilha de canais para dar suporte a streaming. Por padrão, WS-Security e sistema de mensagens confiável não foram adicionadas à pilha de canais porque ambos os recursos não são suportados pelo streaming. A nova associação é implementada na classe `WSStreamedHttpBinding` que deriva de <xref:System.ServiceModel.Channels.Binding>. O `WSStreamedHttpBinding` contém os seguintes elementos de associação: <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, e <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>. A classe fornece um `CreateBindingElements()` método para configurar a pilha de associação resultante, conforme mostrado no código de exemplo a seguir.  
  
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
  
     Para expor o transporte por meio da configuração de exemplo implementa duas classes mais —`WSStreamedHttpBindingConfigurationElement` e `WSStreamedHttpBindingSection`. A classe `WSStreamedHttpBindingSection` é um <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> que expõe `WSStreamedHttpBinding` para o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sistema de configuração. A maior parte da implementação é delegada ao `WSStreamedHttpBindingConfigurationElement`, que é derivado de <xref:System.ServiceModel.Configuration.StandardBindingElement>. A classe `WSStreamedHttpBindingConfigurationElement` tem propriedades que correspondem às propriedades de `WSStreamedHttpBinding`e as funções para mapear cada elemento de configuração para uma associação.  
  
     Registre o manipulador com o sistema de configuração, adicionando a seguinte seção ao arquivo de configuração do serviço.  
  
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
  
     O manipulador pode ser referenciado na seção de configuração do serviceModel.  
  
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
  
2.  Certifique-se de que você executou as etapas listadas na [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Certifique-se de que você executou o [instruções de instalação do certificado de servidor de serviços de informações da Internet (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).  
  
4.  Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5.  Para executar o exemplo em uma configuração entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
6.  Quando a janela do cliente é exibida, digite "Txt". Você deve encontrar uma "cópia de txt" em seu diretório.  
  
## <a name="the-wsstreamedhttpbinding-sample-service"></a>O serviço de exemplo WSStreamedHttpBinding  
 O serviço de exemplo que usa `WSStreamedHttpBinding` está localizado no subdiretório de serviço. A implementação de `OperationContract` usa um `MemoryStream` para recuperar todos os dados do fluxo de entrada antes de retornar o `MemoryStream`. O exemplo de serviço é hospedado por serviços de informações da Internet (IIS).  
  
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
 O cliente que é usado para interagir com o serviço usando `WSStreamedHttpBinding` está localizado no subdiretório de cliente. Como o certificado usado neste exemplo é um certificado de teste criado com o Makecert.exe, um alerta de segurança exibe quando você tenta acessar um endereço HTTPS em seu navegador, como https://localhost/servicemodelsamples/service.svc. Para permitir que o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente para trabalhar com um certificado de teste no lugar, foi adicionado um código adicional para o cliente para suprimir o alerta de segurança. O código e a classe associada não são necessárias ao usar certificados de produção.  
  
```  
// WARNING: This code is only required for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
## <a name="see-also"></a>Consulte também
