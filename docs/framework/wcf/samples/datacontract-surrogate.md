---
title: Alternativa de DataContract
ms.date: 03/30/2017
ms.assetid: b0188f3c-00a9-4cf0-a887-a2284c8fb014
ms.openlocfilehash: 7ef78c4361c055d7be35c03a3c8717e86aceddab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183831"
---
# <a name="datacontract-surrogate"></a><span data-ttu-id="b94dc-102">Alternativa de DataContract</span><span class="sxs-lookup"><span data-stu-id="b94dc-102">DataContract Surrogate</span></span>
<span data-ttu-id="b94dc-103">Esta amostra demonstra como processos como serialização, desserialização, exportação de esquemas e importação de esquemas podem ser personalizados usando uma classe de substituto de contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="b94dc-103">This sample demonstrates how processes like serialization, deserialization, schema export, and schema import can be customized using a data contract surrogate class.</span></span> <span data-ttu-id="b94dc-104">Esta amostra mostra como usar um substituto em um cenário de cliente e servidor onde os dados são serializados e transmitidos entre um cliente e serviço da Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b94dc-104">This sample shows how to use a surrogate in a client and server scenario where data is serialized and transmitted between a Windows Communication Foundation (WCF) client and service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b94dc-105">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="b94dc-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="b94dc-106">A amostra utiliza o seguinte contrato de serviço:</span><span class="sxs-lookup"><span data-stu-id="b94dc-106">The sample uses the following service contract:</span></span>  
  
```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
[AllowNonSerializableTypes]  
public interface IPersonnelDataService  
{  
    [OperationContract]  
    void AddEmployee(Employee employee);  
  
    [OperationContract]  
    Employee GetEmployee(string name);  
}  
```  
  
 <span data-ttu-id="b94dc-107">A `AddEmployee` operação permite que os usuários adicionem dados sobre novos funcionários e a `GetEmployee` operação suporta a busca por funcionários com base no nome.</span><span class="sxs-lookup"><span data-stu-id="b94dc-107">The `AddEmployee` operation allows users to add data about new employees and the `GetEmployee` operation supports search for employees based on name.</span></span>  
  
 <span data-ttu-id="b94dc-108">Essas operações utilizam o seguinte tipo de dados:</span><span class="sxs-lookup"><span data-stu-id="b94dc-108">These operations use the following data type:</span></span>  
  
```csharp
[DataContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
class Employee  
{  
    [DataMember]  
    public DateTime dateHired;  
  
    [DataMember]  
    public Decimal salary;  
  
    [DataMember]  
    public Person person;  
}  
```  
  
 <span data-ttu-id="b94dc-109">No `Employee` tipo, `Person` a classe (mostrada no código de amostra <xref:System.Runtime.Serialization.DataContractSerializer> a seguir) não pode ser serializada pelo porque não é uma classe de contrato de dados válida.</span><span class="sxs-lookup"><span data-stu-id="b94dc-109">In the `Employee` type, the `Person` class (shown in the following sample code) cannot be serialized by the <xref:System.Runtime.Serialization.DataContractSerializer> because it is not a valid data contract class.</span></span>  
  
