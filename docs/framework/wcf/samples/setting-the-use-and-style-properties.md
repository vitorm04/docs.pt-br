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
# <a name="setting-the-use-and-style-properties"></a><span data-ttu-id="ab95c-102">Definindo o uso e as propriedades de estilo</span><span class="sxs-lookup"><span data-stu-id="ab95c-102">Setting the Use and Style Properties</span></span>

<span data-ttu-id="ab95c-103">Esta amostra demonstra como usar as propriedades <xref:System.ServiceModel.XmlSerializerFormatAttribute> Use <xref:System.ServiceModel.DataContractFormatAttribute>e Style no e no .</span><span class="sxs-lookup"><span data-stu-id="ab95c-103">This sample demonstrates how to use the Use and Style properties on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> and the <xref:System.ServiceModel.DataContractFormatAttribute>.</span></span> <span data-ttu-id="ab95c-104">Essas propriedades afetam a formacomo as mensagens são formatadas.</span><span class="sxs-lookup"><span data-stu-id="ab95c-104">These properties affect how messages are formatted.</span></span> <span data-ttu-id="ab95c-105">Por padrão, o corpo da mensagem <xref:System.ServiceModel.OperationFormatStyle.Document>é formatado com o estilo definido como .</span><span class="sxs-lookup"><span data-stu-id="ab95c-105">By default, the message body is formatted with the style set to <xref:System.ServiceModel.OperationFormatStyle.Document>.</span></span> <span data-ttu-id="ab95c-106">Essas configurações podem ser especificadas tanto no nível do contrato de serviço quanto no nível do contrato de operação.</span><span class="sxs-lookup"><span data-stu-id="ab95c-106">These settings can be specified at either the service contract level or the operation contract level.</span></span>

> [!NOTE]
> <span data-ttu-id="ab95c-107">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="ab95c-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="ab95c-108">A <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> propriedade de estilo determina como os metadados do WSDL para o serviço são formatados.</span><span class="sxs-lookup"><span data-stu-id="ab95c-108">The <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> style property determines how the WSDL metadata for the service is formatted.</span></span> <span data-ttu-id="ab95c-109">Os valores possíveis são <xref:System.ServiceModel.OperationFormatStyle.Document>, e <xref:System.ServiceModel.OperationFormatStyle.Rpc>.</span><span class="sxs-lookup"><span data-stu-id="ab95c-109">Possible values are <xref:System.ServiceModel.OperationFormatStyle.Document>, and <xref:System.ServiceModel.OperationFormatStyle.Rpc>.</span></span> <span data-ttu-id="ab95c-110">RPC significa que a representação WSDL de mensagens trocadas por uma operação contém parâmetros como se fosse uma chamada de procedimento remoto.</span><span class="sxs-lookup"><span data-stu-id="ab95c-110">RPC means that the WSDL representation of messages exchanged for an operation contains parameters as if it were a remote procedure call.</span></span> <span data-ttu-id="ab95c-111">A seguir, é mostrado um exemplo.</span><span class="sxs-lookup"><span data-stu-id="ab95c-111">The following is an example.</span></span>

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="n1" type="xsd:double"/>
  <wsdl:part name="n2" type="xsd:double"/>
</wsdl:message>
```

<span data-ttu-id="ab95c-112">Definir o <xref:System.ServiceModel.OperationFormatStyle.Document> estilo para significa que a representação WSDL contém um único elemento que representa o documento que é trocado por uma operação, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ab95c-112">Setting the style to <xref:System.ServiceModel.OperationFormatStyle.Document> means that the WSDL representation contains a single element that represents the document that is exchanged for an operation as shown in the following example.</span></span>

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="parameters" element="tns:Add"/>
</wsdl:message>
```

