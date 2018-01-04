---
title: Tipos conhecidos
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88d83720-ca38-4b2c-86a6-f149ed1d89ec
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e0359e3094b86e3433cebee7c835c7eecec16fe0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="known-types"></a><span data-ttu-id="4f3a4-102">Tipos conhecidos</span><span class="sxs-lookup"><span data-stu-id="4f3a4-102">Known Types</span></span>
<span data-ttu-id="4f3a4-103">Este exemplo demonstra como especificar informações sobre tipos derivados em um contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="4f3a4-103">This sample demonstrates how to specify information about derived types in a data contract.</span></span> <span data-ttu-id="4f3a4-104">Contratos de dados permitem que você transmita dados estruturados para e de serviços.</span><span class="sxs-lookup"><span data-stu-id="4f3a4-104">Data contracts allow you to pass structured data to and from services.</span></span> <span data-ttu-id="4f3a4-105">Em programação orientada a objeto, um tipo que herda de outro tipo pode ser usado no lugar do tipo original.</span><span class="sxs-lookup"><span data-stu-id="4f3a4-105">In object-oriented programming, a type that inherits from another type can be used in place of the original type.</span></span> <span data-ttu-id="4f3a4-106">Em programação orientada a serviços, esquemas, em vez de tipos são comunicados e, portanto, a relação entre os tipos não é preservada.</span><span class="sxs-lookup"><span data-stu-id="4f3a4-106">In service-oriented programming, schemas rather than types are communicated and therefore, the relationship between types is not preserved.</span></span> <span data-ttu-id="4f3a4-107">O <xref:System.Runtime.Serialization.KnownTypeAttribute> atributo permite que as informações sobre tipos derivados devem ser incluídos no contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="4f3a4-107">The <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute allows information about derived types to be included in the data contract.</span></span> <span data-ttu-id="4f3a4-108">Se esse mecanismo não for usado, um tipo derivado não pode ser enviado ou recebido em que um tipo base é esperado.</span><span class="sxs-lookup"><span data-stu-id="4f3a4-108">If this mechanism is not used, a derived type cannot be sent or received where a base type is expected.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4f3a4-109">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="4f3a4-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="4f3a4-110">O contrato de serviço para o serviço usa números complexos, como mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="4f3a4-110">The service contract for the service uses complex numbers, as shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="4f3a4-111">O <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute> é aplicada para o `ComplexNumber` classe para indicar quais campos de classe podem ser transmitidos entre o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="4f3a4-111">The <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> is applied to the `ComplexNumber` class to indicate which fields of the class can be passed between the client and the service.</span></span> <span data-ttu-id="4f3a4-112">Derivada `ComplexNumberWithMagnitude` classe pode ser usada no lugar de `ComplexNumber`.</span><span class="sxs-lookup"><span data-stu-id="4f3a4-112">The derived `ComplexNumberWithMagnitude` class can be used in place of `ComplexNumber`.</span></span> <span data-ttu-id="4f3a4-113">O <xref:System.Runtime.Serialization.KnownTypeAttribute> atributo no `ComplexNumber` tipo indicará isso.</span><span class="sxs-lookup"><span data-stu-id="4f3a4-113">The <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute on the `ComplexNumber` type indicates this.</span></span>  
  
```  
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
  
 <span data-ttu-id="4f3a4-114">O `ComplexNumberWithMagnitude` deriva do tipo `ComplexNumber` , mas adiciona um membro de dados adicionais, `Magnitude`.</span><span class="sxs-lookup"><span data-stu-id="4f3a4-114">The `ComplexNumberWithMagnitude` type derives from `ComplexNumber` but adds an additional data member, `Magnitude`.</span></span>  
  
```  
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
  
 <span data-ttu-id="4f3a4-115">Para demonstrar o recurso de tipos conhecidos, o serviço é implementado de tal forma que ele retorna um `ComplexNumberWithMagnitude` somente para adição e subtração.</span><span class="sxs-lookup"><span data-stu-id="4f3a4-115">To demonstrate the known types feature, the service is implemented in such a way that it returns a `ComplexNumberWithMagnitude` only for addition and subtraction.</span></span> <span data-ttu-id="4f3a4-116">(Mesmo que o contrato especifica `ComplexNumber`, isso é permitido porque o `KnownTypeAttribute` atributo).</span><span class="sxs-lookup"><span data-stu-id="4f3a4-116">(Even though the contract specifies `ComplexNumber`, this is allowed because of the `KnownTypeAttribute` attribute).</span></span> <span data-ttu-id="4f3a4-117">Multiplicação e divisão ainda retornará a base `ComplexNumber` tipo.</span><span class="sxs-lookup"><span data-stu-id="4f3a4-117">Multiplication and division still return the base `ComplexNumber` type.</span></span>  
  
```  
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
  
 <span data-ttu-id="4f3a4-118">No cliente, o contrato de serviço e o contrato de dados são definidos no generatedClient.cs de arquivo de origem, que é gerado pelo [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) de metadados de serviço.</span><span class="sxs-lookup"><span data-stu-id="4f3a4-118">On the client, both the service contract and the data contract are defined in the source file generatedClient.cs, which is generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from service metadata.</span></span> <span data-ttu-id="4f3a4-119">Porque o <xref:System.Runtime.Serialization.KnownTypeAttribute> atributo é especificado no contrato de dados do serviço, o cliente é capaz de receber ambos o `ComplexNumber` e `ComplexNumberWithMagnitude` classes ao usar o serviço.</span><span class="sxs-lookup"><span data-stu-id="4f3a4-119">Because the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute is specified in the service's data contract, the client is able to receive both the `ComplexNumber` and `ComplexNumberWithMagnitude` classes when using the service.</span></span> <span data-ttu-id="4f3a4-120">O cliente detecta se ele tem um `ComplexNumberWithMagnitude` e gerar a saída apropriada:</span><span class="sxs-lookup"><span data-stu-id="4f3a4-120">The client detects whether it got a `ComplexNumberWithMagnitude` and generate the appropriate output:</span></span>  
  
```  
// Create a client  
DataContractCalculatorClient client =   
    new DataContractCalculatorClient();  
  
// Call the Add service operation.  
ComplexNumber value1 = new ComplexNumber(); value1.real = 1; value1.imaginary = 2;  
ComplexNumber value2 = new ComplexNumber(); value2.real = 3; value2.imaginary = 4;  
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
  
 <span data-ttu-id="4f3a4-121">Quando você executar o exemplo, as solicitações e respostas da operação são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="4f3a4-121">When you run the sample, the requests and responses of the operation are displayed in the client console window.</span></span> <span data-ttu-id="4f3a4-122">Observe que uma magnitude será impressa para adição e subtração, mas não para multiplicação e divisão por causa da forma o serviço foi implementado.</span><span class="sxs-lookup"><span data-stu-id="4f3a4-122">Note that a magnitude is printed for addition and subtraction but not for multiplication and division because of the way the service was implemented.</span></span> <span data-ttu-id="4f3a4-123">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="4f3a4-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4f3a4-124">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="4f3a4-124">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="4f3a4-125">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4f3a4-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="4f3a4-126">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4f3a4-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="4f3a4-127">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4f3a4-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4f3a4-128">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="4f3a4-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4f3a4-129">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="4f3a4-129">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4f3a4-130">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="4f3a4-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4f3a4-131">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="4f3a4-131">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\KnownTypes`  
  
## <a name="see-also"></a><span data-ttu-id="4f3a4-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f3a4-132">See Also</span></span>