```csharp
public class Person  
{  
    public string firstName;  
  
    public string lastName;  
  
    public int age;  
  
    public Person() { }  
}  
```  
  
 <span data-ttu-id="b94dc-110">Você pode <xref:System.Runtime.Serialization.DataContractAttribute> aplicar o `Person` atributo à classe, mas isso nem sempre é possível.</span><span class="sxs-lookup"><span data-stu-id="b94dc-110">You can apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the `Person` class, but this is not always possible.</span></span> <span data-ttu-id="b94dc-111">Por exemplo, `Person` a classe pode ser definida em um conjunto separado sobre o qual você não tem controle.</span><span class="sxs-lookup"><span data-stu-id="b94dc-111">For example, the `Person` class can be defined in a separate assembly over which you have no control.</span></span>  
  
 <span data-ttu-id="b94dc-112">Dada essa restrição, uma `Person` maneira de serializar a classe é <xref:System.Runtime.Serialization.DataContractAttribute> substituí-la por outra classe que é marcada e copiar sobre os dados necessários para a nova classe.</span><span class="sxs-lookup"><span data-stu-id="b94dc-112">Given this restriction, one way to serialize the `Person` class is to substitute it with another class that is marked with <xref:System.Runtime.Serialization.DataContractAttribute> and copy over necessary data to the new class.</span></span> <span data-ttu-id="b94dc-113">O objetivo é `Person` fazer com que a <xref:System.Runtime.Serialization.DataContractSerializer>classe apareça como um Contrato de Dados para o .</span><span class="sxs-lookup"><span data-stu-id="b94dc-113">The objective is to make the `Person` class appear as a DataContract to the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="b94dc-114">Observe que esta é uma maneira de serializar classes de contratos não-dados.</span><span class="sxs-lookup"><span data-stu-id="b94dc-114">Note that this is one way to serialize non-data contract classes.</span></span>  
  
 <span data-ttu-id="b94dc-115">A amostra logicamente `Person` substitui a classe `PersonSurrogated`por uma classe diferente chamada .</span><span class="sxs-lookup"><span data-stu-id="b94dc-115">The sample logically replaces the `Person` class with a different class named `PersonSurrogated`.</span></span>  
  
```csharp
[DataContract(Name="Person", Namespace = "http://Microsoft.ServiceModel.Samples")]  
public class PersonSurrogated  
{  
    [DataMember]  
    public string FirstName;  
  
    [DataMember]  
    public string LastName;  
  
    [DataMember]  
    public int Age;  
}  
```  
  
 <span data-ttu-id="b94dc-116">O substituto do contrato de dados é usado para conseguir essa substituição.</span><span class="sxs-lookup"><span data-stu-id="b94dc-116">The data contract surrogate is used to achieve this replacement.</span></span> <span data-ttu-id="b94dc-117">Um substituto de contrato de <xref:System.Runtime.Serialization.IDataContractSurrogate>dados é uma classe que implementa .</span><span class="sxs-lookup"><span data-stu-id="b94dc-117">A data contract surrogate is a class that implements <xref:System.Runtime.Serialization.IDataContractSurrogate>.</span></span> <span data-ttu-id="b94dc-118">Nesta amostra, `AllowNonSerializableTypesSurrogate` a classe implementa essa interface.</span><span class="sxs-lookup"><span data-stu-id="b94dc-118">In this sample, the `AllowNonSerializableTypesSurrogate` class implements this interface.</span></span>  
  
 <span data-ttu-id="b94dc-119">Na implementação da interface, a primeira tarefa `Person` `PersonSurrogated`é estabelecer um mapeamento de tipo a partir de .</span><span class="sxs-lookup"><span data-stu-id="b94dc-119">In the interface implementation, the first task is to establish a type mapping from `Person` to `PersonSurrogated`.</span></span> <span data-ttu-id="b94dc-120">Isso é usado tanto no tempo de serialização quanto no tempo de exportação do esquema.</span><span class="sxs-lookup"><span data-stu-id="b94dc-120">This is used both at serialization time as well as at schema export time.</span></span> <span data-ttu-id="b94dc-121">Esse mapeamento é conseguido <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> com a implementação do método.</span><span class="sxs-lookup"><span data-stu-id="b94dc-121">This mapping is achieved by implementing the <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> method.</span></span>  
  
```csharp
public Type GetDataContractType(Type type)  
{  
    if (typeof(Person).IsAssignableFrom(type))  
    {  
        return typeof(PersonSurrogated);  
    }  
    return type;  
}  
```  
  
 <span data-ttu-id="b94dc-122">O <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> método `Person` mapeia uma instância para uma `PersonSurrogated` instância durante a serialização, conforme mostrado no código de amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="b94dc-122">The <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> method maps a `Person` instance to a `PersonSurrogated` instance during serialization, as shown in the following sample code.</span></span>  
  
