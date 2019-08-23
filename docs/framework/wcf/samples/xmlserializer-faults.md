---
title: Falhas de XmlSerializer
ms.date: 03/30/2017
ms.assetid: c6b80f14-64f4-4162-ae76-71664cf42fd3
ms.openlocfilehash: c800b23ca5f3589ba3a99b88471afe5b4e5a62bf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959631"
---
# <a name="xmlserializer-faults"></a><span data-ttu-id="aa604-102">Falhas de XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="aa604-102">XmlSerializer Faults</span></span>
<span data-ttu-id="aa604-103">O <xref:System.Xml.Serialization.XmlSerializer> exemplo de contrato de falha demonstra como comunicar informações de erro de um serviço para um cliente <xref:System.Xml.Serialization.XmlSerializer>usando o.</span><span class="sxs-lookup"><span data-stu-id="aa604-103">The <xref:System.Xml.Serialization.XmlSerializer> fault contract sample demonstrates how to communicate error information from a service to a client using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="aa604-104">O exemplo é baseado na [introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md), com algum código adicional adicionado ao serviço para converter uma exceção interna em uma falha.</span><span class="sxs-lookup"><span data-stu-id="aa604-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), with some additional code added to the service to convert an internal exception to a fault.</span></span> <span data-ttu-id="aa604-105">O cliente tenta executar a divisão por zero para forçar uma condição de erro no serviço.</span><span class="sxs-lookup"><span data-stu-id="aa604-105">The client attempts to perform division by zero to force an error condition on the service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aa604-106">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="aa604-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="aa604-107">O contrato da calculadora foi modificado para incluir um <xref:System.ServiceModel.FaultContractAttribute> , conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="aa604-107">The calculator contract has been modified to include a <xref:System.ServiceModel.FaultContractAttribute> as shown in the following sample code.</span></span> <span data-ttu-id="aa604-108">Além disso, <xref:System.ServiceModel.XmlSerializerFormatAttribute> o é usado para habilitar a serialização <xref:System.Xml.Serialization.XmlSerializer>usando o.</span><span class="sxs-lookup"><span data-stu-id="aa604-108">Also, the <xref:System.ServiceModel.XmlSerializerFormatAttribute> is used to enable serialization using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="aa604-109">A <xref:System.ServiceModel.XmlSerializerFormatAttribute.SupportFaults%2A> propriedade é definida como `true` neste atributo, que instrui o serializador a usar o <xref:System.Xml.Serialization.XmlSerializer> para leitura e gravação de falhas.</span><span class="sxs-lookup"><span data-stu-id="aa604-109">The <xref:System.ServiceModel.XmlSerializerFormatAttribute.SupportFaults%2A> property is set to `true` on this attribute, which instructs the serializer to use the <xref:System.Xml.Serialization.XmlSerializer> for reading and writing faults.</span></span>  
  
```csharp
[XmlSerializerFormat(SupportFaults=true)]  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    int Add(int n1, int n2);  
  
    [OperationContract]  
    int Subtract(int n1, int n2);  
  
    [OperationContract]  
    int Multiply(int n1, int n2);  
  
    [OperationContract]  
    [FaultContract(typeof(MathFault))]  
    int Divide(int n1, int n2);  
}  
```  
  
 <span data-ttu-id="aa604-110">Ao gerar o código para o proxy do cliente, você deve aplicar o sinalizador **/UseSerializerForFaults** à [ferramenta do utilitário de metadados ServiceModel (svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="aa604-110">When generating code for the client proxy, you must apply the **/UseSerializerForFaults** flag to [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="aa604-111">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="aa604-111">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="aa604-112">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="aa604-112">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="aa604-113">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="aa604-113">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="aa604-114">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="aa604-114">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="aa604-115">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="aa604-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="aa604-116">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="aa604-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="aa604-117">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="aa604-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="aa604-118">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="aa604-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\XmlSerializerFaults`  
  
## <a name="see-also"></a><span data-ttu-id="aa604-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aa604-119">See also</span></span>

- <xref:System.ServiceModel.XmlSerializerFormatAttribute>
- <xref:System.ServiceModel.XmlSerializerFormatAttribute.SupportFaults%2A>
