---
title: Exemplo de XMLSerializer
ms.date: 03/30/2017
ms.assetid: 7d134453-9a35-4202-ba77-9ca3a65babc3
ms.openlocfilehash: ae8e4f7c9be427ec5107318443816c8ade6c5085
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044481"
---
# <a name="xmlserializer-sample"></a><span data-ttu-id="e8b2a-102">Exemplo de XMLSerializer</span><span class="sxs-lookup"><span data-stu-id="e8b2a-102">XMLSerializer Sample</span></span>
<span data-ttu-id="e8b2a-103">Este exemplo demonstra como serializar e desserializar os tipos que são compatíveis com <xref:System.Xml.Serialization.XmlSerializer>o.</span><span class="sxs-lookup"><span data-stu-id="e8b2a-103">This sample demonstrates how to serialize and deserialize types that are compatible with the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="e8b2a-104">O formatador de Windows Communication Foundation padrão (WCF) <xref:System.Runtime.Serialization.DataContractSerializer> é a classe.</span><span class="sxs-lookup"><span data-stu-id="e8b2a-104">The default Windows Communication Foundation (WCF) formatter is the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span> <span data-ttu-id="e8b2a-105">A <xref:System.Xml.Serialization.XmlSerializer> classe pode ser usada para serializar e desserializar os tipos <xref:System.Runtime.Serialization.DataContractSerializer> quando a classe não puder ser usada.</span><span class="sxs-lookup"><span data-stu-id="e8b2a-105">The <xref:System.Xml.Serialization.XmlSerializer> class can be used to serialize and deserialize types when the <xref:System.Runtime.Serialization.DataContractSerializer> class cannot be used.</span></span> <span data-ttu-id="e8b2a-106">Geralmente, esse é o caso em que o controle preciso sobre o XML é necessário, por exemplo, se uma parte dos dados deve ser um atributo XML e não um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="e8b2a-106">This is often the case when precise control over the XML is required - for example, if a piece of data must be an XML attribute and not an XML element.</span></span> <span data-ttu-id="e8b2a-107">Além disso, <xref:System.Xml.Serialization.XmlSerializer> a frequência é selecionada automaticamente ao criar clientes para serviços não WCF.</span><span class="sxs-lookup"><span data-stu-id="e8b2a-107">Also, the <xref:System.Xml.Serialization.XmlSerializer> often gets automatically selected when creating clients for non-WCF services.</span></span>  
  
 <span data-ttu-id="e8b2a-108">Neste exemplo, o cliente é um aplicativo de console (. exe) e o serviço é hospedado pelo Serviços de Informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="e8b2a-108">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e8b2a-109">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="e8b2a-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e8b2a-110">O <xref:System.ServiceModel.ServiceContractAttribute> e<xref:System.ServiceModel.XmlSerializerFormatAttribute> o devem ser aplicados à interface, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="e8b2a-110">The <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.XmlSerializerFormatAttribute> must be applied to the interface as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="e8b2a-111">Os membros públicos da `ComplexNumber` classe são serializados <xref:System.Xml.Serialization.XmlSerializer> pelo como atributos XML.</span><span class="sxs-lookup"><span data-stu-id="e8b2a-111">The public members of `ComplexNumber` class are serialized by <xref:System.Xml.Serialization.XmlSerializer> as XML attributes.</span></span> <span data-ttu-id="e8b2a-112">O <xref:System.Runtime.Serialization.DataContractSerializer> não pode ser usado para criar esse tipo de instância XML.</span><span class="sxs-lookup"><span data-stu-id="e8b2a-112">The <xref:System.Runtime.Serialization.DataContractSerializer> cannot be used to create this kind of XML instance.</span></span>  
  
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
  
 <span data-ttu-id="e8b2a-113">A implementação do serviço calcula e retorna o resultado apropriado — aceitando e retornando valores `ComplexNumber` do tipo.</span><span class="sxs-lookup"><span data-stu-id="e8b2a-113">The service implementation calculates and returns the appropriate result—accepting and returning values of the `ComplexNumber` type.</span></span>  
  
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
  
 <span data-ttu-id="e8b2a-114">A implementação do cliente também usa números complexos.</span><span class="sxs-lookup"><span data-stu-id="e8b2a-114">The client implementation also uses complex numbers.</span></span> <span data-ttu-id="e8b2a-115">O contrato de serviço e os tipos de dados são definidos no arquivo de origem generatedClient.cs, que foi gerado pela [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) de metadados de serviço.</span><span class="sxs-lookup"><span data-stu-id="e8b2a-115">Both the service contract and the data types are defined in the generatedClient.cs source file, which was generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from service metadata.</span></span> <span data-ttu-id="e8b2a-116">Svcutil. exe pode detectar quando um contrato não é serializável pelo <xref:System.Runtime.Serialization.DataContractSerializer> e reverte para `XmlSerializable` emitir tipos nesse caso.</span><span class="sxs-lookup"><span data-stu-id="e8b2a-116">Svcutil.exe can detect when a contract is not serializable by the <xref:System.Runtime.Serialization.DataContractSerializer> and reverts to emitting `XmlSerializable` types in this case.</span></span> <span data-ttu-id="e8b2a-117">Se você quiser forçar o uso do <xref:System.Xml.Serialization.XmlSerializer>, poderá passar a opção de comando/Serializer: XmlSerializer (use XmlSerializer) para a ferramenta svcutil. exe.</span><span class="sxs-lookup"><span data-stu-id="e8b2a-117">If you want to force the use of the <xref:System.Xml.Serialization.XmlSerializer>, you can pass the /serializer:XmlSerializer (use XmlSerializer) command option to the Svcutil.exe tool.</span></span>  
  
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
  
 <span data-ttu-id="e8b2a-118">Quando você executa o exemplo, as solicitações de operação e as respostas são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="e8b2a-118">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="e8b2a-119">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="e8b2a-119">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(1 + 2i, 3 + 4i) = 4 + 6i  
Subtract(1 + 2i, 3 + 4i) = -2 + -2i  
Multiply(2 + 3i, 4 + 7i) = -13 + 26i  
Divide(3 + 7i, 5 + -2i) = 0.0344827586206897 + 1.41379310344828i  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e8b2a-120">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="e8b2a-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e8b2a-121">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e8b2a-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="e8b2a-122">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e8b2a-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="e8b2a-123">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e8b2a-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e8b2a-124">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="e8b2a-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e8b2a-125">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="e8b2a-125">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="e8b2a-126">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="e8b2a-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e8b2a-127">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="e8b2a-127">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\Interop\XmlSerializer`  
