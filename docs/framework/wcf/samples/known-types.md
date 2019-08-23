---
title: Tipos conhecidos
ms.date: 03/30/2017
ms.assetid: 88d83720-ca38-4b2c-86a6-f149ed1d89ec
ms.openlocfilehash: ebcf5e4a1e6d587a3047e3faffb03847715f7a85
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952867"
---
# <a name="known-types"></a><span data-ttu-id="93646-102">Tipos conhecidos</span><span class="sxs-lookup"><span data-stu-id="93646-102">Known Types</span></span>
<span data-ttu-id="93646-103">Este exemplo demonstra como especificar informações sobre tipos derivados em um contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="93646-103">This sample demonstrates how to specify information about derived types in a data contract.</span></span> <span data-ttu-id="93646-104">Os contratos de dados permitem que você transmita dados estruturados de e para serviços.</span><span class="sxs-lookup"><span data-stu-id="93646-104">Data contracts allow you to pass structured data to and from services.</span></span> <span data-ttu-id="93646-105">Na programação orientada a objeto, um tipo que herda de outro tipo pode ser usado no lugar do tipo original.</span><span class="sxs-lookup"><span data-stu-id="93646-105">In object-oriented programming, a type that inherits from another type can be used in place of the original type.</span></span> <span data-ttu-id="93646-106">Na programação orientada a serviços, os esquemas em vez dos tipos são comunicados e, portanto, a relação entre os tipos não é preservada.</span><span class="sxs-lookup"><span data-stu-id="93646-106">In service-oriented programming, schemas rather than types are communicated and therefore, the relationship between types is not preserved.</span></span> <span data-ttu-id="93646-107">O <xref:System.Runtime.Serialization.KnownTypeAttribute> atributo permite que informações sobre tipos derivados sejam incluídas no contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="93646-107">The <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute allows information about derived types to be included in the data contract.</span></span> <span data-ttu-id="93646-108">Se esse mecanismo não for usado, um tipo derivado não poderá ser enviado ou recebido onde um tipo base for esperado.</span><span class="sxs-lookup"><span data-stu-id="93646-108">If this mechanism is not used, a derived type cannot be sent or received where a base type is expected.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="93646-109">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="93646-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="93646-110">O contrato de serviço para o serviço usa números complexos, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="93646-110">The service contract for the service uses complex numbers, as shown in the following sample code.</span></span>  
  
```csharp
// Define a service contract.  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
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
  
 <span data-ttu-id="93646-111">O <xref:System.Runtime.Serialization.DataContractAttribute> `ComplexNumber` e <xref:System.Runtime.Serialization.DataMemberAttribute> é aplicado à classe para indicar quais campos da classe podem ser passados entre o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="93646-111">The <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> is applied to the `ComplexNumber` class to indicate which fields of the class can be passed between the client and the service.</span></span> <span data-ttu-id="93646-112">A classe `ComplexNumberWithMagnitude` derivada pode ser usada no lugar de `ComplexNumber`.</span><span class="sxs-lookup"><span data-stu-id="93646-112">The derived `ComplexNumberWithMagnitude` class can be used in place of `ComplexNumber`.</span></span> <span data-ttu-id="93646-113">O <xref:System.Runtime.Serialization.KnownTypeAttribute> atributo`ComplexNumber` no tipo indica isso.</span><span class="sxs-lookup"><span data-stu-id="93646-113">The <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute on the `ComplexNumber` type indicates this.</span></span>  
  
```csharp
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
[KnownType(typeof(ComplexNumberWithMagnitude))]  
public class ComplexNumber  
{  
    [DataMember]  
    public double Real = 0.0D;  
    [DataMember]  
    public double Imaginary = 0.0D;  
  
    public ComplexNumber(double real, double imaginary)  
    {  
        this.Real = real;  
        this.Imaginary = imaginary;  
    }  
}  
```  
  
 <span data-ttu-id="93646-114">O `ComplexNumberWithMagnitude` tipo deriva de `ComplexNumber` , mas adiciona um membro de dados adicional `Magnitude`,.</span><span class="sxs-lookup"><span data-stu-id="93646-114">The `ComplexNumberWithMagnitude` type derives from `ComplexNumber` but adds an additional data member, `Magnitude`.</span></span>  
  
```csharp
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public class ComplexNumberWithMagnitude : ComplexNumber  
{  
    public ComplexNumberWithMagnitude(double real, double imaginary) :  
        base(real, imaginary) { }  
  
    [DataMember]  
    public double Magnitude  
    {  
        get { return Math.Sqrt(Imaginary*Imaginary  + Real*Real); }  
        set { throw new NotImplementedException(); }  
    }  
}  
```  
  
 <span data-ttu-id="93646-115">Para demonstrar o recurso de tipos conhecidos, o serviço é implementado de forma que ele retorne `ComplexNumberWithMagnitude` apenas para adição e subtração.</span><span class="sxs-lookup"><span data-stu-id="93646-115">To demonstrate the known types feature, the service is implemented in such a way that it returns a `ComplexNumberWithMagnitude` only for addition and subtraction.</span></span> <span data-ttu-id="93646-116">(Embora o contrato especifique `ComplexNumber`, isso é permitido por causa `KnownTypeAttribute` do atributo).</span><span class="sxs-lookup"><span data-stu-id="93646-116">(Even though the contract specifies `ComplexNumber`, this is allowed because of the `KnownTypeAttribute` attribute).</span></span> <span data-ttu-id="93646-117">Multiplicação e divisão ainda retornam o `ComplexNumber` tipo base.</span><span class="sxs-lookup"><span data-stu-id="93646-117">Multiplication and division still return the base `ComplexNumber` type.</span></span>  
  
```csharp
public class DataContractCalculatorService : IDataContractCalculator  
{  
    public ComplexNumber Add(ComplexNumber n1, ComplexNumber n2)  
    {  
        //Return the derived type.  
        return new ComplexNumberWithMagnitude(n1.Real + n2.Real,  
                                      n1.Imaginary + n2.Imaginary);  
    }  
  