```csharp
public object GetObjectToSerialize(object obj, Type targetType)  
{  
    if (obj is Person)  
    {  
        Person person = (Person)obj;  
        PersonSurrogated personSurrogated = new PersonSurrogated();  
        personSurrogated.FirstName = person.firstName;  
        personSurrogated.LastName = person.lastName;  
        personSurrogated.Age = person.age;  
        return personSurrogated;  
    }  
    return obj;  
}  
```  
  
 <span data-ttu-id="b94dc-123">O <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> método fornece o mapeamento reverso para desserialização, como mostrado no código de amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="b94dc-123">The <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> method provides the reverse mapping for deserialization, as shown in the following sample code.</span></span>  
  
```csharp
public object GetDeserializedObject(object obj,
Type targetType)  
{  
    if (obj is PersonSurrogated)  
    {  
        PersonSurrogated personSurrogated = (PersonSurrogated)obj;  
        Person person = new Person();  
        person.firstName = personSurrogated.FirstName;  
        person.lastName = personSurrogated.LastName;  
        person.age = personSurrogated.Age;  
        return person;  
    }  
    return obj;  
}  
```  
  
 <span data-ttu-id="b94dc-124">Para mapear `PersonSurrogated` o contrato de `Person` dados para a classe existente durante <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> a importação do esquema, a amostra implementa o método, conforme mostrado no código amostral a seguir.</span><span class="sxs-lookup"><span data-stu-id="b94dc-124">To map the `PersonSurrogated` data contract to the existing `Person` class during schema import, the sample implements the <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> method, as shown in the following sample code.</span></span>  
  
```csharp
public Type GetReferencedTypeOnImport(string typeName,
               string typeNamespace, object customData)  
{  
if (  
typeNamespace.Equals("http://schemas.datacontract.org/2004/07/DCSurrogateSample")  
)  
    {  
         if (typeName.Equals("PersonSurrogated"))  
        {  
             return typeof(Person);  
        }  
     }  
     return null;  
}  
```  
  
 <span data-ttu-id="b94dc-125">O código de amostra a <xref:System.Runtime.Serialization.IDataContractSurrogate> seguir completa a implementação da interface.</span><span class="sxs-lookup"><span data-stu-id="b94dc-125">The following sample code completes the implementation of the <xref:System.Runtime.Serialization.IDataContractSurrogate> interface.</span></span>  
  
```csharp
public System.CodeDom.CodeTypeDeclaration ProcessImportedType(  
          System.CodeDom.CodeTypeDeclaration typeDeclaration,
          System.CodeDom.CodeCompileUnit compileUnit)  
{  
    return typeDeclaration;  
}  
public object GetCustomDataToExport(Type clrType,
                               Type dataContractType)  
{  
    return null;  
}  
  
public object GetCustomDataToExport(  
System.Reflection.MemberInfo memberInfo, Type dataContractType)  
{  
    return null;  
}  
public void GetKnownCustomDataTypes(  
        KnownTypeCollection customDataTypes)  
{  
    // It does not matter what we do here.  
    throw new NotImplementedException();  
}  
```  
  
 <span data-ttu-id="b94dc-126">Nesta amostra, o substituto é habilitado no `AllowNonSerializableTypesAttribute`ServiceModel por um atributo chamado .</span><span class="sxs-lookup"><span data-stu-id="b94dc-126">In this sample, the surrogate is enabled in ServiceModel by an attribute called `AllowNonSerializableTypesAttribute`.</span></span> <span data-ttu-id="b94dc-127">Os desenvolvedores precisariam aplicar esse atributo em `IPersonnelDataService` seu contrato de serviço, conforme mostrado no contrato de serviço acima.</span><span class="sxs-lookup"><span data-stu-id="b94dc-127">Developers would need to apply this attribute on their service contract as shown on the `IPersonnelDataService` service contract above.</span></span> <span data-ttu-id="b94dc-128">Esse atributo `IContractBehavior` implementa e configura o `ApplyClientBehavior` `ApplyDispatchBehavior` substituto em operações em seus métodos e métodos.</span><span class="sxs-lookup"><span data-stu-id="b94dc-128">This attribute implements `IContractBehavior` and sets up the surrogate on operations in its `ApplyClientBehavior` and `ApplyDispatchBehavior` methods.</span></span>  
  
 <span data-ttu-id="b94dc-129">O atributo não é necessário neste caso - é usado para fins de demonstração nesta amostra.</span><span class="sxs-lookup"><span data-stu-id="b94dc-129">The attribute is not necessary in this case - it is used for demonstration purposes in this sample.</span></span> <span data-ttu-id="b94dc-130">Os usuários podem, alternativamente, habilitar `IContractBehavior` `IEndpointBehavior` um `IOperationBehavior` substituto adicionando manualmente um semelhante, ou usando código ou usando configuração.</span><span class="sxs-lookup"><span data-stu-id="b94dc-130">Users can alternatively enable a surrogate by manually adding a similar `IContractBehavior`, `IEndpointBehavior` or `IOperationBehavior` using code or using configuration.</span></span>  
  
 <span data-ttu-id="b94dc-131">A `IContractBehavior` implementação procura operações que utilizem DataContract verificando se possuem um `DataContractSerializerOperationBehavior` registro.</span><span class="sxs-lookup"><span data-stu-id="b94dc-131">The `IContractBehavior` implementation looks for operations that use DataContract by checking if they have a `DataContractSerializerOperationBehavior` registered.</span></span> <span data-ttu-id="b94dc-132">Se o fizerem, `DataContractSurrogate` isso define a propriedade sobre esse comportamento.</span><span class="sxs-lookup"><span data-stu-id="b94dc-132">If they do, it sets the `DataContractSurrogate` property on that behavior.</span></span> <span data-ttu-id="b94dc-133">O seguinte código de amostra mostra como isso é feito.</span><span class="sxs-lookup"><span data-stu-id="b94dc-133">The following sample code shows how this is done.</span></span> <span data-ttu-id="b94dc-134">A definição do substituto sobre este comportamento de operação permite que ele seja serializador e desserializador.</span><span class="sxs-lookup"><span data-stu-id="b94dc-134">Setting the surrogate on this operation behavior enables it for serialization and deserialization.</span></span>  
  
