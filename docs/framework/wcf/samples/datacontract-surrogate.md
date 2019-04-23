---
title: Alternativa de DataContract
ms.date: 03/30/2017
ms.assetid: b0188f3c-00a9-4cf0-a887-a2284c8fb014
ms.openlocfilehash: a56fbcabfacf146142f7b0c0623325cc8e69c29a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59769093"
---
# <a name="datacontract-surrogate"></a>Alternativa de DataContract
Este exemplo demonstra como processos como a serialização, desserialização, exportação de esquema e importação de esquema podem ser personalizados usando um contrato de dados alternativos classe. Este exemplo mostra como usar um substituto em um cenário de cliente e servidor em que os dados são serializados e transmitidos entre um cliente do Windows Communication Foundation (WCF) e o serviço.  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 O exemplo usa o contrato de serviço a seguir:  
  
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
  
 O `AddEmployee` operação permite que os usuários adicionem dados sobre os novos funcionários e o `GetEmployee` operação dá suporte à pesquisa de funcionários com base no nome.  
  
 Essas operações usam o tipo de dados a seguir:  
  
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
  
 No `Employee` tipo, o `Person` classe (mostrado no código de exemplo a seguir) não pode ser serializado pelo <xref:System.Runtime.Serialization.DataContractSerializer> porque ele não é uma classe de contrato de dados válido.  
  
```  
public class Person  
{  
    public string firstName;  
  
    public string lastName;  
  
    public int age;  
  
    public Person() { }  
}  
```  
  
 Você pode aplicar a <xref:System.Runtime.Serialization.DataContractAttribute> de atributo para o `Person` classe, mas isso nem sempre é possível. Por exemplo, o `Person` classe pode ser definida em um assembly separado sobre o qual você não tem controle.  
  
 Dada essa restrição é uma maneira de serializar o `Person` classe é substituí-lo com outra classe que é marcado com <xref:System.Runtime.Serialization.DataContractAttribute> e copie os dados necessários para a nova classe. O objetivo é tornar o `Person` classe aparecem como DataContract para o <xref:System.Runtime.Serialization.DataContractSerializer>. Observe que essa é uma maneira para serializar classes de contrato de dados não.  
  
 O exemplo logicamente substitui o `Person` classe com uma classe diferente denominada `PersonSurrogated`.  
  
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
  
 O substituto de contrato de dados é usado para atingir essa substituição. Um substituto de contrato de dados é uma classe que implementa <xref:System.Runtime.Serialization.IDataContractSurrogate>. Neste exemplo, o `AllowNonSerializableTypesSurrogate` classe implementa essa interface.  
  
 Na implementação da interface, a primeira tarefa é estabelecer um mapeamento de tipo de `Person` para `PersonSurrogated`. Isso é usado tanto no tempo de serialização, bem como em tempo de exportação de esquema. Esse mapeamento é obtido Implementando o <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> método.  
  
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
  
 O <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> mapas de método uma `Person` da instância para um `PersonSurrogated` da instância durante a serialização, conforme mostrado no código de exemplo a seguir.  
  
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
  
 O <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> método fornece o mapeamento inverso para a desserialização, conforme mostrado no código de exemplo a seguir.  
  
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
  
 Para mapear o `PersonSurrogated` contrato de dados para existente `Person` classe durante a importação de esquema, o exemplo implementa o <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> método, conforme mostrado no código de exemplo a seguir.  
  
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
  
 O seguinte código de exemplo completa a implementação do <xref:System.Runtime.Serialization.IDataContractSurrogate> interface.  
  
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
  
 Neste exemplo, o substituto é habilitado em ServiceModel por um atributo chamado `AllowNonSerializableTypesAttribute`. Os desenvolvedores precisam aplicar esse atributo no seu contrato de serviço, conforme mostrado no `IPersonnelDataService` acima do contrato de serviço. Esse atributo implementa `IContractBehavior` e configura o substituto em operações no seu `ApplyClientBehavior` e `ApplyDispatchBehavior` métodos.  
  
 O atributo não é necessário neste caso – ele é usado para fins de demonstração neste exemplo. Os usuários podem habilitar como alternativa, um substituto adicionando manualmente um semelhante `IContractBehavior`, `IEndpointBehavior` ou `IOperationBehavior` usando código ou configuração.  
  
 O `IContractBehavior` implementação procura por operações que usam DataContract, verificando se eles tiverem um `DataContractSerializerOperationBehavior` registrado. Se Sim, ele define o `DataContractSurrogate` propriedade em que o comportamento. O código de exemplo a seguir mostra como isso é feito. Definir o substituto sobre esse comportamento de operação habilitará para serialização e desserialização.  
  
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
  
 Etapas adicionais precisam ser seguidas para plug-in do substituto para uso durante a geração de metadados. Um mecanismo para fazer isso é fornecer um `IWsdlExportExtension` que é o que este exemplo demonstra. Outra maneira é modificar o `WsdlExporter` diretamente.  
  
 O `AllowNonSerializableTypesAttribute` atributo implements `IWsdlExportExtension` e `IContractBehavior`. A extensão pode ser um `IContractBehavior` ou `IEndpointBehavior` nesse caso. Sua `IWsdlExportExtension.ExportContract` implementação de método permite que o substituto adicionando-à `XsdDataContractExporter` usado durante a geração de esquema para DataContract. O trecho de código a seguir mostra como fazer isso.  
  
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
  
 Quando você executar o exemplo, o cliente chama AddEmployee seguido por uma chamada de GetEmployee para verificar se a primeira chamada foi bem-sucedida. O resultado da solicitação de operação GetEmployee é exibido na janela do console de cliente. A operação GetEmployee deve ter êxito em localizar o funcionário e imprimir "encontrado".  
  
> [!NOTE]
>  Este exemplo mostra como conectar um substituto para serialização, desserializar e geração de metadados. Ele não mostra como conectar um substituto para a geração de código dos metadados. Para ver um exemplo de como um substituto pode ser usado para conectar à geração de código do cliente, consulte a [publicação de WSDL personalizado](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md) exemplo.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para compilar a edição do c# da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DataContract`  
