---
title: Definindo as propriedades de uso e estilo-exemplos do WCF
ms.date: 03/30/2017
ms.assetid: c09a0600-116f-41cf-900a-1b7e4ea4e300
ms.openlocfilehash: 946f8f6aab253eb881faaba7adfdc68dc54d7f0b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958800"
---
# <a name="setting-the-use-and-style-properties"></a><span data-ttu-id="5e8e4-102">Definindo o uso e as propriedades de estilo</span><span class="sxs-lookup"><span data-stu-id="5e8e4-102">Setting the Use and Style Properties</span></span>

<span data-ttu-id="5e8e4-103">Este exemplo demonstra como usar as propriedades de uso e estilo no <xref:System.ServiceModel.XmlSerializerFormatAttribute> e no. <xref:System.ServiceModel.DataContractFormatAttribute></span><span class="sxs-lookup"><span data-stu-id="5e8e4-103">This sample demonstrates how to use the Use and Style properties on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> and the <xref:System.ServiceModel.DataContractFormatAttribute>.</span></span> <span data-ttu-id="5e8e4-104">Essas propriedades afetam o modo como as mensagens são formatadas.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-104">These properties affect how messages are formatted.</span></span> <span data-ttu-id="5e8e4-105">Por padrão, o corpo da mensagem é formatado com o estilo definido <xref:System.ServiceModel.OperationFormatStyle.Document>como.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-105">By default, the message body is formatted with the style set to <xref:System.ServiceModel.OperationFormatStyle.Document>.</span></span> <span data-ttu-id="5e8e4-106">Essas configurações podem ser especificadas no nível de contrato de serviço ou no nível de contrato de operação.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-106">These settings can be specified at either the service contract level or the operation contract level.</span></span>

> [!NOTE]
> <span data-ttu-id="5e8e4-107">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="5e8e4-108">A <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> Propriedade Style determina como os metadados WSDL para o serviço são formatados.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-108">The <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> style property determines how the WSDL metadata for the service is formatted.</span></span> <span data-ttu-id="5e8e4-109">Os valores possíveis <xref:System.ServiceModel.OperationFormatStyle.Document>são e <xref:System.ServiceModel.OperationFormatStyle.Rpc>.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-109">Possible values are <xref:System.ServiceModel.OperationFormatStyle.Document>, and <xref:System.ServiceModel.OperationFormatStyle.Rpc>.</span></span> <span data-ttu-id="5e8e4-110">RPC significa que a representação WSDL das mensagens trocadas para uma operação contém parâmetros como se fosse uma chamada de procedimento remota.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-110">RPC means that the WSDL representation of messages exchanged for an operation contains parameters as if it were a remote procedure call.</span></span> <span data-ttu-id="5e8e4-111">Confira o exemplo abaixo.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-111">The following is an example.</span></span>

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="n1" type="xsd:double"/>
  <wsdl:part name="n2" type="xsd:double"/>
</wsdl:message>
```

<span data-ttu-id="5e8e4-112">Definir o estilo como <xref:System.ServiceModel.OperationFormatStyle.Document> significa que a representação WSDL contém um único elemento que representa o documento que é trocado para uma operação, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-112">Setting the style to <xref:System.ServiceModel.OperationFormatStyle.Document> means that the WSDL representation contains a single element that represents the document that is exchanged for an operation as shown in the following example.</span></span>

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="parameters" element="tns:Add"/>
</wsdl:message>
```

<span data-ttu-id="5e8e4-113">A <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> propriedade determina o formato da mensagem.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-113">The <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> property determines the format of the message.</span></span> <span data-ttu-id="5e8e4-114">Os valores possíveis <xref:System.ServiceModel.OperationFormatUse.Literal> são <xref:System.ServiceModel.OperationFormatUse.Encoded>e; o valor padrão <xref:System.ServiceModel.OperationFormatUse.Literal>é.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-114">Possible values are <xref:System.ServiceModel.OperationFormatUse.Literal> and <xref:System.ServiceModel.OperationFormatUse.Encoded>; the default value is <xref:System.ServiceModel.OperationFormatUse.Literal>.</span></span> <span data-ttu-id="5e8e4-115">Literal significa que a mensagem é uma instância literal do esquema no WSDL, conforme mostrado no exemplo de documento/literal a seguir.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-115">Literal means that the message is a literal instance of the schema in the WSDL as shown in the following Document/ Literal example.</span></span>

```xml
<Add xmlns="http://Microsoft.ServiceModel.Samples">
  <n1>100</n1>
  <n2>15.99</n2>
</Add>
```

<span data-ttu-id="5e8e4-116">Encoded significa que os esquemas no WSDL são especificações abstratas que são codificadas de acordo com as regras encontradas na seção 5 do SOAP 1,1.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-116">Encoded means that the schemas in the WSDL are abstract specifications that are encoded according to the rules found in SOAP 1.1 section 5.</span></span> <span data-ttu-id="5e8e4-117">Este é um exemplo de RPC/codificado.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-117">The following is an RPC/Encoded example.</span></span>

```xml
<q1:Add xmlns:q1="http://Microsoft.ServiceModel.Samples">
  <n1 xsi:type="xsd:double" xmlns="">100</n1>
  <n2 xsi:type="xsd:double" xmlns="">15.99</n2>
</q1:Add>
```