<span data-ttu-id="ab95c-113">A <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> propriedade determina o formato da mensagem.</span><span class="sxs-lookup"><span data-stu-id="ab95c-113">The <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> property determines the format of the message.</span></span> <span data-ttu-id="ab95c-114">Os valores possíveis são <xref:System.ServiceModel.OperationFormatUse.Literal> e; <xref:System.ServiceModel.OperationFormatUse.Encoded> o valor <xref:System.ServiceModel.OperationFormatUse.Literal>padrão é .</span><span class="sxs-lookup"><span data-stu-id="ab95c-114">Possible values are <xref:System.ServiceModel.OperationFormatUse.Literal> and <xref:System.ServiceModel.OperationFormatUse.Encoded>; the default value is <xref:System.ServiceModel.OperationFormatUse.Literal>.</span></span> <span data-ttu-id="ab95c-115">Literal significa que a mensagem é uma instância literal do esquema no WSDL, como mostrado no exemplo documental/literal a seguir.</span><span class="sxs-lookup"><span data-stu-id="ab95c-115">Literal means that the message is a literal instance of the schema in the WSDL as shown in the following Document/ Literal example.</span></span>

```xml
<Add xmlns="http://Microsoft.ServiceModel.Samples">
  <n1>100</n1>
  <n2>15.99</n2>
</Add>
```

<span data-ttu-id="ab95c-116">Codificado significa que os esquemas no WSDL são especificações abstratas que são codificadas de acordo com as regras encontradas na seção SOAP 1.1 5.</span><span class="sxs-lookup"><span data-stu-id="ab95c-116">Encoded means that the schemas in the WSDL are abstract specifications that are encoded according to the rules found in SOAP 1.1 section 5.</span></span> <span data-ttu-id="ab95c-117">A seguir está um exemplo RPC/Codificado.</span><span class="sxs-lookup"><span data-stu-id="ab95c-117">The following is an RPC/Encoded example.</span></span>

```xml
<q1:Add xmlns:q1="http://Microsoft.ServiceModel.Samples">
  <n1 xsi:type="xsd:double" xmlns="">100</n1>
  <n2 xsi:type="xsd:double" xmlns="">15.99</n2>
</q1:Add>
```

<span data-ttu-id="ab95c-118">O Perfil Básico WS-I 1.0 <xref:System.ServiceModel.OperationFormatUse.Encoded> proíbe o uso e você só deve usá-lo quando exigido por serviços legados.</span><span class="sxs-lookup"><span data-stu-id="ab95c-118">The WS-I Basic Profile 1.0 prohibits the use of <xref:System.ServiceModel.OperationFormatUse.Encoded> and you should only use it when required by legacy services.</span></span> <span data-ttu-id="ab95c-119">O `Encoded` formato da mensagem só está disponível quando se usa o XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="ab95c-119">The `Encoded` message format is only available when using the XmlSerializer.</span></span>

