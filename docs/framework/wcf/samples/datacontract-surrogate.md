---
title: Alternativa de DataContract
ms.date: 03/30/2017
ms.assetid: b0188f3c-00a9-4cf0-a887-a2284c8fb014
ms.openlocfilehash: 10b0c2a3e82e39b03291f567ca360c51042b464e
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46003133"
---
# <a name="datacontract-surrogate"></a><span data-ttu-id="a0b4a-102">Alternativa de DataContract</span><span class="sxs-lookup"><span data-stu-id="a0b4a-102">DataContract Surrogate</span></span>
<span data-ttu-id="a0b4a-103">Este exemplo demonstra como processos como a serialização, desserialização, exportação de esquema e importação de esquema podem ser personalizados usando um contrato de dados alternativos classe.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-103">This sample demonstrates how processes like serialization, deserialization, schema export, and schema import can be customized using a data contract surrogate class.</span></span> <span data-ttu-id="a0b4a-104">Este exemplo mostra como usar um substituto em um cenário de cliente e servidor em que os dados são serializados e transmitidos entre um cliente do Windows Communication Foundation (WCF) e o serviço.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-104">This sample shows how to use a surrogate in a client and server scenario where data is serialized and transmitted between a Windows Communication Foundation (WCF) client and service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0b4a-105">As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a0b4a-106">O exemplo usa o contrato de serviço a seguir:</span><span class="sxs-lookup"><span data-stu-id="a0b4a-106">The sample uses the following service contract:</span></span>  
  
```  
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
  
 <span data-ttu-id="a0b4a-107">O `AddEmployee` operação permite que os usuários adicionem dados sobre os novos funcionários e o `GetEmployee` operação dá suporte à pesquisa de funcionários com base no nome.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-107">The `AddEmployee` operation allows users to add data about new employees and the `GetEmployee` operation supports search for employees based on name.</span></span>  
  
 <span data-ttu-id="a0b4a-108">Essas operações usam o tipo de dados a seguir:</span><span class="sxs-lookup"><span data-stu-id="a0b4a-108">These operations use the following data type:</span></span>  
  
```  
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
  
 <span data-ttu-id="a0b4a-109">No `Employee` tipo, o `Person` classe (mostrado no código de exemplo a seguir) não pode ser serializado pelo <xref:System.Runtime.Serialization.DataContractSerializer> porque ele não é uma classe de contrato de dados válido.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-109">In the `Employee` type, the `Person` class (shown in the following sample code) cannot be serialized by the <xref:System.Runtime.Serialization.DataContractSerializer> because it is not a valid data contract class.</span></span>  
  
```  
public class Person  
{  
    public string firstName;  
  
    public string lastName;  
  
    public int age;  
  
    public Person() { }  
}  
```  
  
 <span data-ttu-id="a0b4a-110">Você pode aplicar a `DataContract` de atributo para o `Person` classe, mas isso nem sempre é possível.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-110">You can apply the `DataContract` attribute to the `Person` class, but this is not always possible.</span></span> <span data-ttu-id="a0b4a-111">Por exemplo, o `Person` classe pode ser definida em um assembly separado sobre o qual você não tem controle.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-111">For example, the `Person` class can be defined in a separate assembly over which you have no control.</span></span>  
  
 <span data-ttu-id="a0b4a-112">Dada essa restrição é uma maneira de serializar o `Person` classe é substituí-lo com outra classe que é marcado com `DataContractAttribute` e copie os dados necessários para a nova classe.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-112">Given this restriction, one way to serialize the `Person` class is to substitute it with another class that is marked with `DataContractAttribute` and copy over necessary data to the new class.</span></span> <span data-ttu-id="a0b4a-113">O objetivo é tornar o `Person` classe aparecem como DataContract para o <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-113">The objective is to make the `Person` class appear as a DataContract to the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="a0b4a-114">Observe que essa é uma maneira para serializar classes de contrato de dados não.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-114">Note that this is one way to serialize non-data contract classes.</span></span>  
  
 <span data-ttu-id="a0b4a-115">O exemplo logicamente substitui o `Person` classe com uma classe diferente denominada `PersonSurrogated`.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-115">The sample logically replaces the `Person` class with a different class named `PersonSurrogated`.</span></span>  
  