```csharp
public void ApplyClientBehavior(ContractDescription description, ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.ClientRuntime proxy)  
{  
    foreach (OperationDescription opDesc in description.Operations)  
    {  
        ApplyDataContractSurrogate(opDesc);  
    }  
}  
  
public void ApplyDispatchBehavior(ContractDescription description, ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.DispatchRuntime dispatch)  
{  
    foreach (OperationDescription opDesc in description.Operations)  
    {  
        ApplyDataContractSurrogate(opDesc);  
    }  
}  
  
private static void ApplyDataContractSurrogate(OperationDescription description)  
{  
    DataContractSerializerOperationBehavior dcsOperationBehavior = description.Behaviors.Find<DataContractSerializerOperationBehavior>();  
    if (dcsOperationBehavior != null)  
    {  
        if (dcsOperationBehavior.DataContractSurrogate == null)  
            dcsOperationBehavior.DataContractSurrogate = new AllowNonSerializableTypesSurrogate();  
    }  
}  
```  
  
 <span data-ttu-id="b94dc-135">Medidas adicionais precisam ser tomadas para conectar o substituto para uso durante a geração de metadados.</span><span class="sxs-lookup"><span data-stu-id="b94dc-135">Additional steps need to be taken to plug in the surrogate for use during metadata generation.</span></span> <span data-ttu-id="b94dc-136">Um mecanismo para fazer isso `IWsdlExportExtension` é fornecer um que é o que esta amostra demonstra.</span><span class="sxs-lookup"><span data-stu-id="b94dc-136">One mechanism to do this is to provide an `IWsdlExportExtension` which is what this sample demonstrates.</span></span> <span data-ttu-id="b94dc-137">Outra forma é `WsdlExporter` modificar o diretamente.</span><span class="sxs-lookup"><span data-stu-id="b94dc-137">Another way is to modify the `WsdlExporter` directly.</span></span>  
  
 <span data-ttu-id="b94dc-138">O `AllowNonSerializableTypesAttribute` atributo `IWsdlExportExtension` `IContractBehavior`implementa e .</span><span class="sxs-lookup"><span data-stu-id="b94dc-138">The `AllowNonSerializableTypesAttribute` attribute implements `IWsdlExportExtension` and `IContractBehavior`.</span></span> <span data-ttu-id="b94dc-139">A extensão pode `IContractBehavior` `IEndpointBehavior` ser um ou neste caso.</span><span class="sxs-lookup"><span data-stu-id="b94dc-139">The extension can be either an `IContractBehavior` or `IEndpointBehavior` in this case.</span></span> <span data-ttu-id="b94dc-140">Sua `IWsdlExportExtension.ExportContract` implementação do método permite `XsdDataContractExporter` que o substituto o adicione ao usado durante a geração de esquema para DataContract.</span><span class="sxs-lookup"><span data-stu-id="b94dc-140">Its `IWsdlExportExtension.ExportContract` method implementation enables the surrogate by adding it to the `XsdDataContractExporter` used during schema generation for DataContract.</span></span> <span data-ttu-id="b94dc-141">O seguinte trecho de código mostra como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="b94dc-141">The following code snippet shows how to do this.</span></span>  
  
