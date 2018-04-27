---
title: Referências de objeto
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fcb34efeb7eed28f85774dc5489b3e56aeac4e6c
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="object-references"></a>Referências de objeto
Este exemplo demonstra como passar objetos por referências entre servidor e cliente. Exemplos de uso simulados *redes sociais*. Consiste em uma rede social um `Person` que contém uma lista de amigos no qual cada friend é uma instância da classe de `Person` classe, com sua própria lista de amigos. Isso cria um gráfico de objetos. O serviço expõe operações nessas redes sociais.  
  
 Neste exemplo, o serviço é hospedado por serviços de informações da Internet (IIS) e o cliente é um aplicativo de console (.exe).  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
## <a name="service"></a>Serviço  
 O `Person` classe tem o <xref:System.Runtime.Serialization.DataContractAttribute> atributo aplicado, com o <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> campo definido como `true` para declará-la como um tipo de referência. Todas as propriedades têm o <xref:System.Runtime.Serialization.DataMemberAttribute> atributo aplicado.  
  
```  
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
  
 O `GetPeopleInNetwork` operação aceita um parâmetro de tipo `Person` e retorna todas as pessoas na rede; ou seja, todas as pessoas a `friends` lista o amigo amigos e assim por diante, sem duplicatas.  
  
```  
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 O `GetMutualFriends` operação aceita um parâmetro de tipo `Person` e retorna todos os amigos na lista que também têm essa pessoa em seus `friends` lista.  
  
```  
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
  
 O `GetCommonFriends` operação usa uma lista do tipo `Person`. A lista deve ter dois `Person` objetos contidos nele. A operação retorna uma lista de `Person` objetos que estão na `friends` listas de ambos `Person` objetos na lista de entrada.  
  
```  
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
 O proxy do cliente é criado usando o **adicionar referência de serviço** recurso do Visual Studio.  
  
 Uma rede social que consiste em cinco `Person` objetos é criado. O cliente chama cada um dos três métodos no serviço.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>  
 [Referências de objeto interoperável](../../../../docs/framework/wcf/feature-details/interoperable-object-references.md)