```  
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
  
 <span data-ttu-id="a0b4a-116">O substituto de contrato de dados é usado para atingir essa substituição.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-116">The data contract surrogate is used to achieve this replacement.</span></span> <span data-ttu-id="a0b4a-117">Um substituto de contrato de dados é uma classe que implementa <xref:System.Runtime.Serialization.IDataContractSurrogate>.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-117">A data contract surrogate is a class that implements <xref:System.Runtime.Serialization.IDataContractSurrogate>.</span></span> <span data-ttu-id="a0b4a-118">Neste exemplo, o `AllowNonSerializableTypesSurrogate` classe implementa essa interface.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-118">In this sample, the `AllowNonSerializableTypesSurrogate` class implements this interface.</span></span>  
  
 <span data-ttu-id="a0b4a-119">Na implementação da interface, a primeira tarefa é estabelecer um mapeamento de tipo de `Person` para `PersonSurrogated`.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-119">In the interface implementation, the first task is to establish a type mapping from `Person` to `PersonSurrogated`.</span></span> <span data-ttu-id="a0b4a-120">Isso é usado tanto no tempo de serialização, bem como em tempo de exportação de esquema.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-120">This is used both at serialization time as well as at schema export time.</span></span> <span data-ttu-id="a0b4a-121">Esse mapeamento é obtido Implementando o <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> método.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-121">This mapping is achieved by implementing the <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> method.</span></span>  
  
```  
public Type GetDataContractType(Type type)  
{  
    if (typeof(Person).IsAssignableFrom(type))  
    {  
        return typeof(PersonSurrogated);  
    }  
    return type;  
}  
```  
  
 <span data-ttu-id="a0b4a-122">O <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> mapas de método uma `Person` da instância para um `PersonSurrogated` da instância durante a serialização, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-122">The <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> method maps a `Person` instance to a `PersonSurrogated` instance during serialization, as shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="a0b4a-123">O <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> método fornece o mapeamento inverso para a desserialização, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-123">The <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> method provides the reverse mapping for deserialization, as shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="a0b4a-124">Para mapear o `PersonSurrogated` contrato de dados para existente `Person` classe durante a importação de esquema, o exemplo implementa o <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> método, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-124">To map the `PersonSurrogated` data contract to the existing `Person` class during schema import, the sample implements the <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> method, as shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="a0b4a-125">O seguinte código de exemplo completa a implementação do <xref:System.Runtime.Serialization.IDataContractSurrogate> interface.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-125">The following sample code completes the implementation of the <xref:System.Runtime.Serialization.IDataContractSurrogate> interface.</span></span>  
  
```  
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
  
 <span data-ttu-id="a0b4a-126">Neste exemplo, o substituto é habilitado em ServiceModel por um atributo chamado `AllowNonSerializableTypesAttribute`.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-126">In this sample, the surrogate is enabled in ServiceModel by an attribute called `AllowNonSerializableTypesAttribute`.</span></span> <span data-ttu-id="a0b4a-127">Os desenvolvedores precisam aplicar esse atributo no seu contrato de serviço, conforme mostrado no `IPersonnelDataService` acima do contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-127">Developers would need to apply this attribute on their service contract as shown on the `IPersonnelDataService` service contract above.</span></span> <span data-ttu-id="a0b4a-128">Esse atributo implementa `IContractBehavior` e configura o substituto em operações no seu `ApplyClientBehavior` e `ApplyDispatchBehavior` métodos.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-128">This attribute implements `IContractBehavior` and sets up the surrogate on operations in its `ApplyClientBehavior` and `ApplyDispatchBehavior` methods.</span></span>  
  
 <span data-ttu-id="a0b4a-129">O atributo não é necessário neste caso – ele é usado para fins de demonstração neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-129">The attribute is not necessary in this case - it is used for demonstration purposes in this sample.</span></span> <span data-ttu-id="a0b4a-130">Os usuários podem habilitar como alternativa, um substituto adicionando manualmente um semelhante `IContractBehavior`, `IEndpointBehavior` ou `IOperationBehavior` usando código ou configuração.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-130">Users can alternatively enable a surrogate by manually adding a similar `IContractBehavior`, `IEndpointBehavior` or `IOperationBehavior` using code or using configuration.</span></span>  
  
 <span data-ttu-id="a0b4a-131">O `IContractBehavior` implementação procura por operações que usam DataContract, verificando se eles tiverem um `DataContractSerializerOperationBehavior` registrado.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-131">The `IContractBehavior` implementation looks for operations that use DataContract by checking if they have a `DataContractSerializerOperationBehavior` registered.</span></span> <span data-ttu-id="a0b4a-132">Se Sim, ele define o `DataContractSurrogate` propriedade em que o comportamento.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-132">If they do, it sets the `DataContractSurrogate` property on that behavior.</span></span> <span data-ttu-id="a0b4a-133">O código de exemplo a seguir mostra como isso é feito.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-133">The following sample code shows how this is done.</span></span> <span data-ttu-id="a0b4a-134">Definir o substituto sobre esse comportamento de operação habilitará para serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-134">Setting the surrogate on this operation behavior enables it for serialization and deserialization.</span></span>  
  
