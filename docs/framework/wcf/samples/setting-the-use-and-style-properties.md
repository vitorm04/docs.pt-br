---
title: Definindo o uso e as propriedades de estilo
ms.date: 03/30/2017
ms.assetid: c09a0600-116f-41cf-900a-1b7e4ea4e300
ms.openlocfilehash: d5e6409e3921d40b14b940786f6344aea657b84b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43421344"
---
# <a name="setting-the-use-and-style-properties"></a>Definindo o uso e as propriedades de estilo
Este exemplo demonstra como usar as propriedades de estilo e de uso sobre o <xref:System.ServiceModel.XmlSerializerFormatAttribute> e o <xref:System.ServiceModel.DataContractFormatAttribute>. Essas propriedades afetam como as mensagens são formatadas. Por padrão, o corpo da mensagem é formatado com o estilo definido como <xref:System.ServiceModel.OperationFormatStyle.Document>. Essas configurações podem ser especificadas no nível do contrato de serviço ou o nível de contrato de operação.  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 O <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> propriedade style determina como os metadados WSDL para o serviço é formatado. Os valores possíveis são <xref:System.ServiceModel.OperationFormatStyle.Document>, e <xref:System.ServiceModel.OperationFormatStyle.Rpc>. RPC significa que a representação do WSDL de mensagens trocadas para uma operação contém parâmetros como se fosse uma chamada de procedimento remoto. Confira o exemplo abaixo.  
  
```xml  
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">  
  <wsdl:part name="n1" type="xsd:double"/>  
  <wsdl:part name="n2" type="xsd:double"/>  
</wsdl:message>  
```  
  
 Definindo o estilo como <xref:System.ServiceModel.OperationFormatStyle.Document> significa que a representação do WSDL contém um único elemento que representa o documento trocado para uma operação conforme mostrado no exemplo a seguir.  
  
```xml  
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">  
  <wsdl:part name="parameters" element="tns:Add"/>  
</wsdl:message>  
```  
  
 O <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> propriedade determina o formato da mensagem. Os valores possíveis são <xref:System.ServiceModel.OperationFormatUse.Literal> e <xref:System.ServiceModel.OperationFormatUse.Encoded>; o valor padrão é <xref:System.ServiceModel.OperationFormatUse.Literal>. Literal significa que a mensagem é uma instância literal do esquema em WSDL, conforme mostrado no seguinte documento / Literal exemplo.  
  
```xml  
<Add xmlns="http://Microsoft.ServiceModel.Samples">  
  <n1>100</n1>  
  <n2>15.99</n2>  
</Add>  
```  
  
 Codificado significa que os esquemas WSDL são especificações abstratas codificadas de acordo com as regras encontradas na seção 5 do SOAP 1.1. O exemplo a seguir é um exemplo RPC/codificado.  
  
```xml  
<q1:Add xmlns:q1="http://Microsoft.ServiceModel.Samples">  
  <n1 xsi:type="xsd:double" xmlns="">100</n1>  
  <n2 xsi:type="xsd:double" xmlns="">15.99</n2>  
</q1:Add>  
```  
  
 O WS-I Basic Profile 1.0 proíbe o uso de <xref:System.ServiceModel.OperationFormatUse.Encoded> e você deve usar apenas quando necessário pelos serviços herdados. O `Encoded` formato de mensagem só está disponível ao usar o XmlSerializer.  
  
 Para que você possa ver as mensagens sendo enviadas e recebidas, este exemplo se baseia a [rastreamento e registro em log de mensagem](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md). A configuração de serviço e o código-fonte foram modificadas para habilitar e utilizar o rastreamento e o registro de mensagem. Além disso, o <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> foi configurado sem segurança, portanto, as mensagens registradas podem ser exibidas em um formato não criptografado. Os logs de rastreamento resultante (System.ServiceModel.e2e e Message.log) devem ser exibidos usando o [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Os rastreamentos são configurados para ser criado na pasta C:\LOGS. Crie a pasta antes de executar o exemplo. Para exibir o conteúdo da mensagem na ferramenta do Visualizador de rastreamento, selecione **mensagens** à esquerda e os painéis à direita da ferramenta.  
  
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
  
 Para ver a diferença entre os diferentes <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> e <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> configurações, modificá-los no serviço, gerar novamente o cliente, executar o exemplo e examinar o arquivo c:\logs\message.logs com a ferramenta Visualizador de rastreamento de serviço. Também observar o impacto sobre os metadados por meio da exibição http://localhost/ServiceModelSamples/service.svc?wsdl. Os metadados para os serviços normalmente é dividido em várias páginas. A página principal de wsdl contém associações WSDL, mas exibir http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0 para observar as definições de mensagem.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Crie um diretório c:\Logs. para mensagens de log. Conceder ao usuário permissões para esse diretório de gravação do serviço de rede.  
  
3.  Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\UseAndStyle`  
  
## <a name="see-also"></a>Consulte também
