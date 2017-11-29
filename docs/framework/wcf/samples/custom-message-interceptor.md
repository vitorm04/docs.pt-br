---
title: Interceptor de mensagem personalizado
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 73f20972-53f8-475a-8bfe-c133bfa225b0
caps.latest.revision: "24"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cdc547c26b23c74bb77640e826272da933f45a0d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="custom-message-interceptor"></a>Interceptor de mensagem personalizado
Este exemplo demonstra o uso do modelo de extensibilidade do canal. Em particular, ele mostra como implementar um elemento de associação personalizada que cria fábricas de canais e ouvintes de canais para interceptar todas as mensagens de entrada e saídas em um ponto específico na pilha de tempo de execução. O exemplo também inclui um cliente e servidor que demonstram o uso dessas fábricas personalizado.  
  
 Neste exemplo, o cliente e o serviço são programas de console (.exe). O cliente e o serviço que ambos fazer usam de uma biblioteca comum (. dll) que contém o elemento de associação personalizada e seus objetos de tempo de execução associados.  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\MessageInterceptor`  
  
 O exemplo descreve o procedimento recomendado para criar um canal personalizado em camadas em [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], usando a estrutura de canal e seguindo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] práticas recomendadas. As etapas para criar um canal em camadas personalizado são da seguinte maneira:  
  
1.  Decida quais das formas de canal dará suporte a sua fábrica de canal e ouvinte de canal.  
  
2.  Crie uma fábrica de canais e um ouvinte de canal que oferecem suporte a suas formas de canal.  
  
3.  Adicione um elemento de associação que adiciona o canal em camadas personalizado para uma pilha de canais.  
  
4.  Adicione uma seção de extensão do elemento de associação para expor o novo elemento de associação para o sistema de configuração.  
  
## <a name="channel-shapes"></a>Formas de canal  
 A primeira etapa na composição de um canal em camadas personalizado é decidir quais formas são necessárias para o canal. Para nosso Inspetor de mensagem, há suporte para qualquer formato que oferece suporte a camada abaixo nos (por exemplo, se a camada abaixo nos pode criar <xref:System.ServiceModel.Channels.IOutputChannel> e <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, em seguida, podemos também expor <xref:System.ServiceModel.Channels.IOutputChannel> e <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).  
  
## <a name="channel-factory-and-listener-factory"></a>Fábrica de canais e fábrica de escuta  
 A próxima etapa na gravação de um canal em camadas personalizado é criar uma implementação de <xref:System.ServiceModel.Channels.IChannelFactory> de canais de cliente e de <xref:System.ServiceModel.Channels.IChannelListener> para canais de serviço.  
  
 Essas classes uma fábrica interna e ouvinte e delegar tudo, exceto o `OnCreateChannel` e `OnAcceptChannel` chamadas para a fábrica interna e o ouvinte.  
  
```  
class InterceptingChannelFactory<TChannel> : ChannelFactoryBase<TChannel>  
{ ... }  
class InterceptingChannelListener<TChannel> : ListenerFactoryBase<TChannel>  
{ ... }  
```  
  
## <a name="adding-a-binding-element"></a>Adicionando um elemento de associação  
 O exemplo define um elemento de associação personalizada: `InterceptingBindingElement`. `InterceptingBindingElement`leva um `ChannelMessageInterceptor` como uma entrada e usa esse `ChannelMessageInterceptor` para manipular as mensagens que passam por ele. Essa é a única classe que deve ser público. A fábrica, ouvinte e canais podem ser internas implementações das interfaces públicas do tempo de execução.  
  
```  
public class InterceptingBindingElement : BindingElement  
```  
  
## <a name="adding-configuration-support"></a>Adicionando suporte à configuração  
 Para integrar com configuração de associação, a biblioteca define um manipulador de seção de configuração como uma seção de extensão de elemento de associação. Os arquivos de configuração do cliente e o servidor devem registrar a extensão de elemento de associação com o sistema de configuração. Implementadores de que deseja expor seu elemento de associação para o sistema de configuração podem derivar desta classe.  
  
```  
public abstract class InterceptingElement : BindingElementExtensionElement { ... }  
```  
  
## <a name="adding-policy"></a>Adicionar política  
 A integração com nosso sistema de política, `InterceptingBindingElement` implementa IPolicyExportExtension para sinalizar que podemos deve participar de geração de política. Para dar suporte à política de importação em um cliente gerado, o usuário pode registrar uma classe derivada de `InterceptingBindingElementImporter` e substituir `CreateMessageInterceptor`() para gerar sua política habilitada `ChannelMessageInterceptor` classe.  
  
## <a name="example-droppable-message-inspector"></a>Exemplo: Inspetor de mensagem Droppable  
 Incluído no exemplo é um exemplo de implementação de `ChannelMessageInspector` que descarta mensagens.  
  
```  
class DroppingServerElement : InterceptingElement  
{  
    protected override ChannelMessageInterceptor CreateMessageInterceptor()  
    {  
        return new DroppingServerInterceptor();  
    }  
}  
```  
  
 Você pode acessá-lo da configuração da seguinte maneira:  
  
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
  
 O cliente e o servidor usam esta seção de configuração criado recentemente para inserir as fábricas personalizadas do nível mais baixo de suas pilhas de canal do tempo de execução (acima do nível de transporte).  
  
```xml  
<customBinding>  
  <binding name="sampleBinding">  
    <droppingInterceptor/>  
    <httpTransport/>  
  </binding>  
</customBinding>  
```  
  
 O cliente usa o `MessageInterceptor` numeradas de biblioteca para adicionar um cabeçalho personalizado para até mesmo mensagens. O serviço por outro lado usa `MessageInterceptor` biblioteca para descartar qualquer mensagem que não têm esse cabeçalho especial.  
  
 Você verá a seguinte saída de cliente depois de executar o serviço e, em seguida, o cliente.  
  
```  
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
  
 O cliente relata 10 velocidade do vento diferentes para o serviço, mas somente marcas metade deles com o cabeçalho especial.  
  
 Sobre o serviço, você verá a seguinte saída:  
  
```  
Press ENTER to exit.  
Dangerous wind detected! Reported speed (90) is greater than 64 kph.  
Dangerous wind detected! Reported speed (70) is greater than 64 kph.  
5 wind speed reports have been received.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Instalar [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 usando o comando a seguir.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5.  Execute Service.exe primeiro executar Client.exe e assista a ambas as janelas do console de saída.  
  
## <a name="see-also"></a>Consulte também