<span data-ttu-id="ab95c-120">Para permitir que você veja as mensagens que estão sendo enviadas e recebidas, esta amostra é baseada no [Rastreamento e Registro de Mensagens](tracing-and-message-logging.md).</span><span class="sxs-lookup"><span data-stu-id="ab95c-120">To allow you to see the messages being sent and received, this sample is based on the [Tracing and Message Logging](tracing-and-message-logging.md).</span></span> <span data-ttu-id="ab95c-121">A configuração do serviço e o código-fonte foram modificados para habilitar e utilizar o rastreamento e o registro de mensagens.</span><span class="sxs-lookup"><span data-stu-id="ab95c-121">The service configuration and source code have been modified to enable and utilize tracing and message logging.</span></span> <span data-ttu-id="ab95c-122">Além disso, <xref:System.ServiceModel.WSHttpBinding> o foi configurado sem segurança, para que as mensagens registradas possam ser visualizadas em um formato não criptografado.</span><span class="sxs-lookup"><span data-stu-id="ab95c-122">In addition, the <xref:System.ServiceModel.WSHttpBinding> has been configured without security, so the logged messages can be viewed in an unencrypted format.</span></span> <span data-ttu-id="ab95c-123">Os registros de rastreamento resultantes (System.ServiceModel.e2e e Message.log) devem ser visualizados usando a [Ferramenta de Visualização de Rastreamento de Serviço (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="ab95c-123">The resulting trace logs (System.ServiceModel.e2e and Message.log) should be viewed by using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="ab95c-124">Os traços estão configurados para serem criados na pasta C:\LOGS.</span><span class="sxs-lookup"><span data-stu-id="ab95c-124">The traces are configured to be created in the C:\LOGS folder.</span></span> <span data-ttu-id="ab95c-125">Crie a pasta antes de executar a amostra.</span><span class="sxs-lookup"><span data-stu-id="ab95c-125">Create the folder before running the sample.</span></span> <span data-ttu-id="ab95c-126">Para exibir o conteúdo da mensagem na ferramenta Trace Viewer, selecione **Mensagens** nos painéis esquerdo e direito da ferramenta.</span><span class="sxs-lookup"><span data-stu-id="ab95c-126">To view message contents in the Trace Viewer tool, select **Messages** in both the left and the right panes of the tool.</span></span>

<span data-ttu-id="ab95c-127">O código a seguir mostra <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> o <xref:System.ServiceModel.OperationFormatUse> contrato de serviço com a propriedade <xref:System.ServiceModel.OperationFormatStyle> <xref:System.ServiceModel.OperationFormatStyle.Document>definida e o formato do corpo de mensagem alterado do padrão para .</span><span class="sxs-lookup"><span data-stu-id="ab95c-127">The following code shows the service contract with the <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> property set to <xref:System.ServiceModel.OperationFormatUse> and the format of the message body changed from the default <xref:System.ServiceModel.OperationFormatStyle> to <xref:System.ServiceModel.OperationFormatStyle.Document>.</span></span>

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

<span data-ttu-id="ab95c-128">Para ver a diferença <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> entre as diferentes e as configurações, modifique-as no serviço, regenere o cliente, execute a amostra e examine o arquivo c:\logs\message.logs com a ferramenta Visualizador de rastreamento de serviço.</span><span class="sxs-lookup"><span data-stu-id="ab95c-128">To see the difference between the different <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> and <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> settings, modify them in the service, regenerate the client, run the sample, and examine the c:\logs\message.logs file with the Service Trace Viewer tool.</span></span> <span data-ttu-id="ab95c-129">Observe também o impacto nos `http://localhost/ServiceModelSamples/service.svc?wsdl`metadados visualizando .</span><span class="sxs-lookup"><span data-stu-id="ab95c-129">Also observe the impact on the metadata by viewing `http://localhost/ServiceModelSamples/service.svc?wsdl`.</span></span> <span data-ttu-id="ab95c-130">Os metadados para serviços são normalmente divididos em várias páginas.</span><span class="sxs-lookup"><span data-stu-id="ab95c-130">The metadata for services is typically broken up into multiple pages.</span></span> <span data-ttu-id="ab95c-131">A página principal do wsdl contém as ligações `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0` WSDL, mas é vista para observar as definições da mensagem.</span><span class="sxs-lookup"><span data-stu-id="ab95c-131">The main wsdl page contains the WSDL bindings, but view `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0` to observe the message definitions.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ab95c-132">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="ab95c-132">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="ab95c-133">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ab95c-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="ab95c-134">Crie um diretório C:\LOGS para registrar mensagens.</span><span class="sxs-lookup"><span data-stu-id="ab95c-134">Create a C:\LOGS directory for logging messages.</span></span> <span data-ttu-id="ab95c-135">Dê ao usuário permissões de gravação do Serviço de Rede para este diretório.</span><span class="sxs-lookup"><span data-stu-id="ab95c-135">Give the user Network Service write permissions for this directory.</span></span>

3. <span data-ttu-id="ab95c-136">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ab95c-136">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="ab95c-137">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ab95c-137">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ab95c-138">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="ab95c-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ab95c-139">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="ab95c-139">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="ab95c-140">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="ab95c-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ab95c-141">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="ab95c-141">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\UseAndStyle`
