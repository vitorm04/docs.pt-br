---
title: Definindo as propriedades de estilo e de uso - exemplos do WCF
ms.date: 03/30/2017
ms.assetid: c09a0600-116f-41cf-900a-1b7e4ea4e300
ms.openlocfilehash: 64cf64cf5d53ef0dfb4bc38cf86f91c7acd2e5af
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007858"
---
# <a name="setting-the-use-and-style-properties"></a><span data-ttu-id="cb12d-102">Definindo o uso e as propriedades de estilo</span><span class="sxs-lookup"><span data-stu-id="cb12d-102">Setting the Use and Style Properties</span></span>

<span data-ttu-id="cb12d-103">Este exemplo demonstra como usar as propriedades de estilo e de uso sobre o <xref:System.ServiceModel.XmlSerializerFormatAttribute> e o <xref:System.ServiceModel.DataContractFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="cb12d-103">This sample demonstrates how to use the Use and Style properties on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> and the <xref:System.ServiceModel.DataContractFormatAttribute>.</span></span> <span data-ttu-id="cb12d-104">Essas propriedades afetam como as mensagens são formatadas.</span><span class="sxs-lookup"><span data-stu-id="cb12d-104">These properties affect how messages are formatted.</span></span> <span data-ttu-id="cb12d-105">Por padrão, o corpo da mensagem é formatado com o estilo definido como <xref:System.ServiceModel.OperationFormatStyle.Document>.</span><span class="sxs-lookup"><span data-stu-id="cb12d-105">By default, the message body is formatted with the style set to <xref:System.ServiceModel.OperationFormatStyle.Document>.</span></span> <span data-ttu-id="cb12d-106">Essas configurações podem ser especificadas no nível do contrato de serviço ou o nível de contrato de operação.</span><span class="sxs-lookup"><span data-stu-id="cb12d-106">These settings can be specified at either the service contract level or the operation contract level.</span></span>

> [!NOTE]
>  <span data-ttu-id="cb12d-107">As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="cb12d-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="cb12d-108">O <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> propriedade style determina como os metadados WSDL para o serviço é formatado.</span><span class="sxs-lookup"><span data-stu-id="cb12d-108">The <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> style property determines how the WSDL metadata for the service is formatted.</span></span> <span data-ttu-id="cb12d-109">Os valores possíveis são <xref:System.ServiceModel.OperationFormatStyle.Document>, e <xref:System.ServiceModel.OperationFormatStyle.Rpc>.</span><span class="sxs-lookup"><span data-stu-id="cb12d-109">Possible values are <xref:System.ServiceModel.OperationFormatStyle.Document>, and <xref:System.ServiceModel.OperationFormatStyle.Rpc>.</span></span> <span data-ttu-id="cb12d-110">RPC significa que a representação do WSDL de mensagens trocadas para uma operação contém parâmetros como se fosse uma chamada de procedimento remoto.</span><span class="sxs-lookup"><span data-stu-id="cb12d-110">RPC means that the WSDL representation of messages exchanged for an operation contains parameters as if it were a remote procedure call.</span></span> <span data-ttu-id="cb12d-111">Confira o exemplo abaixo.</span><span class="sxs-lookup"><span data-stu-id="cb12d-111">The following is an example.</span></span>

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="n1" type="xsd:double"/>
  <wsdl:part name="n2" type="xsd:double"/>
</wsdl:message>
```

<span data-ttu-id="cb12d-112">Definindo o estilo como <xref:System.ServiceModel.OperationFormatStyle.Document> significa que a representação do WSDL contém um único elemento que representa o documento trocado para uma operação conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="cb12d-112">Setting the style to <xref:System.ServiceModel.OperationFormatStyle.Document> means that the WSDL representation contains a single element that represents the document that is exchanged for an operation as shown in the following example.</span></span>

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="parameters" element="tns:Add"/>
</wsdl:message>
```

