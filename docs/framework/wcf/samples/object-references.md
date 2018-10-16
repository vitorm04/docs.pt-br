---
title: Referências de objeto
ms.date: 03/30/2017
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
ms.openlocfilehash: 00caccaeed8cebeec2e053d418ae6a5bf9a12138
ms.sourcegitcommit: fd8d4587cc26e53f0e27e230d6e27d828ef4306b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2018
ms.locfileid: "49347738"
---
# <a name="object-references"></a>Referências de objeto
Este exemplo demonstra como passar objetos por referências entre servidor e cliente. O exemplo usa simulado *redes sociais*. Uma rede social consiste em um `Person` que contém uma lista de amigos no qual cada friend é uma instância da classe a `Person` classe, com sua própria lista de amigos. Isso cria um grafo de objetos. O serviço expõe operações nessas redes sociais.  
  
 Neste exemplo, o serviço é hospedado pelo Internet Information Services (IIS) e o cliente é um aplicativo de console (.exe).  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
## <a name="service"></a>Serviço  
 O `Person` classe tem o <xref:System.Runtime.Serialization.DataContractAttribute> atributo aplicado, com o <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> campo definido como `true` declará-lo como um tipo de referência. Todas as propriedades têm o <xref:System.Runtime.Serialization.DataMemberAttribute> atributo aplicado.  
  
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
  
 O `GetPeopleInNetwork` operação leva um parâmetro do tipo `Person` e retorna todas as pessoas na rede; ou seja, todas as pessoas no `friends` lista, o amigo amigos e assim por diante, sem duplicatas.  
  
```csharp
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 O `GetMutualFriends` operação leva um parâmetro do tipo `Person` e retorna todos os amigos da lista que também têm essa pessoa em sua `friends` lista.  
  
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
  
 O `GetCommonFriends` operação aceita uma lista do tipo `Person`. A lista deve ter dois `Person` objetos nele. A operação retorna uma lista dos `Person` objetos que estão na `friends` listas de ambos `Person` objetos na lista de entrada.  
  
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
 O proxy de cliente é criado usando o **adicionar referência de serviço** recurso do Visual Studio.  
  
 Uma rede social que consiste em cinco `Person` objetos é criado. O cliente chama cada um dos três métodos no serviço.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>  
 [Referências de objeto interoperável](../../../../docs/framework/wcf/feature-details/interoperable-object-references.md)
