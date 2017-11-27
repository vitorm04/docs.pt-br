---
title: Alternativa de DataContract
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0188f3c-00a9-4cf0-a887-a2284c8fb014
caps.latest.revision: "21"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 77eee3172b24bc0252ecb18d9ce6b283ba6e5c93
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="datacontract-surrogate"></a>Alternativa de DataContract
Este exemplo demonstra como processos como a serialização, desserialização, exportação de esquema e importação de esquema podem ser personalizados usando um contrato de dados alternativos classe. Este exemplo mostra como usar um substituto em um cenário de cliente e servidor onde os dados são serializados e transmitidos entre um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] cliente e serviço.  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
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
  
 O `AddEmployee` operação permite que os usuários adicionem dados sobre os novos funcionários e `GetEmployee` operação oferece suporte a pesquisa para funcionários com base no nome.  
  
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
  
 No `Employee` tipo, o `Person` (mostrado no código de exemplo a seguir) de classe não pode ser serializado pelo <xref:System.Runtime.Serialization.DataContractSerializer> porque ele não é uma classe de contrato de dados válido.  
  
```  
public class Person  
{  
    public string firstName;  
  
    public string lastName;  
  
    public int age;  
  
    public Person() { }  
}  
```  
  
 Você pode aplicar o `DataContract` de atributo para o `Person` classe, mas isso nem sempre é possível. Por exemplo, a `Person` classe pode ser definida em um assembly separado durante o qual você não tem controle.  
  
 Dada essa restrição, uma maneira para serializar o `Person` classe é para substituí-lo por outra classe que é marcado com `DataContractAttribute` e copie os dados necessários para a nova classe. O objetivo é fazer o `Person` classe aparecem como DataContract para o <xref:System.Runtime.Serialization.DataContractSerializer>. Observe que essa é uma maneira para serializar as classes de contrato de dados não.  
  
 O exemplo logicamente substitui o `Person` classe com uma classe diferente chamada `PersonSurrogated`.  
  
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
  
 O substituto de contrato de dados é usado para atingir essa substituição. Um substituto de contrato de dados é uma classe que implementa <xref:System.Runtime.Serialization.IDataContractSurrogate>. Neste exemplo, a `AllowNonSerializableTypesSurrogate` classe implementa essa interface.  
  
 Na implementação de interface, a primeira tarefa é estabelecer um mapeamento de tipo de `Person` para `PersonSurrogated`. Isso é usado tanto em tempo de serialização, bem como em tempo de exportação de esquema. Esse mapeamento é obtido com a implementação de <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> método.  
  
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
  
 O <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> método mapeia um `Person` de instância para um `PersonSurrogated` instância durante a serialização, conforme mostrado no código de exemplo a seguir.  
  
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
  
 O <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> método fornece o mapeamento inverso para desserialização, conforme mostrado no código de exemplo a seguir.  
  
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
  
 Para mapear o `PersonSurrogated` de contrato de dados para existente `Person` classe durante a importação de esquema, o exemplo implementa o <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> método, conforme mostrado no código de exemplo a seguir.  
  
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
  
 O seguinte código de exemplo conclui a implementação de <xref:System.Runtime.Serialization.IDataContractSurrogate> interface.  
  
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
  
 Neste exemplo, o substituto está habilitado no ServiceModel por um atributo chamado `AllowNonSerializableTypesAttribute`. Os desenvolvedores precisam aplicar esse atributo no seu contrato de serviço, conforme mostrado no `IPersonnelDataService` acima do contrato de serviço. Esse atributo implementa `IContractBehavior` e configura o substituto em operações em seu `ApplyClientBehavior` e `ApplyDispatchBehavior` métodos.  
  
 O atributo não é necessário nesse caso - ele é usado para fins de demonstração neste exemplo. Os usuários também podem habilitar um substituto adicionando manualmente semelhantes `IContractBehavior`, `IEndpointBehavior` ou `IOperationBehavior` usando código ou usando a configuração.  
  
 O `IContractBehavior` implementação procura por operações que usam DataContract, verificando se eles têm um `DataContractSerializerOperationBehavior` registrado. Se isso ocorrer, ele define o `DataContractSurrogate` propriedade esse comportamento. O código de exemplo a seguir mostra como fazer isso. Configuração do substituto nesse comportamento da operação habilitada para serialização e desserialização.  
  
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
  
 Etapas adicionais precisam ser tomadas para plug-in do substituto para uso durante a geração de metadados. Um mecanismo para fazer isso é fornecer um `IWsdlExportExtension` que é o que demonstra este exemplo. É outra maneira de modificar o `WsdlExporter` diretamente.  
  
 O `AllowNonSerializableTypesAttribute` atributo implementa `IWsdlExportExtension` e `IContractBehavior`. A extensão pode ser um `IContractBehavior` ou `IEndpointBehavior` nesse caso. Seu `IWsdlExportExtension.ExportContract` implementação do método permite que o substituto adicionando-o para o `XsdDataContractExporter` usado durante a geração de esquema para DataContract. O trecho de código a seguir mostra como fazer isso.  
  
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
  
 Quando você executar o exemplo, o cliente chama AddEmployee seguido por uma chamada de GetEmployee para verificar se a primeira chamada foi bem-sucedida. O resultado da solicitação de operação GetEmployee é exibido na janela do console do cliente. A operação de GetEmployee deve localizar o funcionário com êxito e imprimir "encontrado".  
  
> [!NOTE]
>  Este exemplo mostra como conectar um substituto de serialização, desserializar e geração de metadados. Ele não mostra como conectar um substituto para geração de código de metadados. Para ver um exemplo de como um substituto pode ser usado para conectar à geração de código de cliente, consulte o [publicação de WSDL personalizado](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md) exemplo.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar o c# edition da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DataContract`  
  
## <a name="see-also"></a>Consulte também
