---
title: Definindo as amostras de propriedades de uso e estilo
ms.date: 03/30/2017
ms.assetid: c09a0600-116f-41cf-900a-1b7e4ea4e300
ms.openlocfilehash: f400c0bc08588afa951ae33f221663b47b37602c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144026"
---
# <a name="setting-the-use-and-style-properties"></a>Definindo o uso e as propriedades de estilo

Esta amostra demonstra como usar as propriedades <xref:System.ServiceModel.XmlSerializerFormatAttribute> Use <xref:System.ServiceModel.DataContractFormatAttribute>e Style no e no . Essas propriedades afetam a formacomo as mensagens são formatadas. Por padrão, o corpo da mensagem <xref:System.ServiceModel.OperationFormatStyle.Document>é formatado com o estilo definido como . Essas configurações podem ser especificadas tanto no nível do contrato de serviço quanto no nível do contrato de operação.

> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.

A <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> propriedade de estilo determina como os metadados do WSDL para o serviço são formatados. Os valores possíveis são <xref:System.ServiceModel.OperationFormatStyle.Document>, e <xref:System.ServiceModel.OperationFormatStyle.Rpc>. RPC significa que a representação WSDL de mensagens trocadas por uma operação contém parâmetros como se fosse uma chamada de procedimento remoto. A seguir, é mostrado um exemplo.

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="n1" type="xsd:double"/>
  <wsdl:part name="n2" type="xsd:double"/>
</wsdl:message>
```

Definir o <xref:System.ServiceModel.OperationFormatStyle.Document> estilo para significa que a representação WSDL contém um único elemento que representa o documento que é trocado por uma operação, como mostrado no exemplo a seguir.

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="parameters" element="tns:Add"/>
</wsdl:message>
```

A <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> propriedade determina o formato da mensagem. Os valores possíveis são <xref:System.ServiceModel.OperationFormatUse.Literal> e; <xref:System.ServiceModel.OperationFormatUse.Encoded> o valor <xref:System.ServiceModel.OperationFormatUse.Literal>padrão é . Literal significa que a mensagem é uma instância literal do esquema no WSDL, como mostrado no exemplo documental/literal a seguir.

```xml
<Add xmlns="http://Microsoft.ServiceModel.Samples">
  <n1>100</n1>
  <n2>15.99</n2>
</Add>
```

Codificado significa que os esquemas no WSDL são especificações abstratas que são codificadas de acordo com as regras encontradas na seção SOAP 1.1 5. A seguir está um exemplo RPC/Codificado.

```xml
<q1:Add xmlns:q1="http://Microsoft.ServiceModel.Samples">
  <n1 xsi:type="xsd:double" xmlns="">100</n1>
  <n2 xsi:type="xsd:double" xmlns="">15.99</n2>
</q1:Add>
```

O Perfil Básico WS-I 1.0 <xref:System.ServiceModel.OperationFormatUse.Encoded> proíbe o uso e você só deve usá-lo quando exigido por serviços legados. O `Encoded` formato da mensagem só está disponível quando se usa o XmlSerializer.

Para permitir que você veja as mensagens que estão sendo enviadas e recebidas, esta amostra é baseada no [Rastreamento e Registro de Mensagens](tracing-and-message-logging.md). A configuração do serviço e o código-fonte foram modificados para habilitar e utilizar o rastreamento e o registro de mensagens. Além disso, <xref:System.ServiceModel.WSHttpBinding> o foi configurado sem segurança, para que as mensagens registradas possam ser visualizadas em um formato não criptografado. Os registros de rastreamento resultantes (System.ServiceModel.e2e e Message.log) devem ser visualizados usando a [Ferramenta de Visualização de Rastreamento de Serviço (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md). Os traços estão configurados para serem criados na pasta C:\LOGS. Crie a pasta antes de executar a amostra. Para exibir o conteúdo da mensagem na ferramenta Trace Viewer, selecione **Mensagens** nos painéis esquerdo e direito da ferramenta.

O código a seguir mostra <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> o <xref:System.ServiceModel.OperationFormatUse> contrato de serviço com a propriedade <xref:System.ServiceModel.OperationFormatStyle> <xref:System.ServiceModel.OperationFormatStyle.Document>definida e o formato do corpo de mensagem alterado do padrão para .

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"),
XmlSerializerFormat(Style = OperationFormatStyle.Rpc,
                                 Use = OperationFormatUse.Encoded)]
public interface IUseAndStyleCalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    [OperationContract]
    double Subtract(double n1, double n2);
    [OperationContract]
    double Multiply(double n1, double n2);
    [OperationContract]
    double Divide(double n1, double n2);
}
```

Para ver a diferença <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> entre as diferentes e as configurações, modifique-as no serviço, regenere o cliente, execute a amostra e examine o arquivo c:\logs\message.logs com a ferramenta Visualizador de rastreamento de serviço. Observe também o impacto nos `http://localhost/ServiceModelSamples/service.svc?wsdl`metadados visualizando . Os metadados para serviços são normalmente divididos em várias páginas. A página principal do wsdl contém as ligações `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0` WSDL, mas é vista para observar as definições da mensagem.

## <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo

1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Crie um diretório C:\LOGS para registrar mensagens. Dê ao usuário permissões de gravação do Serviço de Rede para este diretório.

3. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](building-the-samples.md).

4. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](running-the-samples.md).

> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\UseAndStyle`