<span data-ttu-id="cb12d-113">O <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> propriedade determina o formato da mensagem.</span><span class="sxs-lookup"><span data-stu-id="cb12d-113">The <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> property determines the format of the message.</span></span> <span data-ttu-id="cb12d-114">Os valores possíveis são <xref:System.ServiceModel.OperationFormatUse.Literal> e <xref:System.ServiceModel.OperationFormatUse.Encoded>; o valor padrão é <xref:System.ServiceModel.OperationFormatUse.Literal>.</span><span class="sxs-lookup"><span data-stu-id="cb12d-114">Possible values are <xref:System.ServiceModel.OperationFormatUse.Literal> and <xref:System.ServiceModel.OperationFormatUse.Encoded>; the default value is <xref:System.ServiceModel.OperationFormatUse.Literal>.</span></span> <span data-ttu-id="cb12d-115">Literal significa que a mensagem é uma instância literal do esquema em WSDL, conforme mostrado no seguinte documento / Literal exemplo.</span><span class="sxs-lookup"><span data-stu-id="cb12d-115">Literal means that the message is a literal instance of the schema in the WSDL as shown in the following Document/ Literal example.</span></span>

```xml
<Add xmlns="http://Microsoft.ServiceModel.Samples">
  <n1>100</n1>
  <n2>15.99</n2>
</Add>
```

<span data-ttu-id="cb12d-116">Codificado significa que os esquemas WSDL são especificações abstratas codificadas de acordo com as regras encontradas na seção 5 do SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="cb12d-116">Encoded means that the schemas in the WSDL are abstract specifications that are encoded according to the rules found in SOAP 1.1 section 5.</span></span> <span data-ttu-id="cb12d-117">O exemplo a seguir é um exemplo RPC/codificado.</span><span class="sxs-lookup"><span data-stu-id="cb12d-117">The following is an RPC/Encoded example.</span></span>

```xml
<q1:Add xmlns:q1="http://Microsoft.ServiceModel.Samples">
  <n1 xsi:type="xsd:double" xmlns="">100</n1>
  <n2 xsi:type="xsd:double" xmlns="">15.99</n2>
</q1:Add>
```

<span data-ttu-id="cb12d-118">O WS-I Basic Profile 1.0 proíbe o uso de <xref:System.ServiceModel.OperationFormatUse.Encoded> e você deve usar apenas quando necessário pelos serviços herdados.</span><span class="sxs-lookup"><span data-stu-id="cb12d-118">The WS-I Basic Profile 1.0 prohibits the use of <xref:System.ServiceModel.OperationFormatUse.Encoded> and you should only use it when required by legacy services.</span></span> <span data-ttu-id="cb12d-119">O `Encoded` formato de mensagem só está disponível ao usar o XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="cb12d-119">The `Encoded` message format is only available when using the XmlSerializer.</span></span>