    public ComplexNumber Subtract(ComplexNumber n1, ComplexNumber n2)  
    {  
        //Return the derived type.  
        return new ComplexNumberWithMagnitude(n1.Real - n2.Real,   
                                 n1.Imaginary - n2.Imaginary);  
    }  
  
    public ComplexNumber Multiply(ComplexNumber n1, ComplexNumber n2)  
    {  
        double real1 = n1.Real * n2.Real;  
        double imaginary1 = n1.Real * n2.Imaginary;  
        double imaginary2 = n2.Real * n1.Imaginary;  
        double real2 = n1.Imaginary * n2.Imaginary * -1;  
        //Return the base type.  
        return new ComplexNumber(real1 + real2, imaginary1 +   
                                                  imaginary2);  
    }  
  
    public ComplexNumber Divide(ComplexNumber n1, ComplexNumber n2)  
    {  
        ComplexNumber conjugate = new ComplexNumber(n2.Real,   
                                     -1*n2.Imaginary);  
        ComplexNumber numerator = Multiply(n1, conjugate);  
        ComplexNumber denominator = Multiply(n2, conjugate);  
        //Return the base type.  
        return new ComplexNumber(numerator.Real / denominator.Real,  
                                             numerator.Imaginary);  
    }  
}  
```  
  
 <span data-ttu-id="93646-118">No cliente, o contrato de serviço e o contrato de dados são definidos no arquivo de origem generatedClient.cs, que é gerado pela [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) a partir de metadados de serviço.</span><span class="sxs-lookup"><span data-stu-id="93646-118">On the client, both the service contract and the data contract are defined in the source file generatedClient.cs, which is generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from service metadata.</span></span> <span data-ttu-id="93646-119">Como o <xref:System.Runtime.Serialization.KnownTypeAttribute> atributo é especificado no contrato de dados do serviço, o cliente é capaz de receber as `ComplexNumber` classes e `ComplexNumberWithMagnitude` ao usar o serviço.</span><span class="sxs-lookup"><span data-stu-id="93646-119">Because the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute is specified in the service's data contract, the client is able to receive both the `ComplexNumber` and `ComplexNumberWithMagnitude` classes when using the service.</span></span> <span data-ttu-id="93646-120">O cliente detecta se ele tem um `ComplexNumberWithMagnitude` e gera a saída apropriada:</span><span class="sxs-lookup"><span data-stu-id="93646-120">The client detects whether it got a `ComplexNumberWithMagnitude` and generate the appropriate output:</span></span>  
  
```csharp
// Create a client  
DataContractCalculatorClient client =   
    new DataContractCalculatorClient();  
  
// Call the Add service operation.  
ComplexNumber value1 = new ComplexNumber() { real = 1, imaginary = 2 };  
ComplexNumber value2 = new ComplexNumber() { real = 3, imaginary = 4 };  
ComplexNumber result = client.Add(value1, value2);  
Console.WriteLine("Add({0} + {1}i, {2} + {3}i) = {4} + {5}i",  
    value1.real, value1.imaginary, value2.real, value2.imaginary,  
    result.real, result.imaginary);  
if (result is ComplexNumberWithMagnitude)  
{  
    Console.WriteLine("Magnitude: {0}",   
        ((ComplexNumberWithMagnitude)result).Magnitude);  
}  
else  
{  
    Console.WriteLine("No magnitude was sent from the service");  
}  
```  
  
 <span data-ttu-id="93646-121">Quando você executa o exemplo, as solicitações e respostas da operação são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="93646-121">When you run the sample, the requests and responses of the operation are displayed in the client console window.</span></span> <span data-ttu-id="93646-122">Observe que uma magnitude é impressa para adição e subtração, mas não para multiplicação e divisão devido à maneira como o serviço foi implementado.</span><span class="sxs-lookup"><span data-stu-id="93646-122">Note that a magnitude is printed for addition and subtraction but not for multiplication and division because of the way the service was implemented.</span></span> <span data-ttu-id="93646-123">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="93646-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(1 + 2i, 3 + 4i) = 4 + 6i  
Magnitude: 7.21110255092798  
Subtract(1 + 2i, 3 + 4i) = -2 + -2i  
Magnitude: 2.82842712474619  
Multiply(2 + 3i, 4 + 7i) = -13 + 26i  
No magnitude was sent from the service  
Divide(3 + 7i, 5 + -2i) = 0.0344827586206897 + 41i  
No magnitude was sent from the service  
  
    Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="93646-124">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="93646-124">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="93646-125">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="93646-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="93646-126">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="93646-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="93646-127">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="93646-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="93646-128">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="93646-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="93646-129">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="93646-129">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="93646-130">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="93646-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="93646-131">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="93646-131">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\KnownTypes`  
