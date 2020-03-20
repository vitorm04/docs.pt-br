---
title: Referências de objeto
ms.date: 03/30/2017
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
ms.openlocfilehash: 5eb842e1bff9ba60074379fde5ef3d0597f2184e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183454"
---
# <a name="object-references"></a>Referências de objeto
Esta amostra demonstra como passar objetos por referências entre servidor e cliente. A amostra usa *redes sociais*simuladas. Uma rede social consiste `Person` em uma classe que contém uma lista de `Person` amigos em que cada amigo é uma instância da classe, com sua própria lista de amigos. Isso cria um gráfico de objetos. O serviço expõe as operações nessas redes sociais.  
  
 Nesta amostra, o serviço é hospedado pelo Internet Information Services (IIS) e o cliente é um aplicativo de console (.exe).  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
## <a name="service"></a>Serviço  
 A `Person` classe <xref:System.Runtime.Serialization.DataContractAttribute> tem o atributo <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> aplicado, `true` com o campo definido para declará-lo como um tipo de referência. Todas as <xref:System.Runtime.Serialization.DataMemberAttribute> propriedades têm o atributo aplicado.  
  
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
  
 A `GetPeopleInNetwork` operação tem um `Person` parâmetro de tipo e devolve todas as pessoas da rede; ou seja, todas as `friends` pessoas da lista, os amigos do amigo, e assim por diante, sem duplicatas.  
  
```csharp
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 A `GetMutualFriends` operação tem um `Person` parâmetro de tipo e devolve todos os amigos `friends` da lista que também têm essa pessoa em sua lista.  
  
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
  
 A `GetCommonFriends` operação leva uma `Person`lista de tipos. Espera-se que a `Person` lista tenha dois objetos. A operação retorna `Person` uma lista de `friends` objetos `Person` que estão nas listas de ambos os objetos na lista de entradas.  
  
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
 O proxy do cliente é criado usando o recurso **Add Service Reference** do Visual Studio.  
  
 Uma rede social composta `Person` por cinco objetos é criada. O cliente liga para cada um dos três métodos do serviço.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a>Confira também

- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- [Referências de objeto de interoperabilidade](../../../../docs/framework/wcf/feature-details/interoperable-object-references.md)
