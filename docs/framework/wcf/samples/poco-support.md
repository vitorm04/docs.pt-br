---
title: Suporte para POCO
ms.date: 03/30/2017
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
ms.openlocfilehash: e94f6d9576ed96613d975a66c1965820002f94ce
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183411"
---
# <a name="poco-support"></a><span data-ttu-id="ae691-102">Suporte para POCO</span><span class="sxs-lookup"><span data-stu-id="ae691-102">POCO Support</span></span>
<span data-ttu-id="ae691-103">Esta amostra demonstra o suporte à serialização para tipos não marcados; ou seja, tipos aos quais os atributos de serialização não foram aplicados, às vezes referidos como tipos de Simples Objeto CLR Antigo (POCO).</span><span class="sxs-lookup"><span data-stu-id="ae691-103">This sample demonstrates the serialization support for unmarked types; that is, types to which serialization attributes have not been applied, sometimes referred to as Plain Old CLR Object (POCO) types.</span></span> <span data-ttu-id="ae691-104">O <xref:System.Runtime.Serialization.DataContractSerializer> infere um contrato de dados para todos os tipos públicos não marcados que tenham um construtor sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="ae691-104">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract for all public unmarked types that have a parameterless constructor.</span></span> <span data-ttu-id="ae691-105">Os contratos de dados permitem que você passe dados estruturados de e para serviços.</span><span class="sxs-lookup"><span data-stu-id="ae691-105">Data contracts allow you to pass structured data to and from services.</span></span> <span data-ttu-id="ae691-106">Para obter mais informações sobre tipos não marcados, consulte [Tipos Serializable](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="ae691-106">For more information about unmarked types, see [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
 <span data-ttu-id="ae691-107">Esta amostra é baseada no [Getting Started,](../../../../docs/framework/wcf/samples/getting-started-sample.md)mas usa números complexos em vez de tipos numéricos primitivos.</span><span class="sxs-lookup"><span data-stu-id="ae691-107">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), but uses complex numbers instead of primitive numeric types.</span></span> <span data-ttu-id="ae691-108">Também é semelhante à amostra do Contrato <xref:System.Runtime.Serialization.DataContractAttribute> de <xref:System.Runtime.Serialization.DataMemberAttribute> [Dados Básicos,](../../../../docs/framework/wcf/samples/basic-data-contract.md) exceto que os e atributos não são utilizados.</span><span class="sxs-lookup"><span data-stu-id="ae691-108">It is also similar to the [Basic Data Contract](../../../../docs/framework/wcf/samples/basic-data-contract.md) sample, except that the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes are not used.</span></span>  
  
 <span data-ttu-id="ae691-109">O serviço é hospedado pelo Internet Information Services (IIS) e o cliente é um aplicativo de console (.exe).</span><span class="sxs-lookup"><span data-stu-id="ae691-109">The service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ae691-110">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="ae691-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ae691-111">A `ComplexNumber` classe é `ServiceContract`usada no .</span><span class="sxs-lookup"><span data-stu-id="ae691-111">The `ComplexNumber` class is used in the `ServiceContract`.</span></span> <span data-ttu-id="ae691-112">O `ComplexNumber` tipo não <xref:System.Runtime.Serialization.DataContractAttribute> tem <xref:System.Runtime.Serialization.DataMemberAttribute> os atributos e atributos, como mostrado no código de amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="ae691-112">The `ComplexNumber` type does not have the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes, as shown in the following sample code.</span></span> <span data-ttu-id="ae691-113">Por padrão, todas as propriedades e campos públicos são serializados.</span><span class="sxs-lookup"><span data-stu-id="ae691-113">By default, all public properties and fields are serialized.</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ae691-114">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="ae691-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ae691-115">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ae691-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="ae691-116">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ae691-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="ae691-117">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ae691-117">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ae691-118">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="ae691-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ae691-119">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="ae691-119">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="ae691-120">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="ae691-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ae691-121">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="ae691-121">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## <a name="see-also"></a><span data-ttu-id="ae691-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="ae691-122">See also</span></span>

- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>
- [<span data-ttu-id="ae691-123">Tipos serializáveis</span><span class="sxs-lookup"><span data-stu-id="ae691-123">Serializable Types</span></span>](../../../../docs/framework/wcf/feature-details/serializable-types.md)