```csharp
public void ExportContract(WsdlExporter exporter, WsdlContractConversionContext context)  
{  
    if (exporter == null)  
        throw new ArgumentNullException("exporter");  
  
    object dataContractExporter;  
    XsdDataContractExporter xsdDCExporter;  
    if (!exporter.State.TryGetValue(typeof(XsdDataContractExporter), out dataContractExporter))  
    {  
        xsdDCExporter = new XsdDataContractExporter(exporter.GeneratedXmlSchemas);  
        exporter.State.Add(typeof(XsdDataContractExporter), xsdDCExporter);  
    }  
    else  
    {  
        xsdDCExporter = (XsdDataContractExporter)dataContractExporter;  
    }  
    if (xsdDCExporter.Options == null)  
        xsdDCExporter.Options = new ExportOptions();  
  
    if (xsdDCExporter.Options.DataContractSurrogate == null)  
        xsdDCExporter.Options.DataContractSurrogate = new AllowNonSerializableTypesSurrogate();  
}  
```  
  
 <span data-ttu-id="b94dc-142">Quando você executa a amostra, o cliente liga para AddEmployee seguido de uma chamada getemployee para verificar se a primeira chamada foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="b94dc-142">When you run the sample, the client calls AddEmployee followed by a GetEmployee call to check if the first call was successful.</span></span> <span data-ttu-id="b94dc-143">O resultado da solicitação de operação GetEmployee é exibido na janela do console cliente.</span><span class="sxs-lookup"><span data-stu-id="b94dc-143">The result of the GetEmployee operation request is displayed in the client console window.</span></span> <span data-ttu-id="b94dc-144">A operação GetEmployee deve ter sucesso em encontrar o funcionário e imprimir "encontrado".</span><span class="sxs-lookup"><span data-stu-id="b94dc-144">The GetEmployee operation must succeed in finding the employee and print "found".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b94dc-145">Esta amostra mostra como conectar um substituto para serializar, desserializar e metadados.</span><span class="sxs-lookup"><span data-stu-id="b94dc-145">This sample shows how to plug in a surrogate for serialize, deserialize and metadata generation.</span></span> <span data-ttu-id="b94dc-146">Ele não mostra como conectar um substituto para geração de código a partir de metadados.</span><span class="sxs-lookup"><span data-stu-id="b94dc-146">It does not show how to plug in a surrogate for code generation from metadata.</span></span> <span data-ttu-id="b94dc-147">Para ver uma amostra de como um substituto pode ser usado para conectar à geração de código do cliente, consulte a amostra de publicação personalizada do [WSDL.](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)</span><span class="sxs-lookup"><span data-stu-id="b94dc-147">To see a sample of how a surrogate can be used to plug into client code generation, see the [Custom WSDL Publication](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md) sample.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b94dc-148">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="b94dc-148">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b94dc-149">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b94dc-149">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="b94dc-150">Para construir a edição C# da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b94dc-150">To build the C# edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="b94dc-151">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b94dc-151">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b94dc-152">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="b94dc-152">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b94dc-153">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="b94dc-153">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="b94dc-154">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="b94dc-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b94dc-155">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="b94dc-155">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DataContract`  