<span data-ttu-id="5e8e4-118">O WS-I Basic Profile 1,0 proíbe o uso de <xref:System.ServiceModel.OperationFormatUse.Encoded> e você só deve usá-lo quando exigido pelos serviços herdados.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-118">The WS-I Basic Profile 1.0 prohibits the use of <xref:System.ServiceModel.OperationFormatUse.Encoded> and you should only use it when required by legacy services.</span></span> <span data-ttu-id="5e8e4-119">O `Encoded` formato da mensagem só está disponível ao usar o XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-119">The `Encoded` message format is only available when using the XmlSerializer.</span></span>

<span data-ttu-id="5e8e4-120">Para permitir que você veja as mensagens que estão sendo enviadas e recebidas, este exemplo é baseado no [rastreamento e no log de mensagens](tracing-and-message-logging.md).</span><span class="sxs-lookup"><span data-stu-id="5e8e4-120">To allow you to see the messages being sent and received, this sample is based on the [Tracing and Message Logging](tracing-and-message-logging.md).</span></span> <span data-ttu-id="5e8e4-121">A configuração do serviço e o código-fonte foram modificados para habilitar e utilizar rastreamento e log de mensagens.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-121">The service configuration and source code have been modified to enable and utilize tracing and message logging.</span></span> <span data-ttu-id="5e8e4-122">Além disso, o <xref:System.ServiceModel.WSHttpBinding> foi configurado sem segurança, portanto, as mensagens registradas podem ser exibidas em um formato não criptografado.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-122">In addition, the <xref:System.ServiceModel.WSHttpBinding> has been configured without security, so the logged messages can be viewed in an unencrypted format.</span></span> <span data-ttu-id="5e8e4-123">Os logs de rastreamento resultantes (System. ServiceModel. e2e e Message. log) devem ser exibidos usando a [ferramenta do Visualizador de rastreamento de serviço (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="5e8e4-123">The resulting trace logs (System.ServiceModel.e2e and Message.log) should be viewed by using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="5e8e4-124">Os rastreamentos são configurados para serem criados na pasta C:\LOGS.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-124">The traces are configured to be created in the C:\LOGS folder.</span></span> <span data-ttu-id="5e8e4-125">Crie a pasta antes de executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-125">Create the folder before running the sample.</span></span> <span data-ttu-id="5e8e4-126">Para exibir o conteúdo da mensagem na ferramenta Visualizador de rastreamento, selecione **mensagens** nos painéis esquerdo e direito da ferramenta.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-126">To view message contents in the Trace Viewer tool, select **Messages** in both the left and the right panes of the tool.</span></span>

<span data-ttu-id="5e8e4-127">O código a seguir mostra o contrato de serviço <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> com a propriedade <xref:System.ServiceModel.OperationFormatUse> definida como e o formato do corpo da mensagem foi alterado <xref:System.ServiceModel.OperationFormatStyle> do <xref:System.ServiceModel.OperationFormatStyle.Document>padrão para.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-127">The following code shows the service contract with the <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> property set to <xref:System.ServiceModel.OperationFormatUse> and the format of the message body changed from the default <xref:System.ServiceModel.OperationFormatStyle> to <xref:System.ServiceModel.OperationFormatStyle.Document>.</span></span>

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

<span data-ttu-id="5e8e4-128">Para ver a diferença entre as diferentes <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> configurações, modifique-as no serviço, gere novamente o cliente, execute o exemplo e examine o arquivo c:\logs\message.logs com a ferramenta Visualizador de rastreamento de serviço.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-128">To see the difference between the different <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> and <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> settings, modify them in the service, regenerate the client, run the sample, and examine the c:\logs\message.logs file with the Service Trace Viewer tool.</span></span> <span data-ttu-id="5e8e4-129">Além disso, observe o impacto nos metadados exibindo `http://localhost/ServiceModelSamples/service.svc?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-129">Also observe the impact on the metadata by viewing `http://localhost/ServiceModelSamples/service.svc?wsdl`.</span></span> <span data-ttu-id="5e8e4-130">Os metadados dos serviços normalmente são divididos em várias páginas.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-130">The metadata for services is typically broken up into multiple pages.</span></span> <span data-ttu-id="5e8e4-131">A página WSDL principal contém as associações WSDL, mas a exibição `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0` para observar as definições de mensagem.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-131">The main wsdl page contains the WSDL bindings, but view `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0` to observe the message definitions.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5e8e4-132">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="5e8e4-132">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="5e8e4-133">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5e8e4-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="5e8e4-134">Crie um diretório do C:\LOGS para mensagens de log.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-134">Create a C:\LOGS directory for logging messages.</span></span> <span data-ttu-id="5e8e4-135">Conceda permissões de gravação ao serviço de rede do usuário para esse diretório.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-135">Give the user Network Service write permissions for this directory.</span></span>

3. <span data-ttu-id="5e8e4-136">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5e8e4-136">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="5e8e4-137">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5e8e4-137">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5e8e4-138">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5e8e4-139">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-139">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="5e8e4-140">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5e8e4-141">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-141">This sample is located in the following directory.</span></span>
> 
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\UseAndStyle`
