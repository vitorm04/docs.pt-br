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
# <a name="datacontract-surrogate"></a>Alternativa de DataContract
Esta amostra demonstra como processos como serialização, desserialização, exportação de esquemas e importação de esquemas podem ser personalizados usando uma classe de substituto de contrato de dados. Esta amostra mostra como usar um substituto em um cenário de cliente e servidor onde os dados são serializados e transmitidos entre um cliente e serviço da Windows Communication Foundation (WCF).  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
 A amostra utiliza o seguinte contrato de serviço:  
  
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
  
 A `AddEmployee` operação permite que os usuários adicionem dados sobre novos funcionários e a `GetEmployee` operação suporta a busca por funcionários com base no nome.  
  
 Essas operações utilizam o seguinte tipo de dados:  
  
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
  
 No `Employee` tipo, `Person` a classe (mostrada no código de amostra <xref:System.Runtime.Serialization.DataContractSerializer> a seguir) não pode ser serializada pelo porque não é uma classe de contrato de dados válida.  
  
```csharp
public class Person  
{  
    public string firstName;  
  
    public string lastName;  
  
    public int age;  
  
    public Person() { }  
}  
```  
  
 Você pode <xref:System.Runtime.Serialization.DataContractAttribute> aplicar o `Person` atributo à classe, mas isso nem sempre é possível. Por exemplo, `Person` a classe pode ser definida em um conjunto separado sobre o qual você não tem controle.  
  
 Dada essa restrição, uma `Person` maneira de serializar a classe é <xref:System.Runtime.Serialization.DataContractAttribute> substituí-la por outra classe que é marcada e copiar sobre os dados necessários para a nova classe. O objetivo é `Person` fazer com que a <xref:System.Runtime.Serialization.DataContractSerializer>classe apareça como um Contrato de Dados para o . Observe que esta é uma maneira de serializar classes de contratos não-dados.  
  
 A amostra logicamente `Person` substitui a classe `PersonSurrogated`por uma classe diferente chamada .  
  
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
  
 O substituto do contrato de dados é usado para conseguir essa substituição. Um substituto de contrato de <xref:System.Runtime.Serialization.IDataContractSurrogate>dados é uma classe que implementa . Nesta amostra, `AllowNonSerializableTypesSurrogate` a classe implementa essa interface.  
  
 Na implementação da interface, a primeira tarefa `Person` `PersonSurrogated`é estabelecer um mapeamento de tipo a partir de . Isso é usado tanto no tempo de serialização quanto no tempo de exportação do esquema. Esse mapeamento é conseguido <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> com a implementação do método.  
  
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
  
 O <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> método `Person` mapeia uma instância para uma `PersonSurrogated` instância durante a serialização, conforme mostrado no código de amostra a seguir.  
  
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
  
 O <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> método fornece o mapeamento reverso para desserialização, como mostrado no código de amostra a seguir.  
  
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
  
 Para mapear `PersonSurrogated` o contrato de `Person` dados para a classe existente durante <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> a importação do esquema, a amostra implementa o método, conforme mostrado no código amostral a seguir.  
  
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
  
 O código de amostra a <xref:System.Runtime.Serialization.IDataContractSurrogate> seguir completa a implementação da interface.  
  
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
  
 Nesta amostra, o substituto é habilitado no `AllowNonSerializableTypesAttribute`ServiceModel por um atributo chamado . Os desenvolvedores precisariam aplicar esse atributo em `IPersonnelDataService` seu contrato de serviço, conforme mostrado no contrato de serviço acima. Esse atributo `IContractBehavior` implementa e configura o `ApplyClientBehavior` `ApplyDispatchBehavior` substituto em operações em seus métodos e métodos.  
  
 O atributo não é necessário neste caso - é usado para fins de demonstração nesta amostra. Os usuários podem, alternativamente, habilitar `IContractBehavior` `IEndpointBehavior` um `IOperationBehavior` substituto adicionando manualmente um semelhante, ou usando código ou usando configuração.  
  
 A `IContractBehavior` implementação procura operações que utilizem DataContract verificando se possuem um `DataContractSerializerOperationBehavior` registro. Se o fizerem, `DataContractSurrogate` isso define a propriedade sobre esse comportamento. O seguinte código de amostra mostra como isso é feito. A definição do substituto sobre este comportamento de operação permite que ele seja serializador e desserializador.  
  
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
  
 Medidas adicionais precisam ser tomadas para conectar o substituto para uso durante a geração de metadados. Um mecanismo para fazer isso `IWsdlExportExtension` é fornecer um que é o que esta amostra demonstra. Outra forma é `WsdlExporter` modificar o diretamente.  
  
 O `AllowNonSerializableTypesAttribute` atributo `IWsdlExportExtension` `IContractBehavior`implementa e . A extensão pode `IContractBehavior` `IEndpointBehavior` ser um ou neste caso. Sua `IWsdlExportExtension.ExportContract` implementação do método permite `XsdDataContractExporter` que o substituto o adicione ao usado durante a geração de esquema para DataContract. O seguinte trecho de código mostra como fazer isso.  
  
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
  
 Quando você executa a amostra, o cliente liga para AddEmployee seguido de uma chamada getemployee para verificar se a primeira chamada foi bem sucedida. O resultado da solicitação de operação GetEmployee é exibido na janela do console cliente. A operação GetEmployee deve ter sucesso em encontrar o funcionário e imprimir "encontrado".  
  
> [!NOTE]
> Esta amostra mostra como conectar um substituto para serializar, desserializar e metadados. Ele não mostra como conectar um substituto para geração de código a partir de metadados. Para ver uma amostra de como um substituto pode ser usado para conectar à geração de código do cliente, consulte a amostra de publicação personalizada do [WSDL.](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C# da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DataContract`  