```  
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
  
 <span data-ttu-id="a0b4a-135">Etapas adicionais precisam ser seguidas para plug-in do substituto para uso durante a geração de metadados.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-135">Additional steps need to be taken to plug in the surrogate for use during metadata generation.</span></span> <span data-ttu-id="a0b4a-136">Um mecanismo para fazer isso é fornecer um `IWsdlExportExtension` que é o que este exemplo demonstra.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-136">One mechanism to do this is to provide an `IWsdlExportExtension` which is what this sample demonstrates.</span></span> <span data-ttu-id="a0b4a-137">Outra maneira é modificar o `WsdlExporter` diretamente.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-137">Another way is to modify the `WsdlExporter` directly.</span></span>  
  
 <span data-ttu-id="a0b4a-138">O `AllowNonSerializableTypesAttribute` atributo implements `IWsdlExportExtension` e `IContractBehavior`.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-138">The `AllowNonSerializableTypesAttribute` attribute implements `IWsdlExportExtension` and `IContractBehavior`.</span></span> <span data-ttu-id="a0b4a-139">A extensão pode ser um `IContractBehavior` ou `IEndpointBehavior` nesse caso.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-139">The extension can be either an `IContractBehavior` or `IEndpointBehavior` in this case.</span></span> <span data-ttu-id="a0b4a-140">Sua `IWsdlExportExtension.ExportContract` implementação de método permite que o substituto adicionando-à `XsdDataContractExporter` usado durante a geração de esquema para DataContract.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-140">Its `IWsdlExportExtension.ExportContract` method implementation enables the surrogate by adding it to the `XsdDataContractExporter` used during schema generation for DataContract.</span></span> <span data-ttu-id="a0b4a-141">O trecho de código a seguir mostra como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-141">The following code snippet shows how to do this.</span></span>  
  
```  
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
  
 <span data-ttu-id="a0b4a-142">Quando você executar o exemplo, o cliente chama AddEmployee seguido por uma chamada de GetEmployee para verificar se a primeira chamada foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-142">When you run the sample, the client calls AddEmployee followed by a GetEmployee call to check if the first call was successful.</span></span> <span data-ttu-id="a0b4a-143">O resultado da solicitação de operação GetEmployee é exibido na janela do console de cliente.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-143">The result of the GetEmployee operation request is displayed in the client console window.</span></span> <span data-ttu-id="a0b4a-144">A operação GetEmployee deve ter êxito em localizar o funcionário e imprimir "encontrado".</span><span class="sxs-lookup"><span data-stu-id="a0b4a-144">The GetEmployee operation must succeed in finding the employee and print "found".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0b4a-145">Este exemplo mostra como conectar um substituto para serialização, desserializar e geração de metadados.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-145">This sample shows how to plug in a surrogate for serialize, deserialize and metadata generation.</span></span> <span data-ttu-id="a0b4a-146">Ele não mostra como conectar um substituto para a geração de código dos metadados.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-146">It does not show how to plug in a surrogate for code generation from metadata.</span></span> <span data-ttu-id="a0b4a-147">Para ver um exemplo de como um substituto pode ser usado para conectar à geração de código do cliente, consulte a [publicação de WSDL personalizado](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-147">To see a sample of how a surrogate can be used to plug into client code generation, see the [Custom WSDL Publication](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md) sample.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a0b4a-148">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="a0b4a-148">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="a0b4a-149">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a0b4a-149">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="a0b4a-150">Para compilar a edição do c# da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a0b4a-150">To build the C# edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="a0b4a-151">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a0b4a-151">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a0b4a-152">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-152">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a0b4a-153">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-153">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a0b4a-154">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a0b4a-155">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="a0b4a-155">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DataContract`  
  
## <a name="see-also"></a><span data-ttu-id="a0b4a-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a0b4a-156">See Also</span></span>
