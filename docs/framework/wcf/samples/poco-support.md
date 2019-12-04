---
title: Suporte para POCO
ms.date: 03/30/2017
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
ms.openlocfilehash: 2962fa8a9eb824bbfbbb2f1e9347f8988b50ddcd
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716540"
---
# <a name="poco-support"></a><span data-ttu-id="1afdd-102">Suporte para POCO</span><span class="sxs-lookup"><span data-stu-id="1afdd-102">POCO Support</span></span>
<span data-ttu-id="1afdd-103">Este exemplo demonstra o suporte de serialização para tipos desmarcados; ou seja, tipos para os quais os atributos de serialização não foram aplicados, às vezes chamados de tipos POCO (objeto CLR antigo).</span><span class="sxs-lookup"><span data-stu-id="1afdd-103">This sample demonstrates the serialization support for unmarked types; that is, types to which serialization attributes have not been applied, sometimes referred to as Plain Old CLR Object (POCO) types.</span></span> <span data-ttu-id="1afdd-104">O <xref:System.Runtime.Serialization.DataContractSerializer> infere um contrato de dados para todos os tipos públicos não marcados que têm um construtor sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="1afdd-104">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract for all public unmarked types that have a parameterless constructor.</span></span> <span data-ttu-id="1afdd-105">Os contratos de dados permitem que você transmita dados estruturados de e para serviços.</span><span class="sxs-lookup"><span data-stu-id="1afdd-105">Data contracts allow you to pass structured data to and from services.</span></span> <span data-ttu-id="1afdd-106">Para obter mais informações sobre tipos desmarcados, consulte [tipos serializáveis](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="1afdd-106">For more information about unmarked types, see [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
 <span data-ttu-id="1afdd-107">Este exemplo é baseado na [introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md), mas usa números complexos em vez de tipos numéricos primitivos.</span><span class="sxs-lookup"><span data-stu-id="1afdd-107">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), but uses complex numbers instead of primitive numeric types.</span></span> <span data-ttu-id="1afdd-108">Ele também é semelhante ao exemplo de [contrato de dados básico](../../../../docs/framework/wcf/samples/basic-data-contract.md) , exceto pelo fato de que os atributos <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute> não são usados.</span><span class="sxs-lookup"><span data-stu-id="1afdd-108">It is also similar to the [Basic Data Contract](../../../../docs/framework/wcf/samples/basic-data-contract.md) sample, except that the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes are not used.</span></span>  
  
 <span data-ttu-id="1afdd-109">O serviço é hospedado pelo Serviços de Informações da Internet (IIS) e o cliente é um aplicativo de console (. exe).</span><span class="sxs-lookup"><span data-stu-id="1afdd-109">The service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1afdd-110">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="1afdd-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="1afdd-111">A classe `ComplexNumber` é usada na `ServiceContract`.</span><span class="sxs-lookup"><span data-stu-id="1afdd-111">The `ComplexNumber` class is used in the `ServiceContract`.</span></span> <span data-ttu-id="1afdd-112">O tipo de `ComplexNumber` não tem os atributos <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute>, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="1afdd-112">The `ComplexNumber` type does not have the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes, as shown in the following sample code.</span></span> <span data-ttu-id="1afdd-113">Por padrão, todas as propriedades públicas e campos são serializados.</span><span class="sxs-lookup"><span data-stu-id="1afdd-113">By default, all public properties and fields are serialized.</span></span>  
  
```csharp
public class ComplexNumber  
{  
    public double Real;  
    public double Imaginary;  
    public ComplexNumber()  
    {  
        Real = double.MinValue;  
        Imaginary = double.MinValue;  
    }  
    public ComplexNumber(double real, double imaginary)  
    {  
        this.Real = real;  
        this.Imaginary = imaginary;  
    }  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1afdd-114">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="1afdd-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="1afdd-115">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1afdd-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="1afdd-116">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1afdd-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="1afdd-117">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1afdd-117">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1afdd-118">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="1afdd-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1afdd-119">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="1afdd-119">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="1afdd-120">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="1afdd-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1afdd-121">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="1afdd-121">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## <a name="see-also"></a><span data-ttu-id="1afdd-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1afdd-122">See also</span></span>

- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>
- [<span data-ttu-id="1afdd-123">Tipos serializáveis</span><span class="sxs-lookup"><span data-stu-id="1afdd-123">Serializable Types</span></span>](../../../../docs/framework/wcf/feature-details/serializable-types.md)