<span data-ttu-id="cb12d-120">Para que você possa ver as mensagens sendo enviadas e recebidas, este exemplo se baseia a [rastreamento e registro em log de mensagem](tracing-and-message-logging.md).</span><span class="sxs-lookup"><span data-stu-id="cb12d-120">To allow you to see the messages being sent and received, this sample is based on the [Tracing and Message Logging](tracing-and-message-logging.md).</span></span> <span data-ttu-id="cb12d-121">A configuração de serviço e o código-fonte foram modificadas para habilitar e utilizar o rastreamento e o registro de mensagem.</span><span class="sxs-lookup"><span data-stu-id="cb12d-121">The service configuration and source code have been modified to enable and utilize tracing and message logging.</span></span> <span data-ttu-id="cb12d-122">Além disso, o <xref:System.ServiceModel.WSHttpBinding> foi configurado sem segurança, portanto, as mensagens registradas podem ser exibidas em um formato não criptografado.</span><span class="sxs-lookup"><span data-stu-id="cb12d-122">In addition, the <xref:System.ServiceModel.WSHttpBinding> has been configured without security, so the logged messages can be viewed in an unencrypted format.</span></span> <span data-ttu-id="cb12d-123">Os logs de rastreamento resultante (System.ServiceModel.e2e e Message.log) devem ser exibidos usando o [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="cb12d-123">The resulting trace logs (System.ServiceModel.e2e and Message.log) should be viewed by using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="cb12d-124">Os rastreamentos são configurados para ser criado na pasta C:\LOGS.</span><span class="sxs-lookup"><span data-stu-id="cb12d-124">The traces are configured to be created in the C:\LOGS folder.</span></span> <span data-ttu-id="cb12d-125">Crie a pasta antes de executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="cb12d-125">Create the folder before running the sample.</span></span> <span data-ttu-id="cb12d-126">Para exibir o conteúdo da mensagem na ferramenta do Visualizador de rastreamento, selecione **mensagens** à esquerda e os painéis à direita da ferramenta.</span><span class="sxs-lookup"><span data-stu-id="cb12d-126">To view message contents in the Trace Viewer tool, select **Messages** in both the left and the right panes of the tool.</span></span>

<span data-ttu-id="cb12d-127">O código a seguir mostra o contrato de serviço com o <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> propriedade definida como <xref:System.ServiceModel.OperationFormatUse> e o formato do corpo da mensagem é alterado do padrão <xref:System.ServiceModel.OperationFormatStyle> para <xref:System.ServiceModel.OperationFormatStyle.Document>.</span><span class="sxs-lookup"><span data-stu-id="cb12d-127">The following code shows the service contract with the <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> property set to <xref:System.ServiceModel.OperationFormatUse> and the format of the message body changed from the default <xref:System.ServiceModel.OperationFormatStyle> to <xref:System.ServiceModel.OperationFormatStyle.Document>.</span></span>

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

<span data-ttu-id="cb12d-128">Para ver a diferença entre os diferentes <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> e <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> configurações, modificá-los no serviço, gerar novamente o cliente, executar o exemplo e examinar o arquivo c:\logs\message.logs com a ferramenta Visualizador de rastreamento de serviço.</span><span class="sxs-lookup"><span data-stu-id="cb12d-128">To see the difference between the different <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> and <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> settings, modify them in the service, regenerate the client, run the sample, and examine the c:\logs\message.logs file with the Service Trace Viewer tool.</span></span> <span data-ttu-id="cb12d-129">Também observar o impacto sobre os metadados por meio da exibição `http://localhost/ServiceModelSamples/service.svc?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="cb12d-129">Also observe the impact on the metadata by viewing `http://localhost/ServiceModelSamples/service.svc?wsdl`.</span></span> <span data-ttu-id="cb12d-130">Os metadados para os serviços normalmente é dividido em várias páginas.</span><span class="sxs-lookup"><span data-stu-id="cb12d-130">The metadata for services is typically broken up into multiple pages.</span></span> <span data-ttu-id="cb12d-131">A página principal de wsdl contém associações WSDL, mas exibir `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0` para observar as definições de mensagem.</span><span class="sxs-lookup"><span data-stu-id="cb12d-131">The main wsdl page contains the WSDL bindings, but view `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0` to observe the message definitions.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cb12d-132">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="cb12d-132">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="cb12d-133">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cb12d-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="cb12d-134">Crie um diretório c:\Logs. para mensagens de log.</span><span class="sxs-lookup"><span data-stu-id="cb12d-134">Create a C:\LOGS directory for logging messages.</span></span> <span data-ttu-id="cb12d-135">Conceder ao usuário permissões para esse diretório de gravação do serviço de rede.</span><span class="sxs-lookup"><span data-stu-id="cb12d-135">Give the user Network Service write permissions for this directory.</span></span>

3. <span data-ttu-id="cb12d-136">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cb12d-136">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="cb12d-137">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cb12d-137">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cb12d-138">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="cb12d-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cb12d-139">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="cb12d-139">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="cb12d-140">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="cb12d-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cb12d-141">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="cb12d-141">This sample is located in the following directory.</span></span>
> 
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\UseAndStyle`