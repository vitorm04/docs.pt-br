---
title: 'Exemplo de XMLSerializer '
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7d134453-9a35-4202-ba77-9ca3a65babc3
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: af051dffa93aea6586adaea1e49081ddc357a210
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="xmlserializer-sample"></a><span data-ttu-id="ee90d-102">Exemplo de XMLSerializer </span><span class="sxs-lookup"><span data-stu-id="ee90d-102">XMLSerializer Sample</span></span>
<span data-ttu-id="ee90d-103">Este exemplo demonstra como serializar e desserializar os tipos que são compatíveis com o <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="ee90d-103">This sample demonstrates how to serialize and deserialize types that are compatible with the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="ee90d-104">O padrão [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] formatador de <xref:System.Runtime.Serialization.DataContractSerializer> classe.</span><span class="sxs-lookup"><span data-stu-id="ee90d-104">The default [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] formatter is the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span> <span data-ttu-id="ee90d-105">O <xref:System.Xml.Serialization.XmlSerializer> classe pode ser usada para serializar e desserializar tipos quando o <xref:System.Runtime.Serialization.DataContractSerializer> classe não pode ser usada.</span><span class="sxs-lookup"><span data-stu-id="ee90d-105">The <xref:System.Xml.Serialization.XmlSerializer> class can be used to serialize and deserialize types when the <xref:System.Runtime.Serialization.DataContractSerializer> class cannot be used.</span></span> <span data-ttu-id="ee90d-106">Isso é geralmente o caso quando um controle preciso sobre o XML é necessário – por exemplo, se uma parte dos dados deve ser um atributo XML e não um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="ee90d-106">This is often the case when precise control over the XML is required - for example, if a piece of data must be an XML attribute and not an XML element.</span></span> <span data-ttu-id="ee90d-107">Além disso, o <xref:System.Xml.Serialization.XmlSerializer> geralmente é selecionada automaticamente durante a criação de clientes para não -[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços.</span><span class="sxs-lookup"><span data-stu-id="ee90d-107">Also, the <xref:System.Xml.Serialization.XmlSerializer> often gets automatically selected when creating clients for non-[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services.</span></span>  
  
 <span data-ttu-id="ee90d-108">Neste exemplo, o cliente é um aplicativo de console (.exe) e o serviço é hospedado por serviços de informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="ee90d-108">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ee90d-109">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="ee90d-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ee90d-110">O <xref:System.ServiceModel.ServiceContractAttribute> e <xref:System.ServiceModel.XmlSerializerFormatAttribute> deve ser aplicado à interface, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ee90d-110">The <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.XmlSerializerFormatAttribute> must be applied to the interface as shown in the following sample code.</span></span>  
  
```csharp  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"), XmlSerializerFormat]  
public interface IXmlSerializerCalculator  
{  
    [OperationContract]  
    ComplexNumber Add(ComplexNumber n1, ComplexNumber n2);  
    [OperationContract]  
    ComplexNumber Subtract(ComplexNumber n1, ComplexNumber n2);  
    [OperationContract]  
    ComplexNumber Multiply(ComplexNumber n1, ComplexNumber n2);  
    [OperationContract]  
    ComplexNumber Divide(ComplexNumber n1, ComplexNumber n2);  
}  
```  
  
 <span data-ttu-id="ee90d-111">Os membros públicos de `ComplexNumber` classe são serializados por <xref:System.Xml.Serialization.XmlSerializer> como atributos XML.</span><span class="sxs-lookup"><span data-stu-id="ee90d-111">The public members of `ComplexNumber` class are serialized by <xref:System.Xml.Serialization.XmlSerializer> as XML attributes.</span></span> <span data-ttu-id="ee90d-112">O <xref:System.Runtime.Serialization.DataContractSerializer> não pode ser usado para criar esse tipo de instância XML.</span><span class="sxs-lookup"><span data-stu-id="ee90d-112">The <xref:System.Runtime.Serialization.DataContractSerializer> cannot be used to create this kind of XML instance.</span></span>  
  
```csharp  
public class ComplexNumber  
{  
    private double real;  
    private double imaginary;  
  
    [XmlAttribute]  
    public double Real  
    {  
        get { return real; }  
        set { real = value; }  
    }  
  
    [XmlAttribute]  
    public double Imaginary  
    {  
        get { return imaginary; }  
        set { imaginary = value; }  
    }  
  
    public ComplexNumber(double real, double imaginary)  
    {  
        this.Real = real;  
        this.Imaginary = imaginary;  
    }  
    public ComplexNumber()  
    {  
        this.Real = 0;  
        this.Imaginary = 0;  
    }  
  
}  
```  
  
 <span data-ttu-id="ee90d-113">A implementação do serviço calcula e retorna o resultado apropriado, aceitando e retornando valores da `ComplexNumber` tipo.</span><span class="sxs-lookup"><span data-stu-id="ee90d-113">The service implementation calculates and returns the appropriate result—accepting and returning values of the `ComplexNumber` type.</span></span>  
  
```csharp  
public class XmlSerializerCalculatorService : IXmlSerializerCalculator  
{  
    public ComplexNumber Add(ComplexNumber n1, ComplexNumber n2)  
    {  
        return new ComplexNumber(n1.Real + n2.Real, n1.Imaginary +  
                                                      n2.Imaginary);  
    }  
    …  
}  
```  
  
 <span data-ttu-id="ee90d-114">A implementação de cliente também usa números complexos.</span><span class="sxs-lookup"><span data-stu-id="ee90d-114">The client implementation also uses complex numbers.</span></span> <span data-ttu-id="ee90d-115">O contrato de serviço e os tipos de dados são definidos no arquivo de origem generatedClient.cs, que foi gerado pelo [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) de metadados de serviço.</span><span class="sxs-lookup"><span data-stu-id="ee90d-115">Both the service contract and the data types are defined in the generatedClient.cs source file, which was generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from service metadata.</span></span> <span data-ttu-id="ee90d-116">Svcutil.exe pode detectar quando um contrato não pode ser serializado pelo <xref:System.Runtime.Serialization.DataContractSerializer> e reverte para emitir `XmlSerializable` tipos nesse caso.</span><span class="sxs-lookup"><span data-stu-id="ee90d-116">Svcutil.exe can detect when a contract is not serializable by the <xref:System.Runtime.Serialization.DataContractSerializer> and reverts to emitting `XmlSerializable` types in this case.</span></span> <span data-ttu-id="ee90d-117">Se você quiser forçar o uso do <xref:System.Xml.Serialization.XmlSerializer>, você pode passar a opção de comando /serializer:XmlSerializer (use XmlSerializer) para a ferramenta Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="ee90d-117">If you want to force the use of the <xref:System.Xml.Serialization.XmlSerializer>, you can pass the /serializer:XmlSerializer (use XmlSerializer) command option to the Svcutil.exe tool.</span></span>  
  
```csharp  
// Create a client.  
XmlSerializerCalculatorClient client = new  
                         XmlSerializerCalculatorClient();  
  
// Call the Add service operation.  
ComplexNumber value1 = new ComplexNumber();  
value1.Real = 1;  
value1.Imaginary = 2;  
ComplexNumber value2 = new ComplexNumber();  
value2.Real = 3;  
value2.Imaginary = 4;  
ComplexNumber result = client.Add(value1, value2);  
Console.WriteLine("Add({0} + {1}i, {2} + {3}i) = {4} + {5}i",  
    value1.Real, value1.Imaginary, value2.Real, value2.Imaginary,   
    result.Real, result.Imaginary);  
    …  
}  
```  
  
 <span data-ttu-id="ee90d-118">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="ee90d-118">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="ee90d-119">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="ee90d-119">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(1 + 2i, 3 + 4i) = 4 + 6i  
Subtract(1 + 2i, 3 + 4i) = -2 + -2i  
Multiply(2 + 3i, 4 + 7i) = -13 + 26i  
Divide(3 + 7i, 5 + -2i) = 0.0344827586206897 + 1.41379310344828i  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ee90d-120">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="ee90d-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ee90d-121">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ee90d-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="ee90d-122">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ee90d-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="ee90d-123">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ee90d-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ee90d-124">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="ee90d-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ee90d-125">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="ee90d-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ee90d-126">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="ee90d-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ee90d-127">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="ee90d-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\Interop\XmlSerializer`  
  
## <a name="see-also"></a><span data-ttu-id="ee90d-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ee90d-128">See Also</span></span>
