---
title: Referências de objeto
ms.date: 03/30/2017
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
ms.openlocfilehash: bc9c318fc0e05f384a00df7cd1436a138315d880
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714674"
---
# <a name="object-references"></a>Referências de objeto
Este exemplo demonstra como passar objetos por referências entre servidor e cliente. O exemplo usa *redes sociais*simuladas. Uma rede social consiste em uma classe `Person` que contém uma lista de amigos em que cada amigo é uma instância da classe `Person`, com sua própria lista de amigos. Isso cria um grafo de objetos. O serviço expõe operações nessas redes sociais.  
  
 Neste exemplo, o serviço é hospedado pelo Serviços de Informações da Internet (IIS) e o cliente é um aplicativo de console (. exe).  
  
> [!NOTE]
> O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.  
  
## <a name="service"></a>Service  
 A classe `Person` tem o atributo <xref:System.Runtime.Serialization.DataContractAttribute> aplicado, com o campo <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> definido como `true` para declará-lo como um tipo de referência. Todas as propriedades têm o atributo <xref:System.Runtime.Serialization.DataMemberAttribute> aplicado.  
  
```csharp
[DataContract(IsReference=true)]  
public class Person  
{  
    string name;  
    string location;  
    string gender;  
    int age;  
    List<Person> friends;  
    [DataMember()]  
    public string Name  
    {  
        get { return name; }  
        set { name = value; }  
    }  
    [DataMember()]  
    public string Location  
    {  
        get { return location; }  
        set { location = value; }  
    }  
    [DataMember()]  
    public string Gender  
    {  
        get { return gender; }  
        set { gender = value; }  
    }  
…  
}  
```  
  
 A operação `GetPeopleInNetwork` usa um parâmetro do tipo `Person` e retorna todas as pessoas na rede; ou seja, todas as pessoas na lista de `friends`, os amigos do amigo e assim por diante, sem duplicatas.  
  
```csharp
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 A operação `GetMutualFriends` usa um parâmetro do tipo `Person` e retorna todos os amigos na lista que também têm essa pessoa na lista de `friends`.  
  
```csharp
public List<Person> GetMutualFriends(Person p)  
{  
    List<Person> mutual = new List<Person>();  
    foreach (Person friend in p.Friends)  
    {  
        if (friend.Friends.Contains(p))  
            mutual.Add(friend);  
    }  
    return mutual;  
}  
```  
  
 A operação `GetCommonFriends` usa uma lista do tipo `Person`. Espera-se que a lista tenha dois objetos `Person`. A operação retorna uma lista de objetos de `Person` que estão no `friends` listas de `Person` objetos na lista de entrada.  
  
```csharp
public List<Person> GetCommonFriends(List<Person> people)  
{  
    List<Person> common = new List<Person>();  
    foreach (Person friend in people[0].Friends)  
        if (people[1].Friends.Contains(friend))  
            common.Add(friend);  
    return common;  
}  
```  
  
## <a name="client"></a>Cliente  
 O proxy do cliente é criado usando o recurso **Adicionar referência de serviço** do Visual Studio.  
  
 Uma rede social que consiste em cinco objetos `Person` é criada. O cliente chama cada um dos três métodos no serviço.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras. Este exemplo está localizado no seguinte diretório.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- [Referências de objeto interoperável](../../../../docs/framework/wcf/feature-details/interoperable-object-references.md)
