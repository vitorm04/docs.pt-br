---
title: Interceptor de mensagem personalizado
ms.date: 03/30/2017
ms.assetid: 73f20972-53f8-475a-8bfe-c133bfa225b0
ms.openlocfilehash: 433b14433a7e2dd6edad551a2732e9049a9861ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145080"
---
# <a name="custom-message-interceptor"></a>Interceptor de mensagem personalizado
Esta amostra demonstra o uso do modelo de extensibilidade do canal. Em particular, ele mostra como implementar um elemento de vinculação personalizado que cria fábricas de canais e ouvintes de canais para interceptar todas as mensagens recebidas e de saída em um determinado ponto da pilha de tempo de execução. A amostra também inclui um cliente e um servidor que demonstram o uso dessas fábricas personalizadas.  
  
 Nesta amostra, tanto o cliente quanto o serviço são programas de console (.exe). O cliente e o serviço fazem uso de uma biblioteca comum (.dll) que contém o elemento de vinculação personalizado e seus objetos de tempo de execução associados.  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\MessageInterceptor`  
  
 A amostra descreve o procedimento recomendado para criar um canal em camadas personalizado na Windows Communication Foundation (WCF), usando a estrutura do canal e seguindo as práticas recomendadas do WCF. As etapas para criar um canal em camadas personalizado sao as seguintes:  
  
1. Decida qual dos canais molda sua fábrica de canais e o ouvinte do canal suportará.  
  
2. Crie uma fábrica de canais e um ouvinte de canal que suporte as formas do seu canal.  
  
3. Adicione um elemento de vinculação que adiciona o canal em camadas personalizado a uma pilha de canais.  
  
4. Adicione uma seção de extensão de elemento de vinculação para expor o novo elemento de vinculação ao sistema de configuração.  
  
## <a name="channel-shapes"></a>Formas de canal  
 O primeiro passo para escrever um canal em camadas personalizado é decidir quais formas são necessárias para o canal. Para nosso inspetor de mensagens, apoiamos qualquer forma que a camada abaixo <xref:System.ServiceModel.Channels.IOutputChannel> de <xref:System.ServiceModel.Channels.IDuplexSessionChannel>nós suporta <xref:System.ServiceModel.Channels.IOutputChannel> (por exemplo, se a camada abaixo de nós pode construir e , então também expõe e <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).  
  
## <a name="channel-factory-and-listener-factory"></a>Fábrica de Canais e Fábrica de Ouvintes  
 O próximo passo na criação de um canal <xref:System.ServiceModel.Channels.IChannelFactory> em camadas <xref:System.ServiceModel.Channels.IChannelListener> personalizado é criar uma implementação para canais de clientes e de canais de serviço.  
  
 Essas aulas tomam uma fábrica interna e ouvinte, e delegam tudo, menos as `OnCreateChannel` chamadas `OnAcceptChannel` para a fábrica interna e ouvinte.  
  
```csharp
class InterceptingChannelFactory<TChannel> : ChannelFactoryBase<TChannel>  
{
    //...
}

class InterceptingChannelListener<TChannel> : ListenerFactoryBase<TChannel>  
{
    //...
}  
```  
  
## <a name="adding-a-binding-element"></a>Adicionando um elemento de vinculação  
 A amostra define um elemento `InterceptingBindingElement`de ligação personalizado: . `InterceptingBindingElement`toma `ChannelMessageInterceptor` uma entrada, e `ChannelMessageInterceptor` usa isso para manipular mensagens que passam por ela. Esta é a única classe que deve ser pública. A fábrica, o ouvinte e os canais podem ser implementações internas das interfaces públicas de tempo de execução.  
  
```csharp
public class InterceptingBindingElement : BindingElement
{
}
```  
  
## <a name="adding-configuration-support"></a>Adicionando suporte à configuração  
 Para integrar-se à configuração de vinculação, a biblioteca define um manipulador de seção de configuração como uma seção de extensão de elemento de vinculação. Os arquivos de configuração cliente e servidor devem registrar a extensão do elemento de vinculação com o sistema de configuração. Os implementadores que desejam expor seu elemento de vinculação ao sistema de configuração podem derivar dessa classe.  
  
```csharp
public abstract class InterceptingElement : BindingElementExtensionElement
{
    //...
}
```  
  
## <a name="adding-policy"></a>Adicionando política  
 Para integrar-se ao `InterceptingBindingElement` nosso sistema de políticas, implementa o IPolicyExportExtension para sinalizar que devemos participar na política de geração. Para suportar a política de importação em um cliente gerado, o `CreateMessageInterceptor`usuário pode registrar uma `ChannelMessageInterceptor` classe derivada de `InterceptingBindingElementImporter` e substituir () para gerar sua classe habilitada para políticas.  
  
## <a name="example-droppable-message-inspector"></a>Exemplo: Inspetor de mensagens droppable  
 Incluído na amostra é um `ChannelMessageInspector` exemplo de implementação de que as mensagens soltam.  
  
```csharp
class DroppingServerElement : InterceptingElement  
{  
    protected override ChannelMessageInterceptor CreateMessageInterceptor()  
    {  
        return new DroppingServerInterceptor();  
    }  
}  
```  
  
 Você pode acessá-lo a partir da configuração da seguinte forma:  
  
```xml  
<configuration>  
    ...  
    <system.serviceModel>  
        ...  
        <extensions>  
            <bindingElementExtensions>  
                <add name="droppingInterceptor"
                   type=  
          "Microsoft.ServiceModel.Samples.DroppingServerElement, library"/>  
            </bindingElementExtensions>  
        </extensions>  
    </system.serviceModel>  
</configuration>  
```  
  
 O cliente e o servidor usam essa seção de configuração recém-criada para inserir as fábricas personalizadas no nível mais baixo de suas pilhas de canais de tempo de execução (acima do nível de transporte).  
  
```xml  
<customBinding>  
  <binding name="sampleBinding">  
    <droppingInterceptor/>  
    <httpTransport/>  
  </binding>  
</customBinding>  
```  
  
 O cliente `MessageInterceptor` usa a biblioteca para adicionar um cabeçalho personalizado até mesmo mensagens numeradas. O serviço, por `MessageInterceptor` outro lado, usa biblioteca para soltar quaisquer mensagens que não tenham esse cabeçalho especial.  
  
 Você deve ver a seguinte saída do cliente após executar o serviço e, em seguida, o cliente.  
  
```console  
Reporting the next 10 wind speed  
100 kph  
Server dropped a message.  
90 kph  
80 kph  
Server dropped a message.  
70 kph  
60 kph  
Server dropped a message.  
50 kph  
40 kph  
Server dropped a message.  
30 kph  
20 kph  
Server dropped a message.  
10 kph  
Press ENTER to shut down client  
```  
  
 O cliente relata 10 velocidades de vento diferentes para o serviço, mas apenas marca metade deles com o cabeçalho especial.  
  
 No serviço, você deve ver a seguinte saída:  
  
```console  
Press ENTER to exit.  
Dangerous wind detected! Reported speed (90) is greater than 64 kph.  
Dangerous wind detected! Reported speed (70) is greater than 64 kph.  
5 wind speed reports have been received.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Instale ASP.NET 4.0 usando o seguinte comando.  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5. Executar Service.exe primeiro, em seguida, executar Client.exe e assistir ambas as janelas do console para saída.  
