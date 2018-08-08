---
title: Definindo o uso e as propriedades de estilo
ms.date: 03/30/2017
ms.assetid: c09a0600-116f-41cf-900a-1b7e4ea4e300
ms.openlocfilehash: 74d5baca77fd1af6260def762094b3ce01816179
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33506810"
---
# <a name="setting-the-use-and-style-properties"></a>Definindo o uso e as propriedades de estilo
Este exemplo demonstra como usar as propriedades de uso e estilo no <xref:System.ServiceModel.XmlSerializerFormatAttribute> e <xref:System.ServiceModel.DataContractFormatAttribute>. Essas propriedades afetam como as mensagens são formatadas. Por padrão, o corpo da mensagem é formatado com o estilo definido como <xref:System.ServiceModel.OperationFormatStyle.Document>. Essas configurações podem ser especificadas em nível de contrato de serviço ou nível de contrato da operação.  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 O <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> propriedade style determina como os metadados WSDL para o serviço são formatados. Os valores possíveis são <xref:System.ServiceModel.OperationFormatStyle.Document>, e <xref:System.ServiceModel.OperationFormatStyle.Rpc>. RPC significa que a representação de WSDL de mensagens trocadas para uma operação contém parâmetros, como se fosse uma chamada de procedimento remoto. Confira o exemplo abaixo.  
  
```xml  
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">  
  <wsdl:part name="n1" type="xsd:double"/>  
  <wsdl:part name="n2" type="xsd:double"/>  
</wsdl:message>  
```  
  
 Definindo o estilo como <xref:System.ServiceModel.OperationFormatStyle.Document> significa que a representação de WSDL contém um único elemento que representa o documento que é trocado por uma operação, como mostrado no exemplo a seguir.  
  
```xml  
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">  
  <wsdl:part name="parameters" element="tns:Add"/>  
</wsdl:message>  
```  
  
 O <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> propriedade determina o formato da mensagem. Os valores possíveis são <xref:System.ServiceModel.OperationFormatUse.Literal> e <xref:System.ServiceModel.OperationFormatUse.Encoded>; o valor padrão é <xref:System.ServiceModel.OperationFormatUse.Literal>. Literal significa que a mensagem é uma instância literal do esquema no WSDL, conforme mostrado no seguinte documento / Literal exemplo.  
  
```xml  
<Add xmlns="http://Microsoft.ServiceModel.Samples">  
  <n1>100</n1>  
  <n2>15.99</n2>  
</Add>  
```  
  
 Codificado significa que os esquemas no WSDL são especificações abstratas que são codificadas de acordo com as regras encontradas na seção 5 do SOAP 1.1. O seguinte é um exemplo RPC/Encoded.  
  
```xml  
<q1:Add xmlns:q1="http://Microsoft.ServiceModel.Samples">  
  <n1 xsi:type="xsd:double" xmlns="">100</n1>  
  <n2 xsi:type="xsd:double" xmlns="">15.99</n2>  
</q1:Add>  
```  
  
 O WS-I Basic Profile 1.0 proíbe o uso de <xref:System.ServiceModel.OperationFormatUse.Encoded> e você deve usar apenas quando necessário por serviços legados. O `Encoded` formato de mensagem só está disponível ao usar o XmlSerializer.  
  
 Para permitir que você veja as mensagens que estão sendo enviados e recebidos, este exemplo se baseia o [rastreamento e registro em log de mensagem](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md). A configuração de serviço e o código-fonte foram modificados para habilitar e usar rastreamento e o registro de mensagem. Além disso, o <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> foi configurado sem segurança, para que as mensagens registradas podem ser exibidas em um formato não criptografado. Os logs de rastreamento resultante (System.ServiceModel.e2e e Message.log) devem ser exibidos usando o [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Os rastreamentos são configurados para ser criado na pasta c:\Logs. Crie a pasta antes de executar o exemplo. Para exibir o conteúdo da mensagem na ferramenta do Visualizador de rastreamento, selecione **mensagens** à esquerda e os painéis à direita da ferramenta.  
  
 O código a seguir mostra o contrato de serviço com o <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> propriedade definida como <xref:System.ServiceModel.OperationFormatUse> e o formato do corpo da mensagem é alterado do padrão <xref:System.ServiceModel.OperationFormatStyle> para <xref:System.ServiceModel.OperationFormatStyle.Document>.  
  
```  
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
  
 Para ver a diferença entre os diferentes <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> e <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> configurações, modificá-las no serviço, gere novamente o cliente, executar o exemplo e examine o arquivo de c:\logs\message.logs com a ferramenta do Visualizador de rastreamento de serviço. Observe também o impacto sobre os metadados exibindo http://localhost/ServiceModelSamples/service.svc?wsdl. Os metadados de serviços normalmente é dividido em várias páginas. A página principal de wsdl contém as associações de WSDL, mas exibir http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0 para observar as definições de mensagem.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Crie um diretório c:\Logs. para mensagens de log. Conceda ao usuário permissões para este diretório de gravação do serviço de rede.  
  
3.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\UseAndStyle`  
  
## <a name="see-also"></a>Consulte também
